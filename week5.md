**OOP: Dates**
- Class called ``Date`` that represents a date (day, month, year)
  - 1 <= day <= 31
  - 1 <= month <= 12
  - 0 <= year (an int)
  - E.g. February 15, 2024 is (15, 2, 2024)
  - When using object-oriented features of C++, some prefer to use ``class`` since it signals OOP is being used.

    ```
    class Date {
    public:
      int day;
      int month;
      int year;

      void print() const {
        cout << "(" << day
              << ", " << month
              << ", " year
              << ")";
      }

      void println() const {
        print();
        cout << "\n";
      }
    };
    ```
    
  - ``print()`` and ``println()`` are public const methods.
  - ``day, month, year`` are public member variables.
  - if a method is declared ``const``, it is guaranteed by the compiler that it will not change any variables in the object.
    - Non-mutating method, "read-only".
    - Non-const method is called a mutating method, or a mutator.
    - If something *can* be const, make it const.
      - "const correctness"
      - Use const for parameters, read-only variables and methods.
      - Improved code readability and intent (makes it clear that a value should not change)
      - Compiler can tell you at compile-time if you try to modify something that's const
      - Safety for mulit-threaded code: data that can't change is much easier to use in programs that use multiple CPUs/multiple threads of control
        - Multi-threaded code: code that does more than one thing at the same time.
        - if const, impossible for different threads to change the object at the same time.

  ```
  Date(int d, int m, int y)
  : day(d), month(m), year(y)
  {
    assert(is_valid());
  }
  ```
  - Goes inside your class
  - Same name as the class
  - No explicit return type
  - The constructor takes as input whatever it needs to properly initialize itself.
  - ``: day(d), month(m), year(y)`` is an *initializer list*
    - Initializes variables in the class
    - Use the ``x(val)`` notation styles to initialize variables
    - this notation works with more kinds of objects than ``x = val`` style notation

**Encapsulation**
- Idea of protecting the implementation details of an object
- Data hiding: The implementation details of an object are intentionally hidden from the program
- Thus they don't need to worry about those details, and it allows for changing the object's implenetation later
  - E.g. a ``std::string`` is typically implemented using an array of characters, and the programmer does not need to know this when they use it
- Access control: The object controls how you can read/write its variables. This simplifies interacting with the object
  - E.g. in ``std::string`` object, you can read the size of the string, but you can't set the size of the string directly
   
**Getters**

  ```
  class Data {
    int day;
    int month;
    int year;
  public:
    int get_day() const { return day; }
    int get_month() const { return month; }
    int get_year() const { return year; }
  };
  ```
- getters or accessors return a value of an object's variable, Getters usually don't modify the object so they're typically const

**Designing an (x,y) point class**
- We want it to be easy to create points
- Think about what parts you want to be public and private
  - If you make x and y private you'll need setters/getters
  ```
  Point a(4, -5);
  cout << a.get_x();
  a.set_x(3);
  ```
  - If x and y are public:
  ```
  Point a(4, -5);
  cout << a.x;
  a.x = 3;
  ```
  - Since there doesn't seem to be obvious restrictions on accessing x and y, we cna make them public.
- Decide whether you want points to be mutable or immutable.
  - Means you can't change x and y.

**Implementing an ((x,y) point class**
```
struct Point
{
  const int x;
  const int y;

  Point(int x, int y)
  : x(x), y(y)
  {}

  Point(const Point &other) // A copy constructor takes another point object as input and copies its (x,y) values
  : x(other.x), y(other.y)
  {}

  Point() // A default constructor takes no inputs, assigns x and y some sensible default values
  : x(0), y(0)
  {}
};
```

**More on Free Store Allocation**

```
void f() {
  double* p = new double(6.4);

  cout << *p; // 6.4

  delete p;
}
```
- Make sure ``delete`` is called every time ``}`` is reached.

```
class Temeprature {
  double* temp;
public:
  Temperature(double t)
  : temp new double()
  {}

  double get_temp() const {
    return *temp;
  }

  void set_temp(double t) {
    *temp = t;
  }

  ~Temperature() {
    delete temp;
  }
}
```

- Constructor called ``new``
- Destructor ``~Temperature()`` is called automatically
  - Calls delete
  - Destructor is always called automatically when the object it's associated with is deallocated
  - Destructor is always the name of the class with a ``~`` at the start
  - Takes no inputs

**Resource Acquisition is Initialization (RAII)**
- RAII is the idea of managing memory using objects
- The memory...
  - is allocated in the objects constructor
  - exists for the lifetime of the object
  - is automatically deallocated when the object's destructor is called
- The details of the memory managed are completely handled by the object
  - No memory leaks/dangling pointers
- RAII can also be used for other resources:
  - File handles
  - Network connections

**Assignment 2**
- Constructors
- Destructors
- Management of memory
- Creating a dynamic structure
- Start from free store allocation example as a base template
- Maybe create an ``append()`` method to add something to the end of your array
- How to get more memory for ``append()``?
  - Make a new array, copy everything over with room for the object you're appending
  - Delete the previous array
