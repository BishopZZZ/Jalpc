---
layout: post
title:  "HTML summary"
date:   2019-03-10
desc: "Frontend Basics"
keywords: "Jalpc,Jekyll,gh-pages,website,blog,easy"
categories: [Frontend]
tags: [HTML,Jekyll]
icon: icon-html
---
# JavaScript 知识点

- 原始类型：
Boolean, null, undefined, number, string, symbol

- 对象类型
除了原始类型以外都是对象类型。不同之处是原始类型存储的是值，对象类型存储的是地址。
例子：
'''JavaScript
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
'''

所以最后 person 拥有了一个新的地址（指针），也就和 p1 没有任何关系了，导致了最终两个变量的值是不相同的。

---
