**Pointers**
- Pointer has to match the type of what you're pointing to.
- Never dereference a null pointer.
- If ``p`` is a pointer, ``*p`` is the de-referenced pointer, and it gives the value ``p`` points to.
- Pointers to structs:
  ```
  struct Point {
    double x;
    double y;
  };
  
  Point* p = new Point{1.1, 0.5};

  cout << (*p).x; // 1.1
  cout << (*p).y; // 0.5
  ```
- Must put brackets around *p: ``(*p).x``
  - ``.`` is evaluated before ``*``.
- ``p -> x`` is short for ``(*p).x``

- Practice: Write a loop that prints the elements of arr using ``[]`` notation.
- Write a loop that prints the elements of arr without using ``[]`` notation.
- ``int arr[] = {4, 1, 5};``
  ```
  for (int i = 0; i < 3; i++) {
    cout << *(arr + i);
  }
  ```

**Using free store memory**
```
  void f() {
    double* p - new double (6.4);
    // ...
    delete p;
  }
```
- Memory leak: what happens if ``p`` is popped from the call stack due to function ``f()`` ending?
- Over time small leaks can add up to waste lots of memory.
- Valgrind can recognize memory leaks in a running program.
- `` delete p`` tells C++ to de-allocate the memory that p points to so that it can be re-used.
- A "dangling pointer" is when you delete the memory too soon (a pointer that is not pointing to valid memory).

![image](https://github.com/fangjess/CMPT135/assets/140139367/87dd57d8-9685-43ac-99f8-65a067d768b5)

- ``delete`` given an address, will delete what it points to
  - double deletion is always an error.
  - deleting an array, use ``delete[] arr``
 
- You can point to 1 past the last index of your array (incrementing in a for loop for example...)
  - You can look at what's stored there but cannot do anything with it.

**Function to initialize an array**

```
int* make_array(int size, int fillVal)
{
  assert(n >= 0);
  int* arr = new int[4];
  for (int i = 0; i < size; i++) {
    arr[i] = fillVal;
  };
  return arr;
}
```

**Function to copy an array**
```
int* make_copy(int* other, int n)
{
  int* arr = new int[n];
  for (int i = 0; i< n: i++) {
    arr[i] = other[i];
  };
  return arr;
}

int main()
{
  int* a = make_array(4, 3);
  int* b = make_copy(a, 4);

  return 0;
}
```

**Filtering an array**
- Write a function that takes an int* to an array as input, and returns a pointer to a newly created array that is the same as the original, but all negative ints are removed.
- Name the function remove_negatives
- It returns an int* to the new array. You write the inputs for it.
