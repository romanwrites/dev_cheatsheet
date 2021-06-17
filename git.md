# Git cheatsheet

## What --no-ff option does
`--no-ff` means "no fast-forwarding"  
Using this option makes git create merge commit  
By default, fast forwarding is enabled, and the `git merge branch` operation will simply move all commits from the branch to the master
<img src="img/git/no-ff.jpg">
Let's look at the image.
1. I create `a,b` commits on `master`.
2. Checkout to a new branch `feature_branch_with_ff`.
3. Create the commits `c,d,e,f`.
4. Checkout back to `master` and run `git merge feature_branch_with_ff` command.  
As you can see, all the commits from `feature_branch_with_ff` look as if they were always on the `master` branch.  
5. Checkout to a new branch `feature_no_ff`.
6. Create the commits `g,h,i,j,k`.
7. Checkout to `master` and run `git merge --no-ff feature_no_ff`  
Only merge commit was created on master. 

more on [stackoverflow](https://stackoverflow.com/questions/9069061/what-is-the-difference-between-git-merge-and-git-merge-no-ff)

## Remove previous commits
```
git rebase -i HEAD~4
```
then `pick` commits you want to stay, and `drop` commits you want to delete

## Create branch and checkout
```
git checkout -b <branch_name>
```