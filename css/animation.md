# 动画

* transition
* transform
* animation 
* keyframes
* requestAnimationFrame


## requestAnimationFrame

用法：

```js
// 如果浏览器不支持requestAnimationFrame，用setTimeout模拟
window.requestAnimFrame = (function(){
  return  window.requestAnimationFrame       ||
          window.webkitRequestAnimationFrame ||
          window.mozRequestAnimationFrame    ||
          function( callback ){
            window.setTimeout(callback, 1000 / 60);
          };
})();


// 用法:
(function animloop(){
  requestAnimFrame(animloop);
  render();
})();
```

浏览器支持情况：

```
IE 10+
Chrome 10+
Firefox 4+
```