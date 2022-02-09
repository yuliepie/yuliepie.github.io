---
layout: post
title: Async Programming
tag: Programming
image:
---

## **Blocking vs Non-blocking**

Blocking refers to operations that **block further execution** until that operation finishes. Non-blocking refers to code that doesn't block execution. 

In the given example, `localStorage` is a blocking operation as it stalls execution to read. On the other hand, `fetch` is a non-blocking operation as it does not stall `alert(3)` from execution.

```js
// Blocking: 1,... 2
alert(1);
var value = localStorage.getItem('foo');
alert(2);

// Non-blocking: 1, 3,... 2
alert(1);
fetch('example.com').then(() => alert(2));
alert(3);
```

Blocking code normally happens on **I/O operations, which rely on external data or response**. An I/O task is a task which the CPU cannot perform on its own and must wait for an external components, such as a network response. Usually this involves waiting a long time, compared to the CPU speed, so it's better to switch to another task while waiting.

## **Advantages**

One advantage of non-blocking, asynchronous operations is that you can maximize the usage of a single CPU as well as memory. CPU can perform other tasks while waiting, and return to the previous task once the IO task is done.

## Synchronous & blocking example

An example of synchronous, blocking operations is how some web servers like ones in Java or PHP handle IO or network requests. 

If the code reads from a file or the database, your code "blocks" everything after it from executing. In that period, your machine is holding onto memory and processing time for a **thread *that isn't doing anything*.**

One way to handle other requests while that thread is waiting is to spawn more threads to work on other requests, which requires more resources (memory), which is referred to as **concurrency or parallelism**, a concept distinct from asynchronous programming.

## Asynchronous, non-blocking example

Asynchronous, non-blocking servers - like ones made in Node or FastAPI - only use **one thread to service all requests**. This means an instance of Node makes the most out of a single thread. The creators designed it with the premise that the I/O and network operations are the bottleneck.

So when requests arrive at the server, they are serviced one at a time. 

*Picture 3 queues:* The first queue is the **current execution stack**, second queue is for **pending IO callbacks**, and the third queue is tasks **pending execution**. 

<img src="/assets/images/async-queues.png" alt="drawing" width="auto"/>

When the code needs to query the DB for example, it sends the callback to the second queue *and the main thread will continue running* (it doesn't wait) on other tasks from the first and third queues. Now when the DB operation completes and returns, the corresponding callback is pulled out of the second queue and queued in the third queue. When the engine gets a chance to execute something else (current execution stack is empty), it picks up a callback from the third queue and executes it.

## Performance

In pure terms, an asynchronous request is slower than an equivalent synchronous request because the thread works on other tasks before returning to the first task. However the real benefit happens when scalability is an issue, i.e. ***there are more requests than threads available***. If there are 4 threads who are all working on potentially blocking IO requests, The remaining requests have to wait to even start.

The reason this is important is because in real world environments, it is *impossible to correctly predict* the load at any one time and have a server big enough to handle it using one thread per request. So it is important to maximise the server’s hardware capabilities to handle as many requests as possible, and an asynchronous server can handle several times the number of concurrent requests as a synchronous sever when both thread pools are at the max level.

Also, async code scales faster than synchrounous, because synchrounous code can’t scale faster than the thread injection rate. So a sudden heavy load means very slow response time.

It is important to note that async code does not completely replace the need for a thread pool (multiple threads). It’s not one or the other - async code allows the app to make optimum use of the thread pool, and draw out its maximum efficiency. So I guess it is always better to choose async over sync with scalability in mind.