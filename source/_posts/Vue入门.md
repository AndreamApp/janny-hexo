---
title: Vue入门
date: 2018-09-13
tags: ['Vue']
---

> 有基础的HTML+CSS+JS知识就阔以搞起了

## Hello Vue —— 声明式渲染

```js
<html>

<div id="app">
    Hello Vue, My name is xxx.
</div>

</html>
```

这是一个最简单的网页了，略去了网页其他不必要的细节，我打算据此引入Vue的使用。

```js
<html>

<div id="app">
    Hello Vue, My name is {{ name }}.
</div>

<script src="https://unpkg.com/vue"></script>
<script>
    var obj = new Vue({
        el: '#app',
        data: {
            name: 'Biao'
        }
    })
</script>

</html>
```

这个代码很好懂，目的是用js动态填充`文档元素`里的{{name}}模板。

从面向对象的角度来理解Vue的工作原理，那么这段代码最关键的一个词就是：new。就好像一首诗的“诗眼”一样。

通过new创建了一个Vue对象实例，而这个对象将`文档元素`和`数据`联系在了一起。注意，Vue并非是简单地“模板替换”，在console里输入obj.name='Tony'，你会发现文档`响应式`的改变了，这意味着Vue对象`obj`维护着元素`#app`和其他Vue属性`data`之间的关系。

再提一问：Vue为什么要这样维护？比用DOM维护有什么好处？答案是DOM将结点元素视为一个对象，而Vue将有结构的数据视为一个对象。用Vue修改name只需要obj.name='Tony'即可，而用DOM要先document.getElementById('app')再修改innerHTML。

如果再深究一步：Vue怎样实现这样的维护？那所有的秘密都藏在`<script src="https://unpkg.com/vue"></script>`这一行里了，恐怕只有阅读了源码才能清楚。

## 条件与循环

```html
<div id="app">
    <p v-if="seen">现在你看到我了</p>
    <li v-for="todo in todos">
      {{ todo.text }}
    </li>
</div>
var obj = new Vue({
  el: '#app',
  data: {
    seen: true,
    todos: [
      { text: '学习 JavaScript' },
      { text: '学习 Vue' },
      { text: '整个牛项目' }
    ]
  }
})
```

## 速查手册

```
v-if="seen"
v-for="todo in todos"
v-on:click="reverseMessage"    // 事件绑定
v-model="message"   // 表单数据绑定
var obj = new Vue({
    el: '#app',
    data: {
        name: 'Biao',
        seen: true,
        todo: []
    },
    methods: {
        reverseMessage: function () {
            this.message = this.message.split('').reverse().join('')
        }
    }
})
```

