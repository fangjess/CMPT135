**Filtering an Array**
- Write a function that takes an int* to an array as input, returns a pointer to a newly created array that is the same as the original, but all negative ints are removed.
- need to pass in result_size, use a loop to count number of positives/negatives.
  ```
  int* remove_negs(int* a, int size, int& result_size)
  {
    results_size = 0;
    for (int i = 0; i < size; i++) {
      if (arr[i] >= 0) {
        result_size++;
      }
    }
    
    int* p = new int[result_size];
    // Copy all positives into p:

    int j =0;
    for (int i = 0; i < size; i++) {
      if (arr[i] >= 0) {
        result[j] = arr[i];
        j++;
      }
    }
    return result;
  }
  ```
  
**Swapping**
- ``swap()`` takes *addresses* as its parameters:
  ```
  int x = 4;
  int y = 1;
  swap(&x, &y);
  // now x == 1, y == 4;
  ```
  
- Without using ``swap()``  function:
  ```
  void swap3{int* a, int* b}
  {
    int temp = *a;
    *a = *b;
    *b =  temp;
  }
  ```
- Note: in C++ we prefer passing by reference ``&`` instead of pointers.

**Object oriented programming**
- Data and operations are combined into a single value called an *object*.
- Classes and structs are pretty much the same thing in C++.
  - E.g. in Pac Man you would have a struct for the ghosts, another for the pellets, etc.
  - E.g. a class called ``small_pellet`` and each individual pellet you see is an instance of ``small_pellet``
- Object oriented programming is a choice; may be a good way to implement a program, but not the only way.

**Arrays in C++**
- Pros:
  - Efficient arr[i], *(arr+i)
  - No wasted memory.
  - Built-in support.
  - Works well with pointers
- Cons:
  - Don't know their length.
  - Fixed size.
  - Error prone: no bounds checking
  
    
