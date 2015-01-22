# Project Management

## Technical

### Source Control
Source code for the project will be maintained using Git, and hosted on
GitHub. We will attempt to follow [A successfull Git branching
model](http://nvie.com/posts/a-successful-git-branching-model/) to ensure that
our master branch is stable and working as much as possible. This will ensure
that when we come to demonstrate our software we always have a functional
version, even if it is missing some features.

Code will be peer-reviewed; this means that code should not be pushed directly
to the `master` or `develop` branches. To add code, commit to a new branch,
push the branch and submit a new pull request. All developers should "watch"
the repos on Github so that they are notified of other developers' pull
requests.

### IDE / Environment
We will use IntelliJ IDEA to develop the Condor and Triton branches, and a
regular text editor to develop the Specification branch.

We will use the latest version of IntelliJ; if you are ever prompted for
updates, please do so. If this software update results in generated files
being changed then commit those changes to a separate branch.

We will use UNIX line endings for most files; this means that on Windows
computers, Notepad won't work as a text editor.

### Testing
Code will be tested frequently, both manually by developers during development,
and automatically using a continuous integration platform such as Travis CI.

Manual tests will most likely occur during regular development; if something
doesn't work, it should be fixed fairly promptly. If the person who discovers it
doesn't know how to fix, an issue should be filed on Github.

Automatic tests will be hooked into Github; each new branch will have tests run
on it by the CI platform, and developers should wait for tests to finish before
committing.

Where appropriate, code should be written with accompanying unit tests; these
tests should live in a separate, non-production test folder and should cover as
much critical code as possible. These tests will help us discover when a change
breaks previously working functionality, as well as assisting the development of
new code.

## Non-Technical
### Group Organisation
Nick Rogers has been appointed as project manager, and so is responsible for 
being our primary point of contact with the client. All communication
should go via Nick (including deliverables, organisational emails etc)
unless it is necessary to do otherwise.

### Meetings
Informal group meetings will be organised via Facebook and will normally occur
in the slots allocated for group projects by the computer lab. All members
shall attend all meetings if required, and all members must attend the formal
meetings with the client.
