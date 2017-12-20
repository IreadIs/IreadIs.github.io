---
layout: post
title: "初次接触小程序遇到的一些问题"
date: 2016-06-20 
description: "小程序的使用"
tag: 小程序

---

因为小程序的出现，自己在学习的过程中遇到了一些问题，然后我做了总结，如果你也是在研究小程序的初步阶段，不妨看看，应该会有些帮助。

* 1、小程序之中布局是不是跟html相同？
* 2、如何将小程序的js引用到自己的页面？
* 3、怎样将后台获取到的数据展示到前台？

### 小程序的基本知识
	小程序的视图容器包含`view`、`scroll-view`、`swiper`、`movable-area`、`cover-view`标签，最后两个标签是我最近才补充上的。在开发小程序的过程中最常用的标签就是`view`。下面是`view`标签的用法：

> <view class="section">
>  <view class="section__title">flex-direction: row</view>
>  <view class="flex-wrp" style="flex-direction:row;">
>    <view class="flex-item bc_green">1</view>
>    <view class="flex-item bc_red">2</view>
>    <view class="flex-item bc_blue">3</view>
>  </view>
> </view>
> <view class="section">
>  <view class="section__title">flex-direction: column</view>
>  <view class="flex-wrp" style="height: 300px;flex-direction:column;">
>    <view class="flex-item bc_green">1</view>
>    <view class="flex-item bc_red">2</view>
>    <view class="flex-item bc_blue">3</view>
>  </view>
> </view>

	效果图如下：
<img src="/images/posts/codeless/calendar.png" height="300" width="600"> 
	在上面的示例可以看出小程序的布局跟传统的html布局是不一样的，
* 1、开发语言不同
	> 小程序自己开发了一套WXML标签语言和WXSS样式语言，并非直接使用标准的HTML5+css3。而且我们也发现他
* 2、组件封装不同
	> 小程序独立出来了很多原生APP的组件，在HTML需要模拟才能实现的功能，小程序里可以直接调用组件
	> 以上信息解决了咱们在前文提到的第一个问题