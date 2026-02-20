# git notes

Main source: https://www.w3schools.com/git/git_branch_merge.asp?remote=github

## when to create a branch

Branches are like a separate workspace to make changes and try new things without affecting the main project. Common reasons to create one:

- Developing a new feature
- Fixing a bug
- Experimentation

### create branch 
``` bash
git checkout -b branch-name 
```

### list branches
``` bash
git branch
```

## staging 

``` bash
git add --all # stage all files
git add <file> # stage a file
git restore --staged <file>
```

## commiting

A commit is like a save point in the project. It recrods a snapshot of the files at a certain time, and contains a message escribing what has changed.

```bash
git commit -m "message" # commit staged changes
git commit -a -m "message" # commit all tracked changes without staging
```

### commit message: best practices

- Short
- Imperative
- Describe what changed and why

### typical commit mistakes

- Accidentally commited the wrong files
```bash
git reset --soft HEAD~1 # undo the last commit and keep changes staged
```
- Typo in the message
```bash
git commit --amend -m "Corrected message" # fixes the last commit message
```

## stashing

Stashing allows to save uncommitted changes and return to a clean working directory to later come back and restore the changes. It is a way of:

- Switching branches safely
- Handle emergencies

```bash
git stash # saves changes and cleans the working directory to safely switch tasks or branches
git stash push -m "WIP: new feature" # stash with a message
```

## merging

Used to combine the changes from one branch into another. It is a way of bringing work together after working separately. A good rule of thumb is to switch to the branch I want to merge into (typically main or master) and to run the merge command with the branch name to combine in.

```bash
git checkout main
git merge feature-branch
git merge
```

## when to delete a branch

## creating pull requests
