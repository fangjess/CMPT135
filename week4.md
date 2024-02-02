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
 
- Example: sorting an array:
  ```
  #include <algorithm>
  using namespace std;
  
  struct intarray
  {
      int* arr;
      int size;
  };
  
  // Function to sort an array
  void sort_array(intarray a)
  // Pass by value is fine for arrays; creating a copy of the pointer to the array
  // but data at pointer is not copied.
  {
      sort(a.arr, a.arr + a.size);
  }
  ```
 
**OOP: Objects and classes**
- Objects vs classes example:
  - The circle is a common shape (class of all circles)
  - The circle I've just drawn is very big (a particular circle; the object)
- Objects:
  - Exist at run-time
    - Dont exist at compile-time.
  - Values typically composed of smaller values
  - Must be allocated and de-allocated
  - Have the type of their class
- Classes (basically structs):
  - Exist at compile-time
    - Don't exist at run-time in C++
  - Like blueprints for creating an object
  - Classes are the types for the objects they describe


  ```
  struct Person {
    string name;
    int age;

    string to_string() {
      return name + "" +
          std::to_string(age);
    }
  };

  // need std:: notation because to_string() is both a function in std library and the name of our function.
  ```
  
**Public & Private**
  - Variables inside the struct are member variables.
  - Can also have member functions inside the struct called *methods*.
  - Methods can access the member variables and methods of the struct without any special notation.
  - Private: means specified members are only accessible from other member functions (e.g. can't access from main()).
  - Public: specified members accessible from any function.
  - By default, all members of a *struct* are public.
  - By default, all members of a *class* are private.
  
  ```
  struct Person {
  private:
    string name;
    int age;
  public:
    string to_string() {
      return name + "" +
        std:: to_string(age);
    }
  };
  ```

  - Example of object 'bob' of type 'Person':
  - cout << bob.name // Compiler error (name and age are private)
  - cout << bob.age // Compiler error
  - cout << bob.to_string(); // Bob 25 (to_string is public)
  
  

    
