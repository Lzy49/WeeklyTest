# React 事件 this 值为什么正确。

在 `React` 内部 JSX -> 虚拟 Dom -> render 函数 的过程中 事件绑定是利用`addEventListener` 绑定的。为了不让 `addEventListener` 破坏函数中的`this` 绑定前为其嵌套了一层箭头函数。事件利用`apply` 执行，`this` 值指向发生变化。

## 解决

### bind 绑定

- 在定义 事件时候利用 `bind` 绑定。而`addEventListener` 无法破坏 函数 `this` 。 `this` 就是我们绑定的值。
- 一般情况在`constructor` 中为函数绑定。不推荐在`render` 中绑定。因为`render` 会在每一次修改数据时执行。

### 箭头函数 闭包

- 将所有被绑定函数定义为箭头函数，其 this 值是其父级`this`
