# fallback.js
> You need to instead of this file to server url

## description
1. Add this file to your app index.html
2. Use http link.
3. Just an empty file.
4. If your want to force to clean users cache and something quick things, you can use this file.

## usage
1. Download fallback.js
  ```shell
  curl https://cdn.jsdelivr.net/gh/afeiship/fallback.js/index.js > fallback.js
  ```
2. Add to your own project file
  ```html
  <!--DO NOT DELETE THIS FILE-->
  <script src="//tsscdn.finxos.com/cloud/statics/fallback.js"></script>
  <!--DO NOT DELETE THIS FILE-->
  ```

## inline solution <index.html>

```js
window.onload = function(){
  var head = document.getElementsByTagName('head')[0];
  var fbScript = document.createElement('script');
  fbScript.type = 'text/javascript';
  fbScript.async = true;
  fbScript.src = '/fallback.js?v=' + Date.now();
  fbScript.onload = function() {
    if (navigator && navigator.serviceWorker) {
      if (window.__SW_DISABLED__) {
        navigator.serviceWorker.getRegistration('/').then(function(reg) {
          reg && reg.unregister();
        });
      }
    }
  };
  head.appendChild(fbScript);
};
```
