# Basic team git workflow
Master branch should always contain working version of a project. All new features should be made in different branches and than merged to master.

So you should create new branch, make a feature and merge feature branch to master. Than branch can be deleted. And created a new one for another feature.

Basic pipeline:

Create a new branch and go there
```
git checkout -b new_feature
```
There code a new feature and changes to the branch

When feature is ready checkout to master
```
git checkout master
```
Create merge commit
```
git merge --no-ff new_feature
```
If there are no conflicts after merge, push
```
git push
```
If have conflicts, resolve them (vscode is good for this purpose)

Create new commit and push
```
git add -A
git commit -m "message"
git push
```
