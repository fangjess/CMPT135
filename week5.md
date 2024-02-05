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
