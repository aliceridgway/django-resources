# Async Django


## Background

Some understanding of how Python works explains how asynchronous programming can improve the performance of web applications.

### GIL

The **Global Interpreter Lock (GIL)** is a feature of Python that basically means only one line of code can be executed at a time.

Python manages memory by counting the number of references to a variable, removing it from memory when the counter reaches zero.

Multiple threads can introduce race conditions where multiple threads attempt to mutate the reference counter for a variable at the same time.

The GIL means only one thread can have control of the Python intepreter, avoiding the race condition.

Not all programming languages use a GIL. For example Java uses garbage collection rather than reference counting for memory management. To boost performance, Java uses a **Just in Time (JIT)** compiler. 

Source: [What Is the Python Global Interpreter Lock (GIL)?](https://realpython.com/python-gil)

### CPU-bound vs I/O-bound

CPU-bound threads are where the performance is limited by the hardware the program is running on.

The GIL will prevent two CPU-bound threads from working in parallel. Only one thread can have control of the GIL at a time.

For I/O bound threads, the GIL will share the lock. This means one thread can be processed while another waits for I/O.

### Analogy

There are two queues of people for one ticket office. The ticket office can only serve one person at a time.

For a CPU-bound process, the throughput of people is limited by how quickly the ticket office can serve customers. It doesn't matter if the waiting customers are in one queue or split across two.

For an I/O bound process, imagine a person is ready to be served but they're still looking for their wallet. If there is one queue, then no one can be served while this person searches their bag.

In a multi-threaded process, the ticket office can serve a customer from the other queue while they wait for the slow customer.

In the context of a web application, that slow customer is a process waiting for a database to return the results of a query or a client waiting for the response from an external API.

### Multithreading vs Multiprocessing

**Article**: [Multithreading and Multiprocessing in 10 Minutes](https://towardsdatascience.com/multithreading-and-multiprocessing-in-10-minutes-20d9b3c6a867)

The GIL means that only one thread can have control of the Python interpreter at a time.

Multi-threading is the concept of having multiple threads on a single processor.

Multi-processing is the concept of running multiple processors concurrently.

In the context of our analogy, multi-threading is having multiple queues for one ticket office. Multi-processing is the equivalent of having multiple ticket offices.

Python has the [multiprocessing](https://docs.python.org/3/library/multiprocessing.html) library to set up subprocesses. However, you are limited to the number of processors on your machine.


### Is Django Single-Threaded?

No.

Sychronous and single-threaded are not the same thing.

Asynchronous and multi-threaded are also not the same thing.

## WSGI

[WSGI is not enough anymore - Part 1](https://www.475cumulus.com/single-post/2017/04/03/WSGI-Is-Not-Enough-Anymore)
[Part 2](https://medium.com/475cumulus/wsgi-is-not-enough-anymore-part-ii-b78b4cfdd09)



## Async Python

Asynchronous support has been part of Python since Version 3.4 (released March 2014) which introduced the `asyncio` library.

Familiarising with the `asyncio` will teach you the basics of async Python and provide a foundation for using async Django.

### Coroutines

A [Coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutines) is an asynchronous function declared with the async/await syntax.

e.g.

```
async def some_function():
    await asyncio.sleep(3)
    print("done!")
```

Coroutine functions return coroutine objects, so calling them directly would be unhelpful.

Instead, use `asyncio.run()`

### Tasks

[Tasks](https://docs.python.org/3/library/asyncio-task.html) are a type of awaitable object. They are used to schedule coroutines concurrently. Coroutines can be scheduled using `asyncio.create_task()`.

### The Event Loop

At the heart of the `asyncio` library is the Event Loop, a class which manages the asynchronous execution of coroutines.

With shameless help from ChatGPT, an event loop is:

> ...a programming construct that manages and schedules the execution of asynchronous tasks or coroutines. The event loop runs in a single thread and allows multiple coroutines to run concurrently without blocking the execution of the main thread.

> When a coroutine yields control to the event loop, the event loop can switch to executing another coroutine that is ready to run, thereby allowing multiple coroutines to make progress simultaneously. The event loop manages a queue of coroutines and schedules their execution based on their readiness to run, typically using non-blocking I/O operations or timers.

## Asynchronous Web

##



