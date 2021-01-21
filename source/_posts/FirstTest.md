---
title: 第一次的测试
date: 2021-01-21 17:34:02
tags: web
---
这边来记录一下从零开始的搭建过程
主要的还是基于github的github.io
对于会的人来说应该很快就好了，说起来确实也就几分钟的时间在敲代码上，但是花了蛮久时间研究问题的。
主要的步骤是这样的，先在树莓派上搭建了Node.js+Hexo的框架，然后在去找了个域名，也就是ironrao.xyz。
emmm说起来好像我的github的usr name还是iron-rao，不知道能不能改掉。这个"-"好麻烦。之后再看。
然后现在基本的框架搭好了，但是插件还没装。之后几天再研究一下。

这里有个网页，之后还有好多东西要参考一下：
源自知乎
https://zhuanlan.zhihu.com/p/35668237
orz 看了一下这个确实好厉害，这个整个的主题就和这种原来的Next的主题不一样，太厉害了orz。
有评论区，有目录，有水印，还有网易云的BGM。

还有字数统计什么的常用工具，也可以放照片，太心动了，明天就换它看看。

---


然后在晚上看了看这个界面，emmm，大红大紫的感觉不好看orz。
去github上找了，archer&ayer&catus。试了试这三个。感觉都不是自己想要的。但是我还觉得catus的风格还挺好的，就是不知道为什么在编译的时候报错了，也不知道报错怎么解决。（还截了个屏，之后放上去）。在baidu bug的时候正好遇到了这个(网站)https://www.jianshu.com/p/9f0e90cc32c2
里面啥都有，教我怎么配置Next。还有这个
https://io-oi.me/tech/hexo-next-optimization/
于是乎换回了Next的theme之后再瞅瞅。

有件很有意思的bug是啊，就是在_config.yml里第一段Site中的laguage写了en&cn, 然后网页在远端的格式就崩了，在本地还是好好的orz。调回en就好了。

而且在root/scaffolds的post.md文件里可以定义每次的模版，下次就不用一直写了。hexo new post name是新发布一个，就和发布说说一样。hexo new draft name就是新建个草稿，不会发出去的。

---
2021.01.21
来更新一下，昨天是在树莓派上搭建环境的，跟着[这个](https://zhuanlan.zhihu.com/p/108550672)教程。然后今天想着在windows上也搭个环境，以为挺快的。好家伙，花了我三个小时。

来记一下坑，
前面的安装就不提了，去nodejs上找一下对应版本的安装。
然后建个文件夹放blog的东西，之后再
```shell
hexo init
```
然后
```shell
npm install hexo-deployer-git -save
```
就遇到了这个问题orz
```shell
-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*

  Verion 9 of Highlight.js has reached EOL.  It will no longer
  be supported or receive security updates in the future.
  Please upgrade to version 10 or encourage your indirect
  dependencies to do so.

  For more info:

  https://github.com/highlightjs/highlight.js/issues/2877
  https://github.com/highlightjs/highlight.js/blob/master/VERSION_10_UPGRADE.md

-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*
+ hexo-deployer-git@2.1.0
```
说的是这个Highlight不支持V9版本了，叫我升级。然后我研究了半天它给的链接。发现没啥用，只能手动升级。最后还是打算先放着，试试再说。

然后
```shell
git init && git remote add origin https://github.com/xxx/xxx.github.io.git
```
改了改_config.yml的文件，然后测了下，通了。
这个报错也emmmmm，太迷惑了。

之后就打算写了两个脚本一键刷新和部署。
然后发现windows的cmd不可以直接`hexo `操作......
然后改用bat文件打开git bash，去用git bash 操作一下，
```bat
@REM Publish.bat
start C:\"Program Files"\Git\git-bash.exe -c "hexo clean && hexo g && cp CNAME public && hexo d"
```

还想尝试一下坚果云能不能同步，发现不太行。因为坚果云的文件夹是中文的，它找不到这个文件夹。而且换成英文的话，它是xxx xxx的形式，中间的空格会被识别错误orz。（之前在ROS的时候也遇到过）。
所以还是换Github或者Gitee同步一下叭。