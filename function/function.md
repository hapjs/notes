# function

记录一些可以复用的函数或代码片段，支持在ES5+的环境中运行。

### 客户端os检测
```js
// 判断客户端操作系统是win还是mac还是linux
// 判断客户端是否移动设备
// 判断客户端是否微信

var os = (function(p, ua){
    var win = !!p.match(/^Win/),
        mac = !!p.match(/^Mac/),
        linux = p === 'X11' || !!p.match(/^Linux/),
        mobile = !(win || mac || linux),
        wechat = !!ua.match(/micromessenger/);
    
    return {
        win: win,
        mac: mac,
        linux: linux,
        mobile: mobile,
        wechat: wechat
    };
}(
    navigator.platform, 
    navigator.userAgent.toLowerCase()
));
```

### 扩展函数，支持深度拷贝
```js
/**
 * @param  {boolean} deep 是否深度拷贝，可选参数
 * @param   {object} dest 目标对象
 * @param   {object} src  源对象
 * @param   {object} srcN 源对象N
 * @return  {object} 返回修改后的目标对象
 */
function extend() {
    var args = arguments, deep = false, dest;
    if (typeof args[0] === 'boolean') {
        deep = Array.prototype.shift.call(args);
    };
    dest = Array.prototype.shift.call(args);
    dest && Array.prototype.forEach.call(args, function (src) {
        src && Object.keys(src).forEach(function (key) {
            if (deep && typeof src[key] === 'object' && typeof dest[key] === 'object') {
                extend(true, dest[key], src[key]);
            } else if (typeof src[key] !== 'undefined') {
                dest[key] = src[key];
            };
        });
    });
    return dest;
};
```

### 遍历对象或数组
```js
/**
 * @param {object|array} obj 遍历的对象
 * @param {function}     fn  处理函数，将会接收到2个参数：value, key
 */
function each(obj, fn){
    
    if(typeof fn !== 'function') return;
    
    if(Array.isArray(obj)){
        Array.prototype.forEach.call(obj, fn);
    }else if(typeof obj === 'object'){
        Object.keys(obj).forEach(function(key){
            fn(obj[key], key);
        });
    };
}
```

### 微型模板函数

使用：`sub('hello {name}!', { name: 'world' });` ==> `hello world!`

```js
var sub = function(s, o) {
    var SUBREGEX = /\{\s*([^|}]+?)\s*(?:\|([^}]*))?\s*\}/g; 
    return s.replace ? s.replace(SUBREGEX, function (match, key) {
        return undef(o[key]) ? match : o[key];
    }) : s;
};
```

### 命名空间函数

```js
/** 查询或创建命名空间并给它赋值
  @param {Object} root 根对象（必须）
  @param {String} path 命名空间路径（必须）
  @param {Object} value 对命名空间赋的值（必须）
  @param {Boolean} dontCreate 是否禁止创建路径， 默认为true
*/
export function namespace (root, path, value) {
    if (!path) return root

    var name
    var parent
    var obj = root || window
    var needSetValue = arguments.length >= 3
    
    path = path.split('.')
    
    // get value
    for (var i = 0; i < path.length; i++) {
        name = path[i]
        if (name) {
            // if don't set value 
            if (!(name in obj) && !needSetValue) return undefined
            parent = obj
            obj = parent[name] = parent[name] || ((i < path.length - 1) ? {} : undefined)
        }
    }

    // set value
    if (needSetValue && name) {
        obj = parent[name] = value
    }

    return obj
}
```

### 判断是否数字
```js
function isNumber(s){
    return typeof s === 'number' || !!(s && !isNaN(s));
};
```

### 判断是否具有指定class
```js
function hasClass(node, cls, context){

    // 同时支持Node和选择器
    if(typeof node === 'string'){
        node = (context || document).querySelector(node); 
    };
    
    if(!node || typeof cls !== 'string') return false;
    
    return !!node.className.match(new RegExp('\\b' + cls + '\\b'));
}
```

### addClass
```js
function addClass(node, cls){
    if(typeof node === 'string') node = document.querySelector(node);

    if(!node || (typeof node.className !== 'string')) return;

    if(node.className.indexOf(cls) === -1) {
        node.className += ' ' + cls;
    }
}
```

### removeClass
```js
function removeClass(node, cls){
    if(typeof node === 'string') node = document.querySelector(node);

    if(!node || (typeof node.className !== 'string')) return;

    if(node.className.indexOf(cls) !== -1) {
        node.className = node.className.replace(cls, '');
    }
}
```

### 判断是否奇数（不包含负数）
```js
function isOdd (n) {
    return ((n + '').match(/^\d*(\d)(\.0+)?$/) || [])[1] % 2 === 1
}
```

### 判断是否偶数（不包含负数）
```js
function isEven (n) {
    return ((n + '').match(/^\d*(\d)(\.0+)?$/) || [])[1] % 2 === 0
}
```

### 取url参数
```js
function getParams (url) {
    var params = {};
    (url.split('?')[1] || '').split('&').forEach(function (s) {
        s = s.split('=');
        if (s[0]) params[s[0]] = s[1] || '';
    })
    return params;
}
```
