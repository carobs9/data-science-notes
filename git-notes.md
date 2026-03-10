# git notes

Main sources are [Oh Shit, Git!?!](https://ohshitgit.com/) and the [w3schools git tutorial](https://www.w3schools.com/git/git_branch_merge.asp?remote=github).

## when to create a branch

Branches are like a separate workspace to make changes and try new things without affecting the main project. Common reasons to create one:

- Developing a new feature
- Fixing a bug
- Experimentation

### create branch 
``` bash
git checkout -b branch-name 
```

### list local branches
``` bash
git branch
```

### list remote branches
``` bash
git branch -r
```

### list local and remote branches
``` bash
git branch -a
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
### when everything has been merged but everything is also a mess and you regret it
```bash
git merge --abort
```

### everything is still messy, i don't know what's going on but the main branch is the golden standard and i want my branch to look like it
```bash
git merge --abort
git fetch origin # fetch latest remote state
git reset --hard origin/main # discard all local changes on specific branch, making the specific branch identical to main
git push --force # remotely make the branch match main
```

### i managed to make my branch look like main, but i accidentally deleted a file i needed
```bash
git reflog # helps looking into history and finding the commit with the needed file
git show --name-only b62a624 # displays the name of the file
git restore --source b62a624 path/to/file # collect file
```

## when to delete a branch

In progress...

## creating pull requests

In progress...

## changes made but do not belong to current branch

### if changes are not yet committed

If this happens I can just create a new branch, switch to it and commit whatever I want:

```bash
git switch -c <new-branch-name>
git add . 
git commit -m "Add changes of interest"
```

### if changes are committed

```bash
git branch <new-branch-name> # create new branch at current commit
git switch <original-branch> # go back to original branch
git reset --hard HEAD~1 # remove most recent commit
```

