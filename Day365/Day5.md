# new 关键字执行了哪些操作

## 注意

- 函数返回值会影响 `new` 关键字的赋值
  - 返回 引用值 ，则 `new` 将该引用值赋值给 `target`
  - 返回 基本值 ，则 `new` 将 `this` 赋值 给 `target`

## 理解

new 关键字做了以下事：

- 创建一个对象。
- 执行函数一次，且传入 `this` 值
- 判断函数返回值
  - 返回是对象：返回一个对象
  - 返回值非对象：返回`this`并将函数的`prototype`赋值给对象的`__proto__`

## 实现

```js
function User(name, age) {
  this.name = name;
  this.age = age;
  return 1;
}
const createTarget = (Fun, ...args) => {
  let o = {}; // 创建一个对象。
  let res = Fun.apply(o, args);
  typeof res === 'object' ? (o = res) : (o.__proto__ = Fun.prototype);
  return o;
};
let b = createTarget(User, '张二狗', 19);
```
