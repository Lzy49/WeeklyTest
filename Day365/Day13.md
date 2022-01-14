# 闭包应用 - 构建器打包 webpack

webpack 的模块打包 是将多文件整合到一个文件或几个文件中。在打包的过程中执行了以下步骤：

- 根据 入口文件，各模块引用，将所有模块整合到一起。
- 创建 模块调用器
- 在模块中使用模块调用器调用其他模块。
- 将入口函数设置为自执行函数。与其他模块作用域做隔离。

经过以上的处理，入口函数调用模块使用了模块调用器调用了他自己访问不了的东西。这也是闭包的一种应用。

## 例

```JavaScript
// a.js
const name = 'Justin'
module.exports = 'my name is ' + name
```

```Javascript
//index.js
const a = require('./a.js');
console.log(a);
```

打包后

```JavaScript
(() => {
  var r = {
      85: (r) => {
        r.exports = 'my name is Justin';
      }
    },
    o = {};
  function t(e) {
    var s = o[e];
    if (void 0 !== s) return s.exports;
    var n = (o[e] = { exports: {} });
    // 此处 的 r 其实是外部的 r 也属于闭包
    return r[e](n, n.exports, t), n.exports;
  }
  (() => {
    // 此处调用了 t 函数而t 函数是外部值，这也是一种 闭包的使用。
    const r = t(85);
    console.log(r);
  })();
})();

```
