# Using git

This section documents some best practice when using the
[git](https://git-scm.com/) source code management tool.

Good sources of documentation for git include:

* The [git documentation site](https://git-scm.com/doc) which links to free
    ebooks and videos about git.
* Members of UIS have access to LinkedIn Learning which has [many
    videos](https://www.linkedin.com/learning/me?u=2963594) on git.
* GitHub maintain [extensive documentation](https://help.github.com/) on their
    platform and git in general.

## Concepts

This section *very briefly* lists the main concepts in git. There are [gory
details](https://git-scm.com/book/en/v2/Git-Internals-Plumbing-and-Porcelain) in
the git book. There is also a [terminology section](#terminology) at the end of
this document if any of the terms used herein are unknown.

### Pushing and pulling

**Pushing** a branch to a remote consists of two stages:

1. The remote is sent the branch HEAD commit and any parent commits it doesn't
   already have.
2. The remote updates the remote branch to point to the new HEAD.

This only happens if the remote branch's original HEAD is a descendent of the
local branch's HEAD. Otherwise the push fails.

**Pulling** a branch is the opposite of a push. The steps are identical by the
roles of the remote and local repository are reversed.

### GitHub != git

It is tempting to identify GitHub and git. GitHub is a service provider which
offers git hosting and a set of related "software forge" functionality such as
issue tracking, project management, code review, etc. GitHub may be the 800lb
gorilla of the git world but there are many other large apes out there.

Git was originally designed to be decentralised. It is quite possible to use git
without GitHub and even without a working Internet connection.

## Feature branches

Feature branches are branches being used to develop an individual story. If you
are stuck for a name, "issue-{number}-{summary}" is a good choice where
"{number}" is the issue number of the story you are implementing and "{summary}"
is a brief summary of the story formatted-like-this.

### Structuring the branch

Tell a story with your branch: each commit should implement one step towards
implementing the story. It is kind to a reviewer to allow your pull requests to
be reviewed commit-wise so try to keep commits small, on topic and
self-contained.

### Commits

Each commit message should start with a single line summarising the change. If
the repository has logical "sections", start your commit message with the
section and a colon. For example, a Django webapp is usually composed of several
applications. Using the application name as a section is a good idea. The
single-line summary of a commit is, by convention, rather short. Keeping it
around 50 characters is a good rule of thumb given in the [git
documentation](https://git-scm.com/docs/git-commit#_discussion).

The commit message proper should explain how the commit implements what it
implements. It may also explain how the commit fits into the overall progression
of the story.

If the commit closes an issue, use a [GitHub
keyword](https://help.github.com/articles/closing-issues-using-keywords/) in the
commit. If only the pull request as a whole closes the issue, use the keyword in
the pull-request message.

An example message:

```
mediaplatform: MediaItem: make channel field non-NULL

Make the "channel" field of mediaplatform.models.MediaItem non-NULL. This
enforces that all media items will have an associated channel in future which is
required by #1234.

Add a pre-migration hook which assigns all media items which currently have a
"NULL" channel to an "orphan" channel. If there are no items with a NULL channel
the orphan channel is not created.

The orphan channel has blank edit and view permissions and as such will only be
available to admins.

Closes #1234
```

### Rebasing

Git [rebasing](https://git-scm.com/book/en/v2/Git-Branching-Rebasing) is an
invaluable tool to help you structure your branch to be easy to review. When
developing, the rule is "commit early, commit often". After you have finished
implementing the feature, you may re-order, combine and re-word commits using
the ``git rebase`` tool.

!> Once you have shared your branch with others via a pull request, do not
rebase as it makes pulling your changes harder.

## Terminology

This section briefly describes some of the terminology around git. It's not
intended to be exhaustive.

A **blob** is a set of bytes. It has a name which is the SHA1 hash of its
contents.

A **tree** is a set of blobs in a directory/filename hierarchy. It has a name
which is the SHA1 hash of its contents.

A **commit** is a message describing a tree, the name of a tree and a list of
names of "parent" commits. Its has a name which is the SHA1 hash of its
contents. Recursively following parent links from a commit yields the set of
"descendent" commits.

A **branch** is an alias for a commit. Its content is the name of the commit it
references. Its name is human-readable. Unlike commits, blobs or trees a
branch's name can stay the same even if its content changes. The commit pointed
to by a branch is called the **HEAD** of the branch.

The **master branch** is the branch which we agree as a team reflects the
current state of the product. Beyond this convention and the fact that it is the
default checked out branch when a repository is cloned *there is nothing
special about the master branch**.

A **remote** is an alias for a remote git repository. It maps a human readable
name to a location. For example,
"origin"→"git@github.com:uisautomation/guidebook".
