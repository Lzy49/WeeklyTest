## 判断数据类型的方式有哪些

- typeof
- instanceof
- constructor
- Object.prototype.toString

### 详解

#### typeof

`typeof` 用来判断 基本值的类型：

```js
typeof 1 === 'number';
typeof 1n === 'bigint';
typeof Symbol.for('123') === 'symbol';
```

#### instanceof

`instanceof` 用来判断 引用值类型，但是不能判断基本值。

```js
[] instanceof Array;
new Date() instanceof Date;
```

#### constructor

判断值的 `constructor` 可以判断这个值的类型。但是无法判断`undefined` 和 `null`

```js
(1).constructor === Number;
'1'.constructor === String;
```

#### Object.prototype.toString

`Object.prototype.toString` 可以返回值的类型字符串，通过判断类型字符串可以判断值类型

```js
Object.prototype.toString.call(123) === '[object Number]';
Object.prototype.toString.call(undefined) === '[object Undefined]';
Object.prototype.toString.call(NaN) === '[object Number];
```

### 总结

- `typeof` 用来判断基本值类型。
- `instanceof` 用来判断 引用值类型 通过原型链来判定的。
- `constructor` 可以获取对象的继承类，通过继承类可以判断其类型。但是 `undefined` 和 `null` 无法获取
- `Object.prototype.toString` 可以获取到值转换字符串，可以用来任何值。

工作期间常用`typeof` 和 `instanceof` 。且`instanceof` 可以判断值的任何一级类型。即使是自定义的`class` 也同样适用。
