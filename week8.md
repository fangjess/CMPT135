**Namespace & Seperate Compilation**

**Namespaces**
- ``throw std::runtime_error(message)``
- ``throw`` causes an exception object to propagate through the program; similar to return but for errors
- ``runtime_error`` is an exception object; used when error occurs at runtime
- must ``#include<stdexcept>``
- must use ``std::`` when there is no using namespace statement in the file
- namespaces used to solve "name clashes"
- For example, ``std::terminate()``, and ``cmpt::terminate()`` work because they are in different namespaces, just have to specify from which namespace you are using it from
- ``using``
  - ``using namespace std`` means you're using everything from ``std``
  - ``using std::cout`` means you're only using ``std::cout``

**Seperate Compilation**
- Dividing a program into seperate files
- Each file compiled individually
- All files linked together using g++ to make the final executable
- Definitions and declarations:
  - In C++ you can define things, and you can declare things; they are different.
  - ``double f(double x);`` declaration, just the header
  - ``double f(double x) { return 2 * x - 5; }`` definition, includes the body
  - ``class Point;`` declaration
  - ``class Point {
    public:
      double x, y;
    };``  definition
  - All definitions are declarations, not vice versa though.
  - Cannot define a function twice.
  - you can overload a function with the same name to make it work: ``double f(double x){}`` and ``double f(string x){}`` will compile.
  - You can declare a function multiple times.
  - Single definition rule: Things in C++ must be defined exactly once. However you can declare something as many times as you like.
  - Always an error if something is defined 0 times, or more than once.
