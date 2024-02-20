**Testing**
- Blackbox test cases are created *without* looking at the implementation of the function being tested.
- Whitebox test cases are created looking at the implementation.
- Whitebox testing commonly ensures every line of a function is executed at least once by a test.
- Blackbox test cases can be created before any code has been written.
- *If-style* tests run slower than assert-style.
- When an *assert-style* test fails, the line number of the failed assertion is printed.

**Pointers and Memory Management**
- ``new int(5)`` and ``new int[5]`` bothe return a value of type ``int*``
- ``*(arr + 0)`` and ``arr[0]`` return the same thing.
- Dereferencing a ``nullptr`` is *always* an error.
- If T is a C++ type, then T* is the type of a pointer to a value of type T.
- The amount of call stack memory OR free store a program will use is *not* known at compile-time.

**Classes and Structs**
- ``const`` methods make the intent of the programmer clear.
- If a ``const`` method tries to modify a variable in the object, C++ will catch the error at *compile-time*.
