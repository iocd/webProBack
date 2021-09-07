---
layout: post
title: "yilia 主题的配置使用"
date: 2021-9-6 14:56
comments: true
toc: true
reward: true
tags: 
	- web
	- 博客
---

## yilia 主题的配置使用

主要为了在 github page 发布静态网页的博客。写的是md笔记，用hexo编译后就是静态网页了，yilia 之类的主题是可选使用



#### 一、先安装软件

注意：nodejs 的16.8.0版本在win11上，`npm install` 会报错，建议先安装低一点的版本尝试。

| 下载                                 | 安装                                                         | 备注                                     |
| ------------------------------------ | ------------------------------------------------------------ | ---------------------------------------- |
| [Python](https://www.python.org/)    | [在windows下安装Python(Python入门教程)](https://my.oschina.net/u/3704591/blog/4566022) | nodejs依赖python                         |
| [nodejs](http://nodejs.cn/download/) | [npm安装教程](https://www.cnblogs.com/lgx5/p/10732016.html)  | npm依赖于nodejs。`npm install`能使用即可 |
|                                      |                                                              |                                          |



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

![image-20210906184554990](../assets/blogimg/image-20210906184554990.png)

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



**`themes/yilia/_config.yml`** 

```yaml
# Header
# 不需要使用某项，直接设置值为false，或注释掉

menu:
  主页: /
  相册: /photos

# SubNav
subnav:
  github: "https://github.com/iocd"
  #weibo: "#"
  rss: /atom.xml
  #psn: "#"
  #zhihu: "#"
  #douban: "#"
  #segmentfault: "#"
  #bilibili: "#"
  #acfun: "#"
  #mail: "mailto:1234@qq.com"
  #facebook: "#"
  #google: "#"
  #twitter: "#"
  #linkedin: "#"

rss: /atom.xml

# 是否需要修改 root 路径
# 如果您的网站存放在子目录中，例如 http://yoursite.com/blog，
# 请将您的 url 设为 http://yoursite.com/blog 并把 root 设为 /blog/。
root: 

# Content
excerpt_link: 'more'
show_all_link: '展开全文'
fancybox: true
mathjax: false

# 打赏
# 打赏type设定：0-关闭打赏； 1-文章对应的md文件里有reward:true属性，才有打赏； 2-所有文章均有打赏
reward_type: 1
reward_wording: '谢谢你请我吃糖果'
alipay: /assets/img/alipay.jpg
weixin: /assets/img/weixin.jpg

# 目录
# 目录设定：0-不显示目录； 1-文章对应的md文件里有toc:true属性，才有目录； 2-所有文章均显示目录
toc: 1
# 根据自己的习惯来设置，如果你的目录标题习惯有标号，置为true即可隐藏hexo重复的序号；否则置为false
toc_hide_index: true
# 目录为空时的提示
toc_empty_wording: '目录，不存在的…'

# 是否有快速回到顶部的按钮
top: true

# 是否在新窗口打开链接
open_in_new: true

# Miscellaneous
baidu_analytics: 'a30844fa2bcbce0a9e001fe06cefeddf'
google_analytics: false
favicon: ../assets/img/favicon.ico

#你的头像url
avatar: ../assets/img/touxiang.png

#是否开启分享
share_jia: true

mobile:
  social: true

#评论：1、多说；2、网易云跟帖；3、畅言；4、Disqus 不需要使用某项，直接设置值为false，或注释掉
#请参考wiki：

#1、多说
#duoshuo: "litten-hexo"

#2、网易云跟帖
#wangyiyun: '2dba06fbf8d24c13915ea6c6aa7183b1'

#3、畅言
changyan_appid: 'cysX3aGWt'
changyan_conf: 'prod_1dcda447175aada96edcdb7e412338fa'

#4、Disqus 在hexo根目录的config里也有disqus_shortname字段，优先使用yilia的
disqus: false

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

# 如不需要，将该项置为false
# 比如
#smart_menu:
#  friends: false
smart_menu:
  innerArchive: '所有文章'
  friends: '友情链接'
  aboutme: '关于我'

friends:
  廖雪峰: http://www.liaoxuefeng.com/
  阮一峰: http://www.ruanyifeng.com/blog/
  陈皓: http://coolshell.cn/
  闻波: http://www.cnblogs.com/webary/
  冯兆峯: http://blog.csdn.net/zffenger


aboutme: 红叶，<br>毕业于华科，就职于鹅厂<br><br>热爱大海与冷笑话，<br/>目前是一枚前端<br/><br/>胆小认生，不易相处，<br>年轻无为，卖马为生。
```



测试：

下面这张是站内的图（相对路径）

![btb](../assets/blogimg/btb.jpg)



下面这张是网上的图（外链）

![img](https://www.baidu.com/img/flexible/logo/pc/result.png)



先到这里吧。。。那天再续上
