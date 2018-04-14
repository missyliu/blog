---
title: svn学习笔记
date: 2016-04-29
description: 关键字：svn 命令
---

## svn代码库推荐存储结构

```
| - trunk
| - branches （分支开发）
| - tags （发版打tag）
```

## svn常用命令

```
svn co URL = svn checkout URL = git clone URL
svn up = svn update = git pull
svn add . = git add . (svn 只有添加新文件时记着svn add)
svn ci -m "本次修改的注释" = svn commit -m "本次修改的注释" = git commit -m "本次修改的注释" + git push (svn 仅修改文件只需commit)
svn st = svn status = git status
svn mkdir URL = mkdir URL + svn add URL
svn mkdir -m "本次修改的注释" URL = mkdir URL + svn add URL + svn ci -m "本次修改的注释"
svn sw URL (切换工作副本到其他分支、标签，注意切换会将没有提交的修改混合)
svn log = git log
当前开发分支下: svn merge URL(基线) master ＝ 当前开发分支下: git merge master (将master合并到当前开发分支下) ｛！！！疑惑：基线｝
svn revert . -R = git reset MD5 --hard
svn cleanup (因某些原因工作副本滞留在一个不一致的状态，可以用cleanup来解决)
svn diff = git diff
svn resolve --accept=ARG [PATH...] (解决冲突) ｛！！！疑惑：基线｝
```

## 工作时常用命令以及流程

```
$ svn co URL
$ svn add .
$ svn up
$ svn diff
$ svn status
$ svn ci -m "本次修改的注释"
```