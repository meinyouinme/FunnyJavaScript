### 字符串循环的两种方法比较

方法一：for循环
```javascript
String.prototype.times=function(n){
    var str='';
    for(var i=0;i<n;i++){
        str+=this;
    }
    return str;
}
//测试
averageTime(function(){
   '我是字符串'.times(100000);
})//函数运行1000次平均用时：8.843 毫秒.
```

方法2：数组方法
```javascript
String.prototype.times=function(n){
    return new Array(n+1).join(this)
}
averageTime(function(){
   '我是字符串'.times(100000);
})//函数运行1000次平均用时：2.118 毫秒.
```

测试函数：
```javascript
function averageTime(fn){//计算函数执行的平均时间，1000次
    console.log('开始运行函数.');
    var time=0;
    for(var i=0;i<1000;i++){
        var start=+new Date();
        fn();
        time+=+new Date()-start;
    }
    console.log('运行结束.');
    console.log('函数运行1000次平均用时：'+time/1000+' 毫秒.');
}
```