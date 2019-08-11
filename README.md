# Git exercises

To make each assignment, run the `setup.sh` file and examine the git repository in the `exercise` folder.

You need to provide the git commands you need to solve the task, as well as a copy of the following command from each repository:

`git log --oneline --graph --decorate --all`

## 1

The git commit history looks like a developers internal "I gotta save this" work. Not suited for public.
All work belongs to a task called "#321"

### Task

1. _Squash_ the five relevant commits into one, with the commit message of "close #321"
1. How does `git log` look now?

### Answer

Git commands:

`git rebase -i 040d623`

Git log:

`* d07c283 (HEAD -> master) close #321`

`* 040d623 initial file`

## 2

You develop a new feature on the branch `new-feature`. You have already
implemented the first part of a feature, when you are notified of a critical
bug that has to be fixed right away on the `master` branch.

After the bug fix, you continue to work on the new feature. After you committed the second part of the feature, you realize that you have done your commit on the `master` branch instead of the feature branch.

### Task

1. Move the faulty commit from the `master` branch to the `new-feature` branch.
1. Copy the bugfix to your feature branch as well
1. The commit containing the second part of the feature makes master fail in the CI and you need to take that change out. How would you do that? Answer should provide both the command and the reasoning behind it.

### Answer

Git commands:

```git checkout new-feature
git cherry-pick e5fbc1e 1b1e21e
```

Then I fix a conflict.

```git add myapp.txt 
git commit -m "Implement second part of feature"
git checkout master
git reset --hard e5fbc1e
```

Git log:

```
* fb5db76 (new-feature) Implement second part of feature
* bbacc6f Fix bug
* 0beb584 Implement first part of feature
| * e5fbc1e (HEAD -> master) Fix bug
|/  
* 412195f Initial commit
```


## 3

You have developed a new feature, and wants to commit it to master:

```bash
* 1f37b43 (HEAD -> master) Add readme
| * a824913 (uppercase) Change greeting to uppercase
|/  
* b84f28f Add content to greeting.txt
* efb74a6 Add file greeting.txt
```

Instead of just merging the commit, you like a straight line of commits like the example below

```bash
* 47558e0 (HEAD -> uppercase) Change greeting to uppercase
* 1f37b43 (master) Add readme
* b84f28f Add content to greeting.txt
* efb74a6 Add file greeting.txt
```

### Task

* Show the commands in order to achieve this position of commits.
* Why does the commit with message "Change greeting to uppercase" change sha, when the others do not?

## 4

Look at the git graph and status of the created repository to find out the state.

### Task

* In words, describe what you are seeing in the repository. Use the git terminology when applicable.

Show the list of commands you need to do the following (in the given order).

* remove the work in progress using git.
* remove the staged change
* make master go back to the commit before the bad commit
* does git track bfile.txt? Reason your answer.

## 5

### Task

* In words, describe what you are seeing in the repository. Use the git terminology when applicable.

Show the list of commands you need to do the following (in the given order).

* Move to `master`
* Make a branch  called `the-beginning` that is made from the first commit with message `A`
* Show how you would find the commit with the message `E` and make a branch called `dangling` on that commit.
