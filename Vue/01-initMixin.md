```js
(function(global, factory) {
  global.Vue = factory();
})(this, function() {
  function initMixin(Vue) {
    Vue.prototype._init = function(options) {

    };
  };


  // Vue() this === window
  function Vue(options) {
    if (!(this instanceof Vue)) {
      console.error('Vue is a constructor');
    }
    this._init(options);
  };

  initMixin(Vue);
  return Vue;
})
```
