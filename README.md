practice-git
============

A repository setup to practice git

The purpose of this tutorial is to practice merging, branching, and
rebasing.

To start the tutorial

`git clone git://github.com/imintel/practice-git.git`

Go ahead a do a `git fetch` as well do get all the branches.

###Lesson one - Merging

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
  git merge merge-2
```



