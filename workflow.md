# Working practices

This section discusses how we, as a team, structure our work. EXAMPLE

## Terminology

The fundamental unit of work is a "story". A story is a defined task which is
focussed on a particular outcome. Stories have work estimates associated with
them; Work estimates are given in units of "days".

Examples of stories:

* Add a "plusOneCount" to the "FeatureRequest" resource which reflects the
    number of times the feature request has been plus-oned by a user. **1 day.**
* Investigate integrating the Sphinx documentation generator into the car park
    visitor space booking application. **1 day. Spike.**
* Rename the "doubleplusgood" project on GitHub to "newthink". **Chore.**

Some terminology:

* A "spike" is a story which is typically an investigation and is used when the 
    team don't have enough information to tackle a story. This type of story 
    will always be timeboxed. In the example above, after a day of work, 
    the person doing the story stops and updates the rest of the team on 
    progress. This can be at the daily standup or via a written report on, e.g.,
    a GitHub issue.
* A "chore" is a story where no *new* work is envisaged and are likely to take
    significantly less than a day. We add them to the list of stories so that we
    can track their progress but we expect them to be so small that they do not
    need to contribute to the total work estimate for a sprint.

## Sprints

We organise work into two week "sprints". Each sprint consists of a set of
stories for that sprint which are to be tackled and an associated GitHub project
which tracks GitHub issues/pull requests for those stories. A story can be in
the following states:

* **Backlog.** Not yet started.
* **Rework.** Changes have been requested by a reviewer.
* **Doing.** Being tackled by someone.
* **Review queue.** Development work has been completed and the work is ready
    for code review.
* **Review.** Being code reviewed by someone.
* **Test queue.** The work has passed code review and is ready for testing.
* **Test.** Being tested by someone.
* **Done.** The work has been completed. For code changes, this usually implies
    having been merged to the ``master`` branch.

## Daily standup meetings

Each workday morning at around 9:45am we have a standup meeting around the
current sprint board. At this meeting we each update the team on what we did on
the previous work day, what we're working on that day and anything which has
arisen which stops work proceeding. (These are termed "blockers".)

We have also taken to having brief informal discussions on stories or on wider
institutional matters in the washup of the meeting.

Standups rarely last more than 15 minutes.
