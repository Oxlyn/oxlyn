---
title: "使用 Hugo 生成站点"
date: 2019-01-04T15:16:29+08:00
tags: [ "hugo", "even"]
---

### 1. 目录结构
1. 安装 [Hugo](https://github.com/gohugoio/hugo)  
2. 生成站点：`hugo new site blog`

```
blog
├── archetypes
├── config.toml
├── content
├── data
├── layouts
├── static
├── themes
└── public
```
- archetypes 模板目录
- config.[toml](https://github.com/toml-lang/toml) 全局配置文件
- content 文章存放目录
- data 用来存储网站用到一些配置、数据文件。文件类型可以是 yaml | toml | json 等格式。
- layouts 渲染模板文件
- static 存放静态资源
- themes 存放主题
- public 编译后生成的发布文件

<!--more-->

### 2. 常用命令
- `$ hugo new post/helloworld.md` 根据 archetypes 下的模板生成新的 blog 文章
- `$ hugo` 构建发布文件
- `$ hugo server -D` 启动本地调试服务，-D 包括 draft 文件
- `$ hugo -d public` 构建到指定目录

### 3. 模板配置
```Plain
---
title: "Title"
description: "desc"
date: 2011-11-11T11:11:11-11:11
tags: ["Hugo", "Go"]
categories: ["Hugo"]
slug: sss
project_url: https://example.com
draft: true
---
```

### 4. 更换电脑时，初始化项目奖
#### 1. clone 源码分支
`$ git clone git@github.com:oxlyn/oxlyn.github.io.git -b source`

#### 2. 设置 user & email
`$ git config user.name "Oxlyn"`

`$ git config user.email "oxlyn@hotmail.com"` 

#### 3. clone master 分支到 public 目录
`$ git clone git@github.com:oxlyn/oxlyn.github.io.git -b master public`

#### 4. 设置 Coding Pages 上游
`$ git remote add upstream git@git.coding.net:Oxlyn/oxlyn.git`

#### 5. 提交 source 到 github
`$ git push origin source`

#### 6. 提交 public 到 github & coding
`$ cd public`  
`$ git push origin master`  
`$ git push upstream master`  