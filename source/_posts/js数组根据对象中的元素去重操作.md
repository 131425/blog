---
title: vue/js 数组根据对象中的元素去重操作
date: 2018-08-30 11:03:28
tags: vue/js
- 数组中对象去重操作
---

举例：

```javascript
var test = [
{
    fruit: '苹果',
    eat: '早上吃'
},
{
    fruit: '香蕉',
    eat: '中午吃'
},
{
    fruit: '苹果',
    eat: '晚上吃'
}];

var hash = {};
var newTest = test.reduce(function(item, next) {
    hash[next.fruit] ? '' : hash[next.fruit] = true && item.push(next);
    return item
}, []);

console.log(JSON.stringify(newTest));
```

输出：

```
[{"fruit":"苹果","eat":"早上吃"},{"fruit":"香蕉","eat":"中午吃"}]
```