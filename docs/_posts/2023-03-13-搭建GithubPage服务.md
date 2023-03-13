---
layout: post
title:  "搭建GitHubPage服务"
date:   2023-03-13 16:24:08 +0800
categories: tools
---

# 搭建GitHubPage服务

我们可以使用Github Page来便捷的部署基于markdown格式的静态文本，内容在免费的二级域名`username.github.io`,基于此也可以申请maven central的group
id等内容。 本文主要用来记录部署过程

## 环境

- 系统: macos big sur
- blog软件: jekyll

## 安装Jekyll

Jekyll是一个基于markdown的静态站点生成框架，基于ruby开发，所以本地调试需要一套ruby的环境。 由于网络因素，放弃使用homebrew，转而使用`rbenv-cn`
来安装、管理ruby，目标是在本地环境安装ruby 3.1.3版本(Jekyll文档建议), 并使用国内镜像来安装ruby gems

1. 参考[rbenv-cn]的文档，安装rbenv-cn

```bash
# 安装rbenv-cn
bash -c "$(curl -fsSL https://gitee.com/RubyKids/rbenv-cn/raw/main/tools/install.sh)"
```

2. 替换gem源

```bash
# 替换gem源
gem source -r https://rubygems.org/ 
gem source -a https://gems.ruby-china.com 
# 替换bundler源
bundle config 'mirror.https://rubygems.org' 'https://gems.ruby-china.com' 
```

3. 安装、设置、校验ruby

```bash
#安装3.1.3版本ruby
rbenv install 3.1.3
#全局使用3.1.3版本ruby
rbenv gloabl 3.1.3
# 测试ruby,输出应类似 ruby 3.1.3p185
ruby -v
```

## Github Page配置
1. 参考[GitHub Page]的文档，新建一个名为username.github.io的空repository
2. 将repository clone到本地，并使用命令`jekyll new --skip-bundle .`来初始化一个jelyll项目
3. 在`Gemfile`中将`# gem "github-pages"`注释掉
4. 在`Gemfile`中添加内容`gem "github-pages", "~> 228", group: :jekyll_plugins`来启用github-pages，后面版本号使用最新的
5. 使用命令`bundle add webrick`安装Gem`webrick`
6. 安装gem并本地调试jekyll
```bash
bundle install
bundle exec jekyll serve
```
7. 在本地测试内容是否正常，并将内容推到github，然后即可在`https://username.github.io`来访问文档

[rbenv-cn]: https://gitee.com/RubyKids/rbenv-cn
[GitHub Page]: https://docs.github.com/en/pages