# Lifecycle of a story

This section documents the typical lifecycle of a story from inception to
merging.

!> We currently have both a physical board using sticky notes and a digital
board on GitHub. When we say "move the story from X to Y on the project board",
make sure to update the story in both places.

## Github issue

A story usually starts as a GitHub issue on a repository. Anyone (including
users) can open GitHub issues and not all issues will become stories. The
[Delivery Manager](roles.md#product-manager) selects which issues are
"story-ready" and adds them to a sprint. A story-ready issue:

* has a work estimate in days;
* specifies the work to be done in a clear manner in the issue
    description or in a subsequent comment;
* specifies the criteria for judging if the story is "done".

## Assignment

When someone starts tackling the story, they move it from the **backlog** to
**doing** on the project board.

If you are doing the story, assign yourself to the issue on GitHub.

## Implementation

The story is now being implemented.

If you are doing the story, create a new branch to do your work on. This should,
usually, be a branch from ``master``. Name your branch with the Github issue
number and a summary of the story.

```bash
$ git checkout -b issue-xxx-fix-foobar master
```

If you are implementing a story which for some reason lacks an issue number, or
has an issue in a different repository, omit the ``issue-xxx-`` prefix.

?> Make sure to follow [best practice](bestpractice/git.md#feature-branches)
when creating commits and feature branches.

## Pull request

When the story is ready for review, a pull request is opened and the other
developers on the team are notified. The story moves from **doing** to the
**review queue** on the project board.

If you are doing the story, when the story is ready for review, open a pull
request. Push your work to a branch in your local fork:

```bash
$ git push -u spqr1 issue-xxx-fix-foobar
```

(This assumes you forked your repository with ``hub fork`` and that your GitHub
username is ``spqr1``.)

The ``hub`` tool can then create the pull-request for you automatically and open
your editor pre-loaded with all the commit messages to make writing your pull
request summary easier.

```bash
$ hub pull-request
```

After the pull request is created, its URL is printed. Visit that URL in a
browser and ensure that the PR

* is added to the corresponding project for the sprint;
* has a review requested.

Usually, review requests are sent to "uisautomation/developers".

## Review

A story in the review queue may be picked up by a Developer to review. When they
do so they move the story from the **review queue** to **reviewing** on the
project board. After the review, the story will move to the **test queue** or
will move to **rework** where the original implementer can pick it up. In that
case, the story moves back to the "Implementation" stage above.

If you are doing the review, look at the pull request summary. It should explain
how the commits in the pull request implement the story and whether there are
any particular special steps required to test/deploy the pull request.

Use the GitHub interface to review the code.

?> See the [GitHub documentation for reviewing pull
requests](https://help.github.com/articles/reviewing-proposed-changes-in-a-pull-request/).

If satisfied, move the story from **reviewing** to the **test queue**.

If unsatisfied, move the story from **reviewing** to **rework**.

## Testing

A story in the test queue may be picked up by a Developer to test. When they do
so they move the story from the **test queue** to **testing** on the project
board. After testing, the story will move to **done** or will move to **rework**
where the original implementer can pick it up. In that case, the story moves
back to the "Implementation" stage above.

If you are testing the story, what you need will probably depend on the product
in question. For a web application, for example, you may test the functionality
locally in your development environment and deploy it to a development instance
in the Cloud.

If satisfied, move the story from **testing** to **done** and merge the pull
request.

If unsatisfied, move the story from **testing** to **rework**.
