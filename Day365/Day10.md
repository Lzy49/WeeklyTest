# 闭包应用

## Scala 偏应用函数

> Scala 偏应用函数是一种表达式，你不需要提供函数需要的所有参数，只需要提供部分，或不提供所需参数。

```JavaScript
const partial = (f, ...args) =>{
  // f 是这一层的变量
  return (...moreArgs) =>{
    // f 是外层的变量，所以这个是由闭包完成的。
    return f(...args, ...moreArgs)
  }
};
const add3 = (a, b, c) => a + b + c;
const fivePlus = partial(add3, 2, 3);
fivePlus(4) // 9
```

上面的函数中 `partial` 是个工厂函数。将 add3 缓存到 `partial` 中，返回的函数中使用了该函数以及参数。

## 科里化

> 柯里化是将一个多参数函数转换成多个单参数函数，也就是将一个 n 元函数转换成 n 个一元函数

```JavaScript
const sum = (a, b) => a + b
const curriedSum = (a) => (b) => a + b
curriedSum(40)(2) // 42.
const add2 = curriedSum(2) // (b) => 2 + b
console.log(add2(10)) // 12
console.log(add2(18)) // 20
```

例中 `curriedSum` 将 参数`a`进行了换成在返回的函数中使用了`a` 对一个多参数函数进行了拆分。

## 科里化 和 偏应用函数

> 科里化 是 偏应用函数的更为细的应用。偏应用函数 将多 参数 函数分为 部分参数函数，而科里化将多参数函数转换为单参数函数。两者都是为了解决 参数共用，利用闭包，来缓冲同类参数。
