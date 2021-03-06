# this 指向的多种形式

## 上下文

上下文和作用域是两个东西。

- 作用域是在第一次运行时就决定的，他决定了变量的层级，取值的顺序。
- 上下文是在运行时决定的，它决定了函数归属谁。谁调用了函数。`this` 的值与 上下文有关，与作用域无关。

## this 值确定

### 常规情况

- 当函数直接执行时，`this` 指向 `global`，（严格模式 指向 `undefined`)
- 当函数是某对象的一个属性，以属性形式调用时，`this` 指向调用它的对象。
- 当函数被`call`,`apply`调用，`bind` 绑定`this`。其`this`值指向函数传入`this`
- 当函数是一个构造函数被调用时，其他 `this` 指向 `new` 左侧值。

### 其他特殊情况

- 箭头函数没有自己的`this`所以，其 `this` 等于其父级`this`。
- `addEventListener`添加事件时会将函数中的`this`更改为绑定事件对象。

## 简写

`this` 的确定由 执行上下文决定。

- 函数直接执行时，`this`指向`global`严格模式下指向`undefined`。
- 函数被当作对象方法调用时，`this`指向调用它的对象。
- 函数被`call`,`apply`,`bind`调用时，`this`为其绑定值。
- 函数被 `new` 调用时，`this` 指向 `new` 左侧变量。
- 箭头函数没有`this` ,其`this`是闭包其父级`this`。
- 一些特殊的方法可能会修改`this`值，如`vue`,`addEventListener`
