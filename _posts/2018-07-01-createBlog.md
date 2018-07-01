---
layout: post
title: 搭建博客
date: 2018-07-01 
tags: 搭建博客   
---

本博客最早也是参照别人的创建的.参见 [Jekyll搭建个人博客](http://baixin.io/2016/10/jekyll_tutorials1/).但是也遇到一些问题,记录一下.


### 安装 jekyll的问题
因为默认使用了mac自带的Ruby,在install gem时,写入路径为系统目录,没有权限.所以按照这篇文章[Mac OS X 下使用 Ruby Gem 的两个坑](https://www.jianshu.com/p/bb9fe3fd45d0)重新安装了一个Ruby.


### jekyll启动时的问题
jekyll server后报错:
```
/usr/local/lib/ruby/gems/2.5.0/gems/bundler-1.16.2/lib/bundler/runtime.rb:313:in `check_for_activated_spec!': You have already activated jekyll 3.8.3, but your Gemfile requires jekyll 3.5.2. Prepending `bundle exec` to your command may solve this. (Gem::LoadError)
```
这种错误,手动一个一个修改 /vim Gemfile.lock中对应的组件的版本值,一直到出现了新的错误
```
Dependency Error: Yikes! It looks like you don't have jekyll-watch or one of its dependencies installed. In order to use Jekyll as currently configured, you'll need to install this gem. The full error message from Ruby is: 'cannot load such file -- ruby_dep/warning' If you run into trouble, you can find helpful resources at https://jekyllrb.com/help/!
```
尝试方案  gem list jekyll-watch
gem uninstall jekyll-watch -v 1.0.0
删除模块的多余版本,但是依旧不能运行.

后续一次修改Gemfile.lock失败,导致了文件不可读,出现了如下错误:
```
Your lockfile is unreadable. Run `rm Gemfile.lock` and then `bundle install` to generate a new lockfile. (Bundler::LockfileError)
```
执行bundle install 后可用了.我怀疑第一次就 rm Gemfile.lock 然后 bundle install就可以用了.

### 后续配置项

> * [百度统计](https://tongji.baidu.com/web/welcome/login) 申请账号,查看代码,里边有一个id. 配置到_config.yml的baidu id配置项中.

> * [Google 跟踪](https://analytics.google.com/) 同上,配置申请的 跟踪 ID 到ga.id.

> * 赞赏的收款码在 /image/payimg/目录下.


转载请注明：[张浩的博客](https://zhanghao001.github.io/) » [点击阅读原文](https://zhanghao001.github.io/2018/07/createBlog/)     
