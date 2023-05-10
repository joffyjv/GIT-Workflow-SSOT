# Overview


## Objectives

* **SINGLE SOURCE OF TRUTH**
* **Clean Git history (graph) by combination of Rebase & Non-fast-forward merge**
* **Developer is accountable for branch life-cycle & maintenance**
* **Less-of-a-hassle release cycle (matter of merging your readied Pull Request)**

## High-level workflow for backend development
![[BE](https://github.com/iBeCo/Team/blob/master/img/wf.jpeg)](https://github.com/joffyjv/gwflow/blob/main/blob/wf.jpeg)

## Best Practices
### Communication is CRUCIAL
For when you intend to rebase at development branches, it’s important to communicate to the team because of history rewriting!

### Rebase First!
Whether your in your own feature branch or in any of the main branches, before you merge to _master_ or dev branches, always rebase onto master FIRST! Reason is we want to make sure the feature branch or dev branches are on top of _**master**_.

### Merge with --no-ff (non-fast forward)

This is essential for getting a merge commit where fast forward do-not, so that we can see the history the commits respective to your merged feature branch.

![[Image](https://github.com/iBeCo/Team/blob/master/img/242621193_588242542357810_206814242058425790_n.jpeg)](https://github.com/joffyjv/gwflow/blob/main/blob/merge.jpeg)

### Use Git Alias!
Setting the following alias will help to reduce chances of mistake by simply running git CLI via alias.

**Setup alias for staging** <br />
`$ git config --global alias.update-dev '!git fetch && git checkout master && git branch -D dev && git checkout dev && git rebase origin/master && git push origin dev --force'`


After setting up the aliases, executing them simply with one liner and perform all the chain commands in order to rebase the development branch onto master. <br />
`$ git update-dev`

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
`$ git branch -D dev`<br />
`$ git checkout dev`<br />
`$ git rebase origin/master`<br />
`$ git push origin dev --force`<br />

OR, best to use git alias.
 ## dev branch update 
 `$ git rebase origin/master` <br />
 `$ git push -f` <br />
### Git Workflow steps for a feature implementation

TBF
