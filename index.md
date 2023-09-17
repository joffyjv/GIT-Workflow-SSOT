# Overview


## Objectives

* **SINGLE SOURCE OF TRUTH**
* **Clean Git history (graph) by combination of Rebase & Non-fast-forward merge**
* **Developer is accountable for branch life-cycle & maintenance**
* **Less-of-a-hassle release cycle (matter of merging your readied Pull Request)**

## High-level workflow for backend development
![Workflow](https://github.com/joffyjv/gwflow/blob/main/blob/wf.jpeg?raw=true)

## Best Practices
### Communication is CRUCIAL
For when you intend to rebase at development branches, it’s important to communicate to the team because of history rewriting!

### Rebase First!
Whether your in your own feature branch or in any of the main branches, before you merge to _master_ or staging branches, always rebase onto master FIRST! Reason is we want to make sure the feature branch or staging branches are on top of _**master**_.

### Merge with --no-ff (non-fast forward)

This is essential for getting a merge commit where fast forward do-not, so that we can see the history the commits respective to your merged feature branch.

![[Image]](https://github.com/joffyjv/gwflow/blob/main/blob/merge.jpeg)

### Use Git Alias!
Setting the following alias will help to reduce chances of mistake by simply running git CLI via alias.

**Setup alias for staging** <br />
`$ git config --global alias.update-staging '!git fetch && git checkout master && git branch -D staging && git checkout staging && git rebase origin/master && git push origin staging --force'`


After setting up the aliases, executing them simply with one liner and perform all the chain commands in order to rebase the development branch onto master. <br />
`$ git update-staging`

### Useful Git CLIs

**Merge with non-fast-forward** <br />

`$ git merge --no-ff <feature_branch>` <br />

**Rebase onto master from feature branch**<br />

`$ git fetch && git checkout <feature_branch> && git pull origin <feature_branch>`<br />
`$ git rebase origin/master`<br />
`$ git push origin <feature_branch> --force`<br />

**Rebase onto master from development branches (staging, pre-release)**<br />

`$ git fetch`<br />
`$ git checkout master`<br />
`$ git branch -D staging`<br />
`$ git checkout staging`<br />
`$ git rebase origin/master`<br />
`$ git push origin staging --force`<br />

OR, best to use git alias.
 ## staging branch update 
 `$ git rebase origin/master` <br />
 `$ git push -f` <br />
### Git Workflow steps for a feature implementation

Notes: 
Steps 3,4,5 and 6 are used to update the staging server.
Steps 12,13 and 14 are used to update the local branches.
1. Create a new branch from the master with task specifications as the branch name.
2. Push the task branch to the remote repo.
3. Run update-staging alias. `$ git update-staging` 
4. `$ git merge --no-ff <feature_branch>` <br />
5. `$ git rebase origin/master` <br />
6. `$ git push -f` <br />
7. Create a pull request to the master from the feature-branch.
8. `$ git fetch && git checkout <feature_branch> && git pull origin <feature_branch>`<br />
9. `$ git rebase origin/master`<br />
10. `$ git push origin <feature_branch> --force`<br />
11. Merge to master if everything is working fine in staging.<br />
12. `$ git checkout master`<br />
13. `$ git pull`<br />
14. `$ git update-staging`<br />

### Reverting a change in staging.
If you need to revert the changes on the staging server. You need to follow the below-mentioned steps:
1. `$ git log`<br />
2. Copy the commit id you want to revert to.
3. `$ git reset --hard <commit-id>`<br />
4. `$ git push --force`<br />

All changes from staging will be reverted to the <commit-id>.
