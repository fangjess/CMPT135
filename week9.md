**Exceptions and Recursion**

**Exceptions**
- General purpose technique for error-handling
- Exceptions are "thrown"
- Immediately stops the function, passes the exception object out of the function, up to the calling function
- A bit like a ``return``
- When you throw an exception, there's always a possibility that it might stop the program.
- Use exceptions only when the issue is "worth" possibly crashing the entire program.
- ``try`` & ``catch`` blocks:
  - Can have multiple catch parts, one for each kind of exception you want to handle.
  - ``catch (...)`` notation catches any exception, best to put it as the final catch block.
  - Destructors are called when exceptions are thrown; prevents memory leaks when working with free-store.

**Other ways to handle errors**
- Global variable flags
- Extra error return value

**Recursion**

```
void f()
{
  f();
}

int main()
{
  f();
}
```
- In theory, this program should run infinitely, however when ran it crashes inmmediately.
  - Every time ``f()`` is called, some call stack memory is useed.
- If you add flag ``-O2`` to makefile, will optimize your program.
- Running the code after ``-O2`` completely changes the behaviour of the program.
  - Program doesn't crash anymore.
- Why?
  - ``-O2`` Rewrites program into loop
 
```
void f(int n)
{
  if(n > 10) {
    return;
  } else {
      cout << n << endl;
      f(n + 1);
  }
} 

int main()
{
  f(1);
}
```
- This example will execute about *half* as many times as the previous.
  - Due to ``int`` taking up memory
- Note: This recursive loop is kind of like if you wrote a `for()` loop with ``i = 1, i++ ...``
- Note: "Tail recursion" is when the last part of the loop being called is the recursive function.
  - This function is tail-recursive.

```
void g(int n)
{
  if(n > 0) {
    g(n - 1);
    cout << n << " ";
    g(n - 1);
  }
}
```
- Order of which function executes ``cout``, from top to bottom & right to left:
  g(1)
  
  g(2)  - g(1)
  
  g(3)  - g(1)
        - g(2)
        - g(1)

- Prints: ``1 2 1 3 1 2 1``
