## 数字超过最大限制的如何处理?

### 如何判断一个值是否超出限制

```js
Number.isSafeInteger;
```

### 解决方案

#### 使用 JavaScript 新数据类型 `BigInt`

- 优点
  - 不需要引入任何库
  - 与 JavaScript 提供的 运算符 兼容
- 缺点
  - 兼容性
  - 不能与 `Number` 类型加减
  - 有新的 API 学习有成本

### 使用第三方库

- BigInt
- bigDecimal
- json-bigint

原理：`高精度计算`就是将一个很大的数字转换为一个数组，分存为多个数字，当进行运算时，会对每一位进行运算。
