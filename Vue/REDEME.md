
## 配置的覆盖

- 禁止给config对象整体赋值，只可以通过键值对的方式来赋值
- 通过代理的方式返回另一个对象, 保护内在对象，

```js
var Vue = {}
var configDef = {}
var config = {
  merge: true
}

configDef.get = function() {
  return config;
}
configDef.set = function() {
  console.warn('warn, do not set config');
}


Object.defineProperty(Vue, 'config', configDef)

console.log(Vue.config); // {merge: true }
setTimeout(() => {
  Vue.config.title = 'title';
  Vue.config = {a:1}; // warn:do not set config
  console.log(Vue.config); // {merge: true, title: title }
}, 1000);
```

