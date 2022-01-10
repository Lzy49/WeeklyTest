# 为什么箭头函数不能当构造函数

## 衍生问题

- 箭头函数`this`是什么
- 箭头函数与`function`有什么区别
- new 箭头函数会怎么样。

## 箭头函数与`function`的区别

- 箭头函数只有`length`和`name`，`function` 函数还有`caller`
- `function` 函数 有内部变量 `this` ,`arguments`
- 箭头函数没有`prototype`
- 箭头函数无法被`new`关键字调用，调用会报错。
- `function` 有 3 种定义方式，箭头函数只有一种。
  - 函数声明
  - 函数表达式
  - `new`

```js
function test(a, b, c) {
  console.log(this, arguments, test.caller, test.length, test.name);
}
test(1, 2, 3);
const test_ = (a, b, c) => {
  console.log(this, test_.length, test_.name);
};
test_();
```

## 箭头函数的`this`是什么。

箭头函数的`this`就是其父函数环境的`this`。属于闭包。

## 为什么箭头函数不能当构造函数

因为箭头函数没有这个功能。例如： `this` ，`caller`
