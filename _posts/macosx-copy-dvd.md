---
Title: MAC OSX上用免费软件复制正版DVD
layout: post
Date: 2013-06-07
Category: 苹果
Tags: OSX, Apple, DVD, MAC
---
以前写过一篇关于复制正版DVD的文章, 换了苹果机以后那些工具都用不上了, 前天正好需要帮朋友复制一张买来的正版的曹秀美音乐会的DVD, 在网上找了一下没有什么好用又免费的一条龙服务式的软件可以在OSX上干这个, 最后想了个办法, 总结了一套工具, 顺手发篇博客做备忘.

基本的流程是用Fairmount+libdvdcss把正版DVD破解以后以U盘形式挂到Finder里, 然后用命令行里的hdiutil工具把整个DVD复制到一个iso映象文件放到桌面上, 再用OSX自带的Disk Utility工具把iso映象文件刻录到空DVD上.

所需工具:

[libdvdcss.pkg](http://download.videolan.org/pub/videolan/libdvdcss/1.2.12/macosx/libdvdcss.pkg) – 用来破解正版DVD (目前Mac OSX上可用版本是1.2.12, 如果有更新版本可以[去这找](http://download.videolan.org/pub/videolan/libdvdcss/))

[Fairmount](https://github.com/downloads/pmetzger/Fairmount/Fairmount-1.1.3.dmg) – 可以在Mac OSX上将正版DVD通过libdvdcss的破解像U盘一样mount起来

hdiutil – Mac OSX 自带命令行工具, 想详细了解的可以看[这里](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man1/hdiutil.1.html)

Disk Utility – Mac OSX 自带的工具, 我们用它来刻录新DVD, 想详细了解的看[这里](http://mac.tutsplus.com/tutorials/os-x/whatisdiskutillity/)

步骤:

1. 用上面提供的链接下载libdvdcss.pkg和Fairmount并安装
2. 插入需要复制的DVD并打开Fairmount, 双击它找到的你刚插入的DVD
3. Fairmount会开始读取并mount, 完成以后你会看到这张DVD的内容已经像U盘一样出现在Finder里了.
4. 打开Mac OSX自带的命令行工具(Terminal)
5. 输入命令后回车: hdiutil makehybrid -iso -o ~/Desktop/[这里插入一个你随便起的文件名].iso /Volumes/[这里插入你在Finder里看到的你的DVD的名字] -udf   (比如我起的文件名是SUMIJO_RECITAL, 那张DVD在Finder里的名字是UNTITLED_DISC, 那么我输入的命令就是 hdiutil makehybrid -iso -o ~/Desktop/SUMIJO_RECITAL.iso /Volumes/UNTITLED_DISC -udf)
6. 这时候你会发现桌面上出现了你刚刚命名的iso文件, 命令行里会显示正在创建映像, 等到命令行再次回到$提示符以后, 映像就创建完毕了 (如果DVD比较大, 那大概要等比较久, 视你电脑和光驱的情况而定)
7. 映像创建完毕以后, 可以把正版DVD拿出来了, 再放一张空白DVD进去
8. 右键单击你桌面上创建好的iso文件, 选用Disk Utility打开, 点击刻录(Burn), 按提示选择你的iso和空白光盘所在光驱按提示确认刻录就可以了.
喜欢命令行下操作的, 刻录应该也可以用hdiutil完成, 我是懒得弄了, 直接用Disk Utility鼠标点点. =)
