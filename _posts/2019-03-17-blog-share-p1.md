---
layout: post
title:  "JavaScript 知识点总结（一）"
date:   2019-03-10
desc: "Frontend Basics"
keywords: "JavaScript,website,blog,easy"
categories: [Frontend]
tags: [JavaScript]
icon: icon-javascript
---
## JavaScript 知识点总结(一)

### **原始类型**：

Boolean, null, undefined, number, string, symbol

***

### **对象类型**：

除了原始类型以外都是对象类型。不同之处是原始类型存储的是值，对象类型存储的是地址。
例子：

```js
function test(person) {
  person.age = 26
  person = {
    name: 'yyy',
    age: 30
  }

  return person
}
const p1 = {
  name: 'yck',
  age: 25
}
const p2 = test(p1)
```

所以最后 person 拥有了一个新的地址（指针），也就和 p1 没有任何关系了，导致了最终两个变量的值是不相同的。

***

### **typeof 和 instanceof**：

typeof 对于原始类型来说，除了 null 都可以显示正确的类型

```js
typeof 1 // 'number'
typeof '1' // 'string'
typeof undefined // 'undefined'
typeof true // 'boolean'
typeof Symbol() // 'symbol'
```

typeof 对于对象来说，除了函数都会显示 object，所以说 typeof 并不能准确判断变量到底是什么类型
如果我们想判断一个对象的正确类型，这时候可以考虑使用 instanceof，因为内部机制是通过原型链来判断的

```js
const Person = function() {}
const p1 = new Person()
p1 instanceof Person // true

var str = 'hello world'
str instanceof String // false

var str1 = new String('hello world')
str1 instanceof String // true
```

***

### **类型转换**：

 JS 中类型转换只有三种情况，分别是：

1. 转换为布尔值： 在条件判断时，除了 undefined， null， false， NaN， ''， 0， -0，其他所有值都转为 true，包括所有对象。
2. 转换为数字：调用 x.valueOf()，如果转换为基础类型，就返回转换的值
3. 转换为字符串： 调用 x.toString()，如果转换为基础类型，就返回转换的值

***

### **this**：

```js
function foo() {
  console.log(this.a)
}
var a = 1
foo()

const obj = {
  a: 2,
  foo: foo
}
obj.foo()

const c = new foo()
```

对于直接调用 foo 来说，不管 foo 函数被放在了什么地方，this 一定是 window.
对于 obj.foo() 来说，我们只需要记住，谁调用了函数，谁就是 this，所以在这个场景下 foo 函数中的 this 就是 obj 对象.
对于 new 的方式来说，this 被永远绑定在了 c 上面，不会被任何方式改变 this.

```js
function a() {
  return () => {
    return () => {
      console.log(this)
    }
  }
}
console.log(a()()())
```

首先箭头函数其实是没有 this 的，箭头函数中的 this 只取决包裹箭头函数的第一个普通函数的 this。在这个例子中，因为包裹箭头函数的第一个普通函数是 a，所以此时的 this 是 window。另外对箭头函数使用 bind 这类函数是无效的。
