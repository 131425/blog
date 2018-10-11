---
layout: 微信小程序
title: navigateTo跳转失灵
date: 2018-10-11 15:06:32
tags:
- 微信小程序
- navigateTo跳转失灵
---

1.`wx.navigateTo({url}) 不会销毁当前页面，仅仅是将其hide，使用wx.navigateBack可以返回到原页面。`

2.`wx.redirectTo({url}) 销毁当前页面，跳转到应用内的其他页面。`

3.`wx.switchTab({url}) 用于跳转到tabBar。` 检查你要跳转的位置是否位于`TabBar`中，如果是的话，要使用`wx.switchTab `来跳转界面 

