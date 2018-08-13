---
title: js字符串安逗号、回车分割
date: 2018-08-13 11:07:40
tags: 
- JS textarea
- 字符串按逗号和回车分隔
---

> 工作中有需求：用户输入时1、可按逗号隔开输入 2、也可以用换行分割输入 最终就提交一个数组

```javascript
var str = 指定字符串值;
var arr = str.split(/[\n,]/g)
console.log(arr);
```

