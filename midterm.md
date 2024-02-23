**Testing**
- Unit testing: test one part of a program, e.g. a single function.
- System testing: Testing the entire system.
- Blackbox test cases are created *without* looking at the implementation of the function being tested.
- Whitebox test cases are created looking at the implementation.
- Whitebox testing commonly ensures every line of a function is executed at least once by a test.
- Blackbox test cases can be created before any code has been written.

**Methods of testing**
- If-style tests run slower than assert-style.
- Table-based testing is easier to add new test cases than if-style.
- Assert-style testing is usually simplest.

**Pointers and Memory Management**
- If T is a C++ type, then T* is the type of a pointer to a value of type T.
- ``new int(5)`` and ``new int[5]`` bothe return a value of type ``int*``
- ``*(arr + 0)`` and ``arr[0]`` return the same thing.
- Dereferencing a ``nullptr`` is *always* an error.
  - Must be 100% sure that ``p`` is not the ``nullptr`` when you evaluate ``*p``.
- The amount of call stack memory OR free store a program will use is *not* known at compile-time.
- Pointers to structs:
  - ``(*p).x`` is the same as ``p -> x``
- ``this``: used for an object to refer to itself.

**Classes and Structs**
- ``const`` methods make the intent of the programmer clear.
- If a ``const`` method tries to modify a variable in the object, C++ will catch the error at *compile-time*.
- A copy constructor *does not* have to use an initializer list.
