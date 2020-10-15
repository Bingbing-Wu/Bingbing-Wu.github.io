---
title: JavaScript中的一些任务机制
abbrlink: 41514
date: 2020-09-19 09:24:50
tags:
---

# JavaScript中的执行机制、任务队列、宏任务和微任务

## JavaScript是单线程的
1. JavaScript是单线程的，意味着在同一时间时，只能做一件事情。
2. JavaScript的只要任务是操作DOM和用户进行交互，这决定了只能是单线程的。假如JavaScript是多线程的，一个线程在进行渲染DOM，而另一个线程在进行的DOM的删除，这必然会带来冲突。JavaScript的单线程已经成为其语言的最大特点。

## 任务队列 （task Queue)

### 在JS中，共有两种任务：同步任务和异步任务

1. 同步任务进入主线程，等本次任务执行完毕后，在执行下一个任务 
2. 异步任务：不进入主线程，进入任务队列，只有主线程通知异步任务和执行了，才会按需进行执行。
{% asset_img 任务队列.png This is an 任务队列 50%}

## JS中的宏任务(macrotask)和微任务(microtask)

### 宏任务 (macrotask)
1. 每次执行栈执行的代码就是一个宏任务
2. 浏览器对宏任务的执行流程
   宏任务 --> 网页渲染 --> 宏任务
### 微任务 (microtask)
1. 当前任务执行结束后，就立即执行的任务，在当前task任务完成后，下一个task任务开始之前，在渲染之前进行的任务。
主要的宏任务有：script脚本、setTimeout、setInterval、I/O、用户界面交互事件 postMessage MessageChannel setImmediate.
主要的微任务有：promise.then catch finally process.nextTick(Node环境)、mutationObserver(浏览器使用)

{% asset_img 宏任务和微任务.png This is an 宏任务和微任务 50%}
{% asset_img 宏任务和微任务的执行流程.png This is an 宏任务和微任务的执行流程 50%}
