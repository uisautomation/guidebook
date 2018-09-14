# Lifecycle of a story

This section documents the typical lifecycle of a story from inception to
merging.

!> We currently have both a physical board using sticky notes and a digital
board on GitHub. When we say "move the story from X to Y on the project board",
make sure to update the story in both places.

## GitHub issue

A story usually starts as a GitHub issue on a repository. Anyone (including
users) can open GitHub issues and not all issues will become stories. The
[Delivery Manager](roles.md#delivery-manager) selects which issues are
"sprint-ready" and adds them to a sprint. A sprint-ready story:

1. specifies the work to be done in a clear manner in the issue
    description or in a subsequent comment;
2. specifies the criteria for judging if the story is "done";
3. has a size estimate in days.

## The backlog refinement meeting

An important tool for transforming a GitHub issue into a sprint-ready story
is the Backlog refinement meeting. The aim of the meeting is to provide the 
Delivery Manager with enough sprint-ready stories to be able to create a sprint.

Typically one or two of these meetings is scheduled well before the next 
sprint by the Delivery Manager. The Delivery Manager will select a number of
issues that he judges to be candidates for the next sprint. The team will
discuss each issue and attempt to document the story as per (1) & (2) in the
previous list. If the team feel they don't yet know enough to estimate the 
size, the Delivery Manager creates a [Spike](workflow.md#terminology) to investigate
the issue further. Otherwise the team estimate the size and the GitHub issue 
is now sprint-ready story.

### Estimating the size of a story

We use the technique of 
[Planning poker](https://en.wikipedia.org/wiki/Planning_poker) to estimate the
size of a story. In particular, we use a variant called "Effort x Complexity".
For a given story, the team estimates the effort required to complete the story
and the complexity of that story and multiplies the resulting numbers to obtain
the size. Note the following:

* The effort estimate should be given **as if you are extremely familiar with
doing exactly this kind of story**.

* The following check-list can be used to help estimate complexity:

  * Do I know how to do this story? (estimate=1)
  * Does anyone in the team know how to do this story? (estimate=2)
  * Does anyone in the world know how to do this story? (estimate=3)

* When estimating effort it's important to include the total time that the team
spends coding, reviewing, and testing. While estimating, it can be useful 
to keep the following "average story" in mind:

  * A implements a feature.
  * B reviews the feature - 2 changes are requested.
  * A makes the code review changes.
  * B deploys to an appropriate environment and tests the feature - 1 bug is found.
  * A fixes the bug.


## Assignment

When someone starts tackling the story, they move it from the **backlog** to
**doing** on the project board.

If you are doing the story, assign yourself to the issue on GitHub.

## Implementation

The story is now being implemented.

If you are doing the story, create a new branch to do your work on. This should,
usually, be a branch from ``master``. Name your branch with the GitHub issue
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
