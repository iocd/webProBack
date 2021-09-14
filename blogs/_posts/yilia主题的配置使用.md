---
layout: post
title: "yilia主题的配置使用"
date: 2021-9-6 14:56
comments: true
toc: true
reward: true
tags: 
	- web
	- 博客
typora-root-url: ..\..
---

## yilia主题的配置使用

主要为了在 github page 发布静态网页的博客。写的是md笔记，用hexo编译后就是静态网页了，yilia 之类的主题是可选使用



#### 一、先安装软件

<!-- more -->

注意：nodejs 的16.8.0版本在win11上，`npm install` 会报错，建议先安装低一点的版本尝试。

| 下载                                 | 安装                                                         | 备注                                     |
| ------------------------------------ | ------------------------------------------------------------ | ---------------------------------------- |
| [Python](https://www.python.org/)    | [在windows下安装Python(Python入门教程)](https://my.oschina.net/u/3704591/blog/4566022) | nodejs依赖python                         |
| [nodejs](http://nodejs.cn/download/) | [npm安装教程](https://www.cnblogs.com/lgx5/p/10732016.html)  | npm依赖于nodejs。`npm install`能使用即可 |



#### 二、安装 hexo

```sh
npm install -g hexo-cli -verbose
```



#### 三、使用

1.初始化

```sh
mkdir blog
cd blog
hexo init
# 下载 yilia 主题
git clone https://gitee.com/llkCharles/hexo-theme-yilia.git themes/yilia
```



2.在 根目录 `./blog/_config.yml` 修改配置为 **`theme: yilia`** 后，在自行配置 **`themes/yilia/_config.yml`** 。参考文尾



3.hexo目录结构，主要如下，其他先不管

```sh
├─public #最终生成的文件在这里
├─source
│  └─_posts
│       └─hello-world.md #hexo把它编译成html放入public目录
└─themes
    └─yilia
        └─_config.yml #yilia之类的主题主要配置这个即可
```

md里的图片、视频等素材，可放在 `source` 下的自定义目录里。

md文档里 图的路径设置成绝对路径网站访问不到c盘，相对路径与public最终目录里的又不匹配，还得研究。。



4、开始写文。md笔记头部自行设定

```yaml
layout: post
title: "yilia 主题的配置使用"
date: 2021-9-6 14:56
comments: true
toc: true # 目录
reward: true # 打赏
brief: "摘要不好使"
tags: 
	- web
	- 博客
```

![image-20210906184554990](/blogs/assets/blogimg/yilia主题的配置使用/image-20210906184554990.png)

5.编译测试发布

```sh
hexo g
hexo s
```

本地浏览ok之后，可以吧 public 目录里的网站传到 github page 啦



#### 四、_config.yml的配置参考

```
# 打赏设定：0-关闭打赏； 1-文章对应的md文件里有reward:true； 2-所有文章均有打赏
# 目录设定：0-不显示； 1-文章对应的md文件里有toc:true； 2-所有文章均显示目录

# 不使用的某项，比如
smart_menu:
  friends: false
```



**`_config.yml`** 

```yaml
# Hexo Configuration
## Docs: https://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site
title: 红叶的博客
subtitle: 胆小认生，不易相处
description: 此为博客一枚0
keywords:
author: 红叶
language: en
timezone: ''

# URL
## Set your site url here. For example, if you use GitHub Page, set url as 'https://username.github.io/project'
url: https://zilv.icu/blogs
root: /blogs/
permalink: :year/:month/:day/:title/
permalink_defaults:
pretty_urls:
  trailing_index: true # Set to false to remove trailing 'index.html' from permalinks
  trailing_html: true # Set to false to remove trailing '.html' from permalinks

# Directory
source_dir: blogs # 因为博客在站点子目录（/blogs/）下，所以这里吧工程目录设置为md图片根目录
public_dir: public
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
i18n_dir: :lang
skip_render:

# Writing
new_post_name: :title.md # File name of new posts
default_layout: post
titlecase: false # Transform title into titlecase
external_link:
  enable: true # Open external links in new tab
  field: site # Apply to the whole site
  exclude: ''
filename_case: 0
render_drafts: false
post_asset_folder: true
relative_link: false
future: true
highlight:
  enable: true
  line_number: true
  auto_detect: false
  tab_replace: ''
  wrap: true
  hljs: false
prismjs:
  enable: false
  preprocess: true
  line_number: true
  tab_replace: ''

# Home page setting
# path: Root path for your blogs index page. (default = '')
# per_page: Posts displayed per page. (0 = disable pagination)
# order_by: Posts order. (Order by date descending by default)
index_generator:
  path: ''
  per_page: 10
  order_by: -date

# Category & Tag
default_category: uncategorized
category_map:
tag_map:

# Metadata elements
## https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meta
meta_generator: true

# Date / Time format
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD
time_format: HH:mm:ss
## updated_option supports 'mtime', 'date', 'empty'
updated_option: 'mtime'

# Pagination
## Set per_page to 0 to disable pagination
per_page: 10
pagination_dir: page

# Include / Exclude file(s)
## include:/exclude: options only apply to the 'source/' folder
include:
exclude:
ignore:

# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: yilia

# Deployment
## Docs: https://hexo.io/docs/one-command-deployment
# 自动部署 public 目录到博客地址，hexo d
# rm -rf .deploy_git && npm install hexo-deployer-git --save
deploy:
  type: git
  repo: git@github.com:iocd/blogs.git
  branch: master

# 标签生成
# npm i hexo-generator-json-content --save
jsonContent:
    meta: false
    pages: false
    posts:
      title: true
      date: true
      path: true
      text: false
      raw: false
      content: false
      slug: false
      updated: false
      comments: false
      link: false
      permalink: false
      excerpt: false
      categories: false
      tags: true
```



**`themes/yilia/_config.yml`** 

```yaml
# Header

menu:
  主页: /
  相册: /photos
  #随笔: /tags/随笔/

# SubNav
subnav:
  github: "https://github.com/iocd"
  #weibo: "#"
  rss: /blogs/atom.xml
  #psn: "#"
  #qq: "#"
  #weixin: "#"
  #jianshu: "#"
  #douban: "#"
  #segmentfault: "#"
  #bilibili: "#"
  #acfun: "#"
  #mail: "mailto:litten225@qq.com"
  #facebook: "#"
  #google: "#"
  #twitter: "#"
  #linkedin: "#"

rss: /blogs/atom.xml

# 是否需要修改 root 路径
# 如果您的网站存放在子目录中，例如 http://yoursite.com/blog，
# 请将您的 url 设为 http://yoursite.com/blog 并把 root 设为 /blog/。


# Content

# 文章太长，截断按钮文字
excerpt_link: more
# 文章卡片右下角常驻链接，不需要请设置为false
show_all_link: '展开全文'
# 数学公式
mathjax: false
# 是否在新窗口打开链接
open_in_new: false

# 打赏
# 打赏type设定：0-关闭打赏； 1-文章对应的md文件里有reward:true属性，才有打赏； 2-所有文章均有打赏
reward_type: 2
# 打赏wording
reward_wording: '谢谢你请我吃糖果'
# 支付宝二维码图片地址，跟你设置头像的方式一样。比如：/assets/img/alipay.jpg
# 微信二维码图片地址
alipay: /blogs/assets/img/alipay.jpg
weixin: /blogs/assets/img/weixin.jpg

# 目录
# 目录设定：0-不显示目录； 1-文章对应的md文件里有toc:true属性，才有目录； 2-所有文章均显示目录
toc: 1
# 根据自己的习惯来设置，如果你的目录标题习惯有标号，置为true即可隐藏hexo重复的序号；否则置为false
toc_hide_index: true
# 目录为空时的提示
toc_empty_wording: '目录，不存在的…'

# 是否有快速回到顶部的按钮
top: true

# Miscellaneous
baidu_analytics: ''
google_analytics: ''
favicon: /blogs/assets/img/favicon.ico

#头像
avatar: /blogs/assets/img/touxiang.png

#是否开启分享
share_jia: true

#评论：1、多说；2、网易云跟帖；3、畅言；4、Disqus；5、Gitment
#不需要使用某项，直接设置值为false，或注释掉
#具体请参考wiki：https://github.com/litten/hexo-theme-yilia/wiki/

#1、多说
duoshuo: false

#2、网易云跟帖
wangyiyun: false

#3、畅言
changyan_appid: false
changyan_conf: false

#4、Disqus 在hexo根目录的config里也有disqus_shortname字段，优先使用yilia的
disqus: false

#5、Gitment
gitment_owner: false      #你的 GitHub ID
gitment_repo: ''          #存储评论的 repo
gitment_oauth:
  client_id: ''           #client ID
  client_secret: ''       #client secret

# 样式定制 - 一般不需要修改，除非有很强的定制欲望…
style:
  # 头像上面的背景颜色
  header: '#4d4d4d'
  # 右滑板块背景
  slider: 'linear-gradient(200deg,#a0cfe4,#e8c37e)'

# slider的设置
slider:
  # 是否默认展开tags板块
  showTags: false

# 智能菜单
# 如不需要，将该对应项置为false
# 比如
#smart_menu:
#  friends: false
smart_menu:
  innerArchive: '所有文章'
  friends: '友链'
  aboutme: '关于我'

friends:
  廖雪峰: http://www.liaoxuefeng.com/
  阮一峰: http://www.ruanyifeng.com/blog/
  陈皓: http://coolshell.cn/
  闻波: http://www.cnblogs.com/webary/
  冯兆峯: http://blog.csdn.net/zffenger

aboutme: 很惭愧<br><br>只做了一点微小的工作<br>谢谢大家
```

关于路劲问题：[typora + hexo博客中插入图片](https://blog.csdn.net/qq_32623363/article/details/100524856)

设置如下

![image-20210906184554990](/blogs/assets/blogimg/yilia主题的配置使用/typora1.png)

![image-20210906184554990](/blogs/assets/blogimg/yilia主题的配置使用/typora2.png)



注意：部署有延时，hexo中有某个js访问超过21s，导致打开慢



先到这里吧。。。那天再续上





