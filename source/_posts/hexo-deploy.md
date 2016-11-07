---
title: Hexo 部署概要
date: 2016-04-21 20:12:00
tags: [hexo, git]
---

#### 安装 Hexo

1. Install Homebrew
`$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
`
2. Install Git
`$ brew install git`
3. Install Nvm:
`$ Curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | sh`
4. Install Node.js
`$ nvm install 5`
5. Install Hexo
`$ npm install hexo-cli -g`

<!--more-->

#### 部署到 coding 和 github

1. 初始化
``` bash
$ hexo init <your_blog>
$ cd <your_blog>
$ npm install
```
2. 设置 [_config.yml](https://hexo.io/docs/configuration.html) 
   在 github 和 coding 上创建项目 oxlyn，并开启 Pages 服务。_config.yml 中 deploy 部分配置如下：
```
deploy:
  type: git
  repo: 
    github: git@github.com:oxlyn/oxlyn.git,gh-pages
    coding: git@git.coding.net:oxlyn/oxlyn.git,coding-pages
```

3. 设置git
```
$ git config --global user.name '<your_name>'
$ git config --global user.email '<your_email>'
```
4. Deploy
先上传公钥到 github 和 coding，然后 deploy。
```
$ npm install hexo-deployer-git --save
$ hexo deploy
```

#### 将源码提交到 github

1. 设置 origin
`git remote add origin git@github.com:oxlyn/oxlyn.git`
2. 提交
```
$ git init .
$ git add .
$ git commit -m '<commit_msg>'
$ git push origin master
```

#### 安装主题

* [Install](https://github.com/pinggod/hexo-theme-apollo)
```
$ npm install --save hexo-renderer-pug hexo-generator-feed hexo-generator-sitemap hexo-browsersync hexo-generator-archive
$ git clone https://github.com/pinggod/hexo-theme-apollo.git themes/apollo
```
* 更改 _config.yml，启用主题
```yaml
theme: apollo

# 在归档页面显示所有文章
# 需要上面安装的 hexo-generator-archive 插件支持
archive_generator:
    per_page: 0
    yearly: false
    monthly: false
    daily: false
```