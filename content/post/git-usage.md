---
title: Git 常用
date: "2019-01-04 08:33:23"
tags: ["git"]
---

### Setup Git
```Plain
$ git config --global user.name "username"
$ git config --global user.email username@email.com
$ git config --list
```

### 代码提交
```Plain
$ git init 
$ git add .
$ git commit -m "init commit"
$ git push origin master 
$ git push origin master -f                 # 强制提交
```

<!--more-->

### 代码更新
```Plain
$ git fetch --all                           # 下载远程的库的内容
$ git pull                                  # git pull = git fetch + git merge
$ git reset HEAD^                           # 放弃上次 commit，本地修改还在
$ git reset --hard origin/master            # 放弃本地内容，使用服务端强制覆盖本地
```

### 打标签
```Plain
$ git tag                                   # 查看标签列表
$ git tag <tag_name> -m "msg"               # 打标签
$ git push origin <tag_name>                # 提交标签
$ git tag                                   # 查看标签列表
$ git show <tag_name>                       # 查看标签详情
$ git tag -d <tag_name>                     # 删除本地标签
$ git push origin :refs/tags/<tag_name>     # 删除远端标签
$ git checkout <tag_name>                   # 切换到指定标签
```

### 设置多个上游
```Plain
$ git remote -v                             # 查看上游设置
$ git remote add upstream ssh://xxx.git     # 添加上游
$ git pull upstream master                  # 更新上游代码
$ git fetch upstream                        # 获取 fork 的原始上游代码
$ git checkout master                       # 切换到自己仓库的 master
$ git merge upstream/master                 # merge 并解决冲突
$ git remote rm upstream                    # 删除上游
```

### 分支操作
```Plain
$ git branch -d <BranchName>                # 删除本地分支
$ git push origin --delete <BranchName>     # 删除远程分支
$ git branch -a                             # 列出所有分支
$ git checkout -b master origin/master      # 切换远端分支
```

### Gerrit
```Plain
$ git commit --amend                    # 与上次提交合并， Gerrit 中带上 commitId 可以实现 update patch set
```

