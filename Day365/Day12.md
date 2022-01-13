# 立即执行函数 + 闭包 实现类库封装。

利用函数作用域进行类库封装。类库内的变量无法污染全局，而全局可以使用类库提供的方法访问类库中的变量。

## 例

```JavaScript
var $ = (function() {
  function jQuery() {
    // Initialize
  }

  return jQuery

})()
```

## Rollup

> 在 Rollup 中 的 iife 打包模式，就会将我们的的代码打包成这种形式。

源代码

```JavaScript
// index.js
const age = 10;
export default function getAge() {
  console.log(age);
}
```

通过 rollup 打包

```shell
npx rollup index.js -f iife -n $ -o build.js
```

结果

```JavaScript
// build.js
var $ = (function () {
  'use strict';

  const age = 10;
  function getAge() {
    console.log(age);
  }

  return getAge;

})();
```
