practice-git
============

A repository setup to practice git

The purpose of this tutorial is to practice merging, branching, and
rebasing.

To start the tutorial

`git clone git://github.com/imintel/practice-git.git && cd practice-git`

###Lesson one - Merging

##Setup

`git checkout merge-1 && git checkout merge-2 && git checkout merge-3 && git checkout merge-4 && git checkout master`

####Scenario

Clojure decided nil => null, but someone thought it was nil => pizza

```bash
  git checkout merge-1
  git merge merge-2
```

Clojure decided to change ( => [ and ) to => ] , but someone on the team thought it
was just $ signs

```bash
  git checkout merge-3
  git merge merge-4
```

###Lesson two - Workflows with rebase

```bash
  git checkout -b feature-1
```
The -b flag tells git to use a new branch.

Alternatively we could have done,

```bash
  git branch feature-1
  git checkout feature-1
```

feature-1 is a feature you have to implement. 

Now make 4 - 5 commits, arbitrary changes are fine.

Now we want to get some commits into one commit because they are all
referencing the same task within that feature-1.

We want to rebase back to the HEAD commit on master.

To see the head commit

`git log master` and copy the SHA of the top commit

Now we are ready to prepare feature-1 to be added to master.

```bash
  git rebase SHA_OF_MASTER_HEAD -i
```
The -i is for interactive mode

You should see your text editor popup! As a side note, if you want to
change your default editor it is possible.

Assuming you are still have 'feature-1' checked out, the `git log`
should look like the commits you "rebuilt" with rebase on top of the
HEAD commit on master.

Now you are ready to bring your work over to master. I typically will
use rebase again, but merge can also be used.

```bash
git checkout master
git merge feature-1
```

Under the hood this is what github pull requests do.

Alternatively, you can use rebase! But first when want to clear the
commits we just added to master.

###Using `git reset`

git reset can be your best and worst friend at times if you don't know
how to use the command.

For now, we are using it to get the commits off of master that we just
merged from feature-1. `git reset` first param is a commit reference.
That can be a SHA, HEAD, HEAD~1, HEAD~n. For us, we are going to use the
SHA of the head of master from earlier. We can also pass a flag to
reset, --hard. The --hard flag clears all changes. By default, it uses
--soft, which keeps the diff in the working tree.

```bash
  git reset SHA_OF_MASTER_FROM_BEFORE --soft
  git status
```

The `git status` will show you the changes from all of the commits that
were "reset". We don't need these, so we will `git stash`.

Now lets add those commits to master from feature-1 with a rebase.

`git rebase feature-1`


