---
title: Vue基础
date: 2018-09-13
tags:
---

ViewModel 使用Vue实例联系起HTML元素(View)和data(Model)
响应式 当data变化后会立即同步变化View
组件 所有视图可以视为以Vue实例为根的组件树，可以嵌套层叠，通过CSS控制布局和样式。封装为组件可提高抽象层次，方便复用

## 模板语法

```
{{ rawHtml }}
<span v-html="rawHtml"></span>
v-bind:id="dynamicId"
v-bind:disabled="isButtonDisabled"
v-bind:id="'list-' + id"
v-if="seen"
v-on:click="doSomething"

v-bind:href="url"  缩写为  :href="url"
v-on:click="doSomething"  缩写为  @click="doSomething"
```

## 计算属性

```
// {{ message.split('').reverse().join('') }}
{{ reversedMessage }}
var vm = new Vue({
  el: '#example',
  data: {
    message: 'Hello'
  },
  computed: {
    // 计算属性的 getter
    reversedMessage: function () {
      // `this` 指向 vm 实例
      return this.message.split('').reverse().join('')
    }
  }
})
```

计算属性和函数区别：计算属性是基于它们的依赖进行缓存的。只在相关依赖发生改变时它们才会重新求值。这就意味着只要 message 还没有发生改变，多次访问 reversedMessage 计算属性会立即返回之前的计算结果，而不必再次执行函数。

计算属性setter

```
computed: {
  fullName: {
    // getter
    get: function () {
      return this.firstName + ' ' + this.lastName
    },
    // setter
    set: function (newValue) {
      var names = newValue.split(' ')
      this.firstName = names[0]
      this.lastName = names[names.length - 1]
    }
  }
}
```

## Class 与 Style

```
<div class="static"
     v-bind:class="{ active: isActive, 'text-danger': hasError }">
</div>
和如下 data：

data: {
  isActive: true,
  hasError: false
}
结果渲染为：

<div class="static active"></div>

我们也可以在这里绑定一个返回对象的计算属性。这是一个常用且强大的模式：

<div v-bind:class="classObject"></div>
data: {
  isActive: true,
  error: null
},
computed: {
  classObject: function () {
    return {
      active: this.isActive && !this.error,
      'text-danger': this.error && this.error.type === 'fatal'
    }
  }
}

直接绑定到一个样式对象通常更好，这会让模板更清晰：

<div v-bind:style="styleObject"></div>
data: {
  styleObject: {
    color: 'red',
    fontSize: '13px'
  }
}
同样的，对象语法常常结合返回对象的计算属性使用。

```
