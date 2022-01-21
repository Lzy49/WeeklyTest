# call & apply & bind

## call & apply

修改 `this` 指向，就是将函数变成某对象的方法。

#### call 实现

```JavaScript
function myCall(thisValue,...args){
  thisValue.fun = this;
  const res = thisValue.fun(...args)
  delete thisValue.fun
  return res ;
}
Function.prototype.myCall = myCall
function test(age,sex){
  console.log(`姓名：${this.name}，年纪${age}，性别${sex}`)
}
test.myCall({name:'张飞'},18,'男')
```

#### apply 实现

```JavaScript
function myApply(thisValue,args){
  thisValue.fun = this;
  const res = thisValue.fun(...args)
  delete thisValue.fun
  return res ;
}
Function.prototype.myApply = myApply
function test(age,sex){
  console.log(`姓名：${this.name}，年纪${age}，性别${sex}`)
}
test.myApply({name:'张飞'},[18,'男'])
```

## bind

`bind` 方法是将函数的上下文修改成指定值，但是没有执行。所以只需要在执行时，对 `this` 进行修改即可。
要注意的是`bind` 创建的函数还可能是一个 类，需要判断被`new`的情况。
```JavaScript
Function.prototype.myBind = function(thisValue,...args){
  const _this = this;
  return function F(){
    if(this instanceof F){
      return new _this(...args,...arguments)
    }
    return _this.call(thisValue,...args,...arguments)
  }
}
function test(age,sex){
  this.age = age;
  console.log(`姓名：${this.name}，年纪${age}，性别${sex}`)
}
const f = test.myBind({name:'张飞'},18,'男')
// f()
let b = new f()
```
