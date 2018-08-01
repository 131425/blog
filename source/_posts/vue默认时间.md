---
layout: posts
title: vue默认时间
date: 2018-07-23 15:15:15
tags:
- vue
- ElementUI
- DateTimePicker 日期时间选择器 默认时间
---

> 项目中用到 ElementUI 里的 DateTimePicker 日期时间选择器 默认时间,我列举的只是最笨的方法，大家也可以利用插件（比如：date_fns  ）转变格式来显示默认时间，以下仅作参考喔~

```javascript
<el-date-picker v-model="com_input_date" type="datetimerange"></el-date-picker>
```

> 在data中设置默认时间

```javascript
//this.getData(-7) -7指的是当前时间的前七天 可以自行填写
com_input_date: [this.getDate(-7),new Date()]
```

> 在方法中写入

```javascript
getDate(n){
    var ss = 24*60*60*1000; //一天的毫秒数86400
    var timestamp = new Date().getTime(); //获取当前时间戳
    var date1 = new Date( ss*n+timestamp ) //加上n天的国际标准日期
    var newTime = date1.toLocaleString(); //把日期转换成2018/6/4 下午10:45:19 格式
    var arr = newTime.split(" "); //把2018/6/4提取出来
    var arr2 = arr[0].split('/'); //把年月日数字单独提出来
    return arr2[0]+'-'+arr2[1]+'-'+arr2[2]+' '+'00:00:00'; //拼接成我们需要的格式返回
},
//时间格式化函数，此处仅针对yyyy-MM-dd hh:mm:ss 的格式进行格式化
dateFormat:function(time) {
   var date=new Date(time);
   var year=date.getFullYear();
   var month= date.getMonth()+1<10 ? "0"+(date.getMonth()+1) : date.getMonth()+1;
   var day=date.getDate()<10 ? "0"+date.getDate() : date.getDate();
   var hours=date.getHours()<10 ? "0"+date.getHours() : date.getHours();
   var minutes=date.getMinutes()<10 ? "0"+date.getMinutes() : date.getMinutes();
   var seconds=date.getSeconds()<10 ? "0"+date.getSeconds() : date.getSeconds();
   // 拼接
   return year+"-"+month+"-"+day+" "+hours+":"+minutes+":"+seconds;
},
```

