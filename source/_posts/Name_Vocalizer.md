---
title: 使用Vocalizer.js喊出自己的名字!
subtitle: Improving The UX Of Names With Vocalizer.js
date: 2017-01-03 18:14:23
categories:
- Tutorial
- Vocalizer.js
tags:
- Vocalizer.js
- Inspiration
- User Experience
banner: /gallery/implementation-of-Vocalizer-large-opt.jpg
---

#### Pronounce Names Right!
##### Improving The UX Of Names With Vocalizer.js

今天在逛smashingmagazine的时候发现了**@Atif Azam**写的一个Vocalizer的组件。
我也试着添加到自己的博客上。

##### 实现步骤如下:

##### 1. 首先，到**@Atif Azam** 的官方Github上下载Vocalizer.js组件，并引用如下：

官方Github仓库:https://github.com/atifazam/vocalizer

```javascript
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/vocalizer/1.0.0/vocalizer.min.js"></script>
```

##### 2. 添加Vocalizer标签

```html
<span class="vocalizer" data-source="auto">NAME</span>
<span class="vocalizer" data-source="/media/名字.mp3 | m4a">NAME</span>
```
在需要的位置添加此标签，span标签中对应写会喊出的名字，需要注意的是：
1. 如果data-source中写的是auto,会调用[NamesShouts](https://www.nameshouts.com) - https://www.nameshouts.com/  进行查找名字读音，可能会不太准确或者匹配错误.

此时我们已经完成了Vocalizer的功能增强.

{% asset_img Vocalizer.png myVocalizer %}

##### 3. 完整拼出自己的名字

昨天，我只是喊出一部分的名字，今天完整的制作一下自己名字的音频。

** 3.1. 搜索自己名字的音频 **

   我发现[NamesShouts](https://www.nameshouts.com) - https://www.nameshouts.com/ 还是非常好用的。在这里搜索出了自己的名字。
   直接键入自己的名字即可（目前只测试了英文）。此站点会搜索出相关的音频。

   {% asset_img myname.png myName %}

   每一个单词都会有一个mp3格式的音频，可以供下载。
   **下载方式：** 右键名字单词即可打开对应音频文件下载链接，保存即可。
   如果需要自己名字读的慢一些，可以打开“小蜗牛”的开关，则可以切换了。
   可能会有多个地区的读音可供参考。

** 3.2. 制作名字音频合并 **

由于名字的音频是两个mp3的文件，我们需要合并一下（不是自己电脑的，没有安装本地应用）。

推荐两个在线版的音频处理网站:

   http://audio-joiner.com/ - Audio Joiner --> 个人感觉非常好使. 界面清爽，功能专注，视频和音频的剪切、拼接都可以分步完成.
   他们的主站点: http://123apps.com/

此时完成了名字音频的合并，我们可以重新添加一下音频到博客了。


** 个人建议：**
  1. 使用windows的Voice Recorder自己录一个*.m4a文件，经过测试Vocalizer.js也支持*.m4a格式;
  2. 使用https://zh.forvo.com 中的读音会比较标准。
  3. 记得写出正确的相对路径即可。


** 参考资料：**
https://github.com/atifazam/vocalizer
https://www.smashingmagazine.com/2016/12/improving-ux-names-vocalizer-js/
http://atifaz.am/blog/vocalizer-help-others-pronounce-your-name-correctly.html
