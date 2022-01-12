# 立即执行函数 IIFE

## 什么是立即执行函数 IIFE

立即执行函数就是一个马上创建，马上执行，马上销毁的函数。分为以下几步：

- 创建匿名函数
- 执行函数
- 函数执行后因为食匿名函数所以会被回收。

## 应用

### 创建临时独立作用域

立即执行函数的主要作用就是创建独立作用域。与闭包结合可以产生新的火花

```JavaScript
const sum = (function(){
  let count = 0;
  return ()=>{
    return count ++ ;
  }
})();
console.log(sum())
```

上例中`sum`是一个计数器，使用闭包封闭变量 `count` 使得其不污染全局作用域。

### 解决变量名冲突

根据作用域，就近访问变量的原则。当想要在局部使用某变量且全局已有该变量时，可以使用立即执行函数解决

```JavaScript
const $ = ()=>console.log('全局 $ 已经不是 jQuery');
$();
(function($){
  console.log('我任能被执行')
  $('body').html('')
}(jQuery))
```

上例中假设在一个 jQuery 环境中`$`已被使用，想要使用已有的 jQuery 代码可以使用立即执行函数解决变量名冲突问题。

### 使用简洁变量名

```JavaScript
const obj = {name:'张飞',info:{age:10,sex:'男'}}
(function (age){
  console.log(age)
}(obj.info.age))
```

### 循环陷阱

```JavaScript
for(var a = 0 ; a < 10 ; a++){
  (function(v){
    setTimeout(function(){
      console.log(v)
    },0)
  })(a)
}
```