# Git cheatsheet

## Remove previous commits
```
git rebase -i HEAD~4
```
then `pick` commits you want to stay, and `drop` commits you want to delete

## Create branch and checkout
```
git checkout -b <branch_name>
```
