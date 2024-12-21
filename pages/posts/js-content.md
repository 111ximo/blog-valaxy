---
title: js基础知识-执行上下文
date: 2024-11-01
updated: 2024-11-01
categories: js基础知识
tags:
  - 笔记
  - js
top: 1
---

## Javascript 的执行上下文栈
对于每个执行上下文，都有三个重要属性
-变量对象(Viriable object,VO)
-作用域链(Scope chain)
-this

Javascript的可执行代码有全局代码、函数代码、eval代码。

Javascript创建了执行上下文栈。在执行到一个函数的时候，会创建一个执行上下文，并且压入执行上下文栈，当函数执行完毕的时候，就会将函数的执行上下文从栈中弹出。

  ```var scope = "global scope";
  function checkscope(){
      var scope = "local scope";
      function f(){
          return scope;
      }
      return f();
  }
  checkscope();
  ```
压入：globalscope->checkscope->fscope->弹出：fscope->checkscope->globalscope

  ```var scope = "global scope";
  function checkscope(){
      var scope = "local scope";
      function f(){
          return scope;
      }
      return f;
  }
  checkscope()();
  ```
压入：globalscope->checkscope->弹出：checkscopr->压入：fscope->弹出：fscope

这两端代码都会输出local scope，但是上下文栈不同。
