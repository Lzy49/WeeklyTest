# 如何利用闭包制造惰性函数

## 惰性函数

惰性函数表示函数执行的分支只会在函数第一次调用的时候执行，在第一次调用过程中，该函数会被覆盖为另一个按照合适方式执行的函数，这样任何对原函数的调用就不用再经过执行的分支了。

### 例

```js
function createXHR() {
  var xhr = null;
  if (typeof XMLHttpRequest != 'undefined') {
    xhr = new XMLHttpRequest();
    createXHR = function () {
      return new XMLHttpRequest();
    };
  } else {
    try {
      xhr = new ActiveXObject('Msxml2.XMLHTTP');
      createXHR = function () {
        return new ActiveXObject('Msxml2.XMLHTTP');
      };
    } catch (e) {
      try {
        xhr = new ActiveXObject('Microsoft.XMLHTTP');
        createXHR = function () {
          return new ActiveXObject('Microsoft.XMLHTTP');
        };
      } catch (e) {
        createXHR = function () {
          return null;
          x;
        };
      }
    }
  }
  return xhr;
}
```

## 闭包制造惰性函数

```js
var square = (function () {
  let cache = {};
  return function (n) {
    // 此处有缓存
    if (!cache[n]) {
      cache[n] = n * n;
    }
    return cache[n];
  };
})();
```
