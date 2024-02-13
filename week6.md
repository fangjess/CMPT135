**Inheritance**
- Think of it as a trick for creating new classes
- E.g. create a class called ``int_vec``, but also has a ``sort()`` method so we can write ``v.sort()``
- With inheritance:
  - Make a new ``class`` called ``int_vec``
  - ``int_vec`` inherits from ``vector<int>``
  - add the ``sort()`` method to ``int_vec``
  - With inheritance, we can use the methods in ``vector<int>`` in any methods we add to ``int_vec``

```
class int_vec : public vector<int> {

public:

  void sort() {
    std::sort(begin(), end());
  }

  int sum() const {
    int result = 0;
    for(int i = 0; i < size(); i++) {
      result += (*this)[i];
    }
    return result;
  }
  // Every C++ object has a pointer called 'this' that points to the object itself.
  // Can also use for-each: for(int n : *this) { result += n; }
};

int main()
{
  int_vec v;
  
  v.push_back(2);
  v.push_back(1);
  
  v.sort();
  
  for (int n : v) {
    cout << n "";
  }
}
```
- We can also add member variables to ``int_vec`` that dont appear in ``vector<int>``

**Polymorphism**
- Whenever a vector<int> can be used, we replace it with int_vec
- That's because an int_vec can do everything a vector<int> can do and more.
