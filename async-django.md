# Async Django

## GIL

The **Global Interpreter Lock (GIL)** is a feature of Python that basically means only one line of code can be executed at a time.

Python manages memory by counting the number of references to a variable, removing it from memory when the counter reaches zero.

Multiple threads can introduce race conditions where multiple threads attempt to mutate the reference counter for a variable at the same time.

The GIL means only one thread can have control of the Python intepreter, avoiding the race condition.

It effectively makes Python a single-threaded programming language.

Not all programming languages use a GIL. For example Java uses garbage collection rather than reference counting for memory management. To boost performance, Java uses a **Just in Time (JIT)** compiler. 

Source: [What Is the Python Global Interpreter Lock (GIL)?](https://realpython.com/python-gil)
