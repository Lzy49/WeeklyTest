# 为什么一定要有块级作用域

## 变量提升

js 在变量声明时，会将比申明语句 根据其关键字 提升到其所在的作用域的最前面。且 `let` 和 `const` 都有 TDZ （假定死区）而`var` 变量没有假定死区。

```JavaScript
// let 被提升且，它有 TDZ
function test1(){
  console.log(a) //ReferenceError: Cannot access 'a' before initialization
  let a = 10;
}
var a = 10
function test2(){
  console.log(a) // undefned , 下面的 a 被提升到函数作用域，且没有假定死区
  if(true){
   var a = 20
  }
}
```

## 为什么要增加 块级作用域

因为`var` 定义的变量没有块级作用域的,会擅自修改了执行的逻辑。让开发人员看起来不直观：

### 问题 1 内层变量会覆盖外层变量

```JavaScript
var a = 10
function test2(){
  console.log(a) // undefned
  if(true){
   var a = 20
  }
}
```

在上例中，想要的结果应该是 a = 10 的结果，但打印的结果是 `undefned`。但如果使用 `let` 定义变量将不会出现这种问题。

### 问题 2 本应销毁的变量没有被销毁

```JavaScript
for(var i = 0 ; i < 10;i++){
  var b = i;
  console.log(b)
}
console.log('外层打印',b)
```

在上例中，`b` 在 `for` 循环中定义，直观理解是 `b` 在循环中使用，但因为 `var` 没有作用域提升。其被提升到 `for` 以外。
