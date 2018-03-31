---
title: git-note
date: 2017-03-27 19:23:31
tags: git, note
categories: git
---

## git使用笔记
1. ### git 一些设置
  ```
  git config --global alias.br branch
  git config --global alias.ci commit
  git config --global alias.co checkout
  git config --global alias.st status
  # 很好看地显示git log
  git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen (%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --"
  git config --global log.date iso
  # 设置用户信息
  ```
1. ### 用git config命令查看配置文件

  命令参数
  –list, 简写 -l
  格式：git config [–local|–global|–system] -l
  查看仓库级的config，git config –-local -l
  查看全局级的config，git config -–global -l
  查看系统级的config，git config –-system -l
  查看当前生效的配置：git config -l，显示最终三个配置文件计算后的配置信息

1. ### git remote

  ```
  git remote add helloworld git@github.com:helloworld/helloworld.github.io.git
  ```
  上面的命令就会增加URL地址为

  ```
  git@github.com:helloworld/helloworld.github.io.git
  ```
  ，名称为 helloworld 的远程服务器，以后提交代码的时候只需要使用 helloworld 别名即可
  查看远程仓库：$ git remote -v
  添加远程仓库：$ git remote add [name] [url]
  删除远程仓库：$ git remote rm [name]
  修改远程仓库：$ git remote set-url –push [name] [newUrl]
  拉取远程仓库：$ git pull [remoteName] [localBranchName]
  推送远程仓库：$ git push [remoteName] [localBranchName]

  *如果想把本地的某个分支test提交到远程仓库，并作为远程仓库的master分支，或者作为另外一个名叫test的分支，如下：
  $git push origin test:master // 提交本地test分支作为远程的master分支
  $git push origin test:test // 提交本地test分支作为远程的test分支

1. ### 分支(branch)操作相关命令
  查看本地分支：$ git branch
  查看远程分支：$ git branch -r
  创建本地分支：$ git branch [name] —-注意新分支创建后不会自动切换为当前分支
  切换分支：$ git checkout [name]
  创建新分支并立即切换到新分支：$ git checkout -b [name]
  删除分支：$ git branch -d [name] —- -d选项只能删除已经参与了合并的分支，对于未有合并的分支是无法删除的。如果想强制删除一个分支，可以使用-D选项
  合并分支：$ git merge [name] —-将名称为[name]的分支与当前分支合并
  创建远程分支(本地分支push到远程)：$ git push origin [name]
  删除远程分支：$ git push origin :heads/[name] 或 $ gitpush origin :[name]

  *创建空的分支：(执行命令之前记得先提交你当前分支的修改，否则会被强制删干净没得后悔)
  $git symbolic-ref HEAD refs/heads/[name]
  $rm .git/index
  $git clean -fdx

1. ### 版本(tag)操作相关命令
  查看版本：$ git tag
  创建版本：$ git tag [name]
  删除版本：$ git tag -d [name]
  查看远程版本：$ git tag -r
  创建远程版本(本地版本push到远程)：$ git push origin [name]
  删除远程版本：$ git push origin :refs/tags/[name]
  合并远程仓库的tag到本地：$ git pull origin –tags
  上传本地tag到远程仓库：$ git push origin –tags
  创建带注释的tag：$ git tag -a [name] -m ‘yourMessage’

1. ### 子模块(submodule)相关操作命令

  添加子模块：$ git submodule add [url] [path]
  如：$git submodule add git@github.com:helloworld/hexo-theme-next.git themes/next

  初始化子模块：$ git submodule init —-只在首次检出仓库时运行一次就行
  更新子模块：$ git submodule update —-每次更新或切换分支后都需要运行一下

  删除子模块：（分4步走）

  1. $ git rm –cached [path]
  1. 编辑“.gitmodules”文件，将子模块的相关配置节点删除掉
  1. 编辑“ .git/config”文件，将子模块的相关配置节点删除掉
  1. 手动删除子模块残留的目录

1. ### .ssh权限问题

  Permissions 0644 for ‘/home/robin/.ssh/id_rsa’ are too open.
  It is recommended that your private key files are NOT accessible by others.
  This private key will be ignored.
  bad permissions: ignore key: /home/robin/.ssh/id_rsa

  解决方案
  ```
  chmod 755 ~/.ssh/
  chmod 600 ~/.ssh/id_rsa ~/.ssh/id_rsa.pub
  chmod 644 ~/.ssh/known_hosts
  ```
