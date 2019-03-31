---
layout: post
title:  "JavaScript 知识点总结"
date:   2019-03-10
desc: "Frontend Basics"
keywords: "JavaScript,website,blog,easy"
categories: [Frontend]
tags: [JavaScript]
icon: icon-JavaScript
---
# JavaScript 知识点总结

- 原始类型：
Boolean, null, undefined, number, string, symbol

- 对象类型
除了原始类型以外都是对象类型。不同之处是原始类型存储的是值，对象类型存储的是地址。
例子：

```JavaScript
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

- typeof 和 instanceof
typeof 对于原始类型来说，除了 null 都可以显示正确的类型

```JavaScript
typeof 1 // 'number'
typeof '1' // 'string'
typeof undefined // 'undefined'
typeof true // 'boolean'
typeof Symbol() // 'symbol'
```

typeof 对于对象来说，除了函数都会显示 object，所以说 typeof 并不能准确判断变量到底是什么类型
如果我们想判断一个对象的正确类型，这时候可以考虑使用 instanceof，因为内部机制是通过原型链来判断的

```JavaScript
const Person = function() {}
const p1 = new Person()
p1 instanceof Person // true

var str = 'hello world'
str instanceof String // false

var str1 = new String('hello world')
str1 instanceof String // true
```


---
