---
title: git-flow
date: 2016-11-03 15:51:06
tags: git, git flow
categories: git
---

## Using git-flow to automate your git branching workflow.

[ (_原文_)](http://danielkummer.github.io/git-flow-cheatsheet/index.zh_CN.html)

![](http://jeffkreeftmeijer.com/images/gitflow.gif)

After installing git-flow (brew install git-flow), you can start using git-flow in your repository by using it's init command. You can use it in existing projects, but let's start a new repository:

```
    $ git flow init
    Initialized empty Git repository in ~/project/.git/
    No branches exist yet. Base branches must be created now.
    Branch name for production releases: [master]
    Branch name for "next release" development: [develop]

    How to name your supporting branch prefixes?
    Feature branches? [feature/]
    Release branches? [release/]
    Hotfix branches? [hotfix/]
    Support branches? [support/]
    Version tag prefix? []
```

## Feature branches

    1. git flow feature start authentication
    2. git flow feature finish authentication

## Versioned releases

    1. git flow release start 0.1.0
    2. git flow release finish 0.1.0

## Hotfixing production code

    1. git flow hotfix start assets
    2. git flow hotfix finish assets

## set git 

```
git config --global alias.br branch
    git config --global alias.ci commit
    git config --global alias.co checkout
    git config --global alias.st status
    # 很好看地显示git log
    git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen (%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --"
    # 设置用户信息
    
```


