# Vue

```js
var vm = new Vue({
    el: '#id',
    data: {
        message: 'Hello Vue'
    }
})
```


```
v-if
v-for
v-bind
v-model
v-on
v-on:click
```

### v-bind 缩写
```html
<!-- 完整语法 -->
<a v-bind:href="url">...</a>

<!-- 缩写 -->
<a :href="url">...</a>
```

### v-on 缩写
```html
<!-- 完整语法 -->
<a v-on:click="doSomething">...</a>

<!-- 缩写 -->
<a @click="doSomething">...</a>
```

### methods vs computed
方法属性每次都会执行
计算属性是基于它们的响应式依赖进行缓存的,只在相关响应式依赖发生改变时它们才会重新求值(执行)