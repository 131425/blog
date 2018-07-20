---
layout: posts
title: vue-axios的同步问题
date: 2018-07-17 10:16:33
tags: 
- Vue 
- axios
---



> 在vue项目里面，需要循环发送ajax请求，出现的问题就是循环结束，第一次服务器还没返回，导致数据处理错误，需要使用同步请求 



```javascript
methods:{
   	getDeviceType (callback) {
        // 方法里面的事情做完了,或者你觉得该调用的时候
        // 如果有参数的话,通过 callback 传过去
        callback && callback(param)	
        //比如： 
        //调用接口得到的key 并赋值  this.key = res.data.data.key; 要在其他地方调用，就需要用到回调 把参数带过去
        //callback && callback(this.key)
    },
    handleEdit () {
        this.getDeviceType(() => {
            // 这里接收 getDeviceType 回调传过来的参数 param
            console.log(this.key);
        })
    }
 }
```

