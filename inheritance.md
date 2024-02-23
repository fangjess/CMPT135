**What is inheritance?**
- Think of it as a trick to create new classes.
- Ex.: Suppose you like ``vector<int>``, but what to have a ``sort()`` method, so you can type ``v.sort()``.
  - We want to create a class called ``int_vec`` that works just like ``vector<int>`` but has a ``sort()`` method.
  - Make a new class called ``int_vec``
  - ``int_vec`` inherits from ``vector<int>``
  
    ```
     class int_vec : public vector<int>
      {...}
    ```
  
  - Add ``sort()`` method to ``int_vec``
  - ``int_vec`` now works just like a ``vector<int>`` plus a ``sort()`` function.

**Modifying the child class**
- Adding a member variable:
  ```
  class int_vec : public vector<int> {
    string name;
  
  public:
    int vec(const string &name) : name(name) {
      assert(name.size() > 0);
    }
  
    string get_name() const {
      return "<intvec:" + name + ">";
    }
  
    void set_name(const string &name) {
      assert(name.size() > 0);
      this->name = name;
    }
  
    // ...
  
  };
  ```

**Polymorphism**
- Wherever a ``vector<int>`` can be used, we can replace it with ``int_vec``
  - Because ``int_vec`` can do everything a ``vector<int>`` can do.
- However, a ``vector<int>`` may not be able to do everything ``int_vec`` can.

**Public inheritance**
- When a class inherits from another class using ``public`` keyword.
- Members that were private/public in the class being inherited from *stay* public/private in the inheriting class.
  ```
  class int_vec : public vector<int> { // int_vec inherits from vector<int>
    // ...
  };
  ```
- All methods ``int_vec`` inherits from ``vector<int>`` have the *same* visibility.
  - e.i. ``public`` or ``private`` members stay that way.
