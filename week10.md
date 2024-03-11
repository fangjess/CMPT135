**More Recursion**

Examples:


Fibonacci sequence
```
// Returns the nth Fibonacci number (n > 0)
int f(int n)
{
    if( n == 1)   // base case
    {
      return 1;
    }
    else if(n == 2)  // base case
    {
      return 1;
    }
    else
    {
      return f(n - 1) + f(n -2);  // recursive case
    }
}
```

Recursion on Vectors:
Suppose we want to sum the numbers in a vector recursively.
- Base case: the empty vector has sum 0. e.g. ``sum({})`` is 0
- Recursive case: the sum of all the elements in ``v`` is ``v[0] + sum(rest(v))``
- The function ``rest(v)`` returns a copy of the original vector with the first element chopped off.

```
// Returns a new vector w of n - 1 (n == v.size()) such that
// w[0] == v[1], w[1] == v[2], ..., w[n - 2] == v[n - 1].
// In other words, it returns a copy of v with the first element 
// chopped off.
vector<int> rest(const vector<int>& v) 
{
   vector<int> result;
   for (int i = 1; i < v.size(); i++)  // i starts at 1
   {
      result.push_back(v[i]);
   }
   return result;
}
```

Now we can write ``sum`` as follows:

```
int sum1(const vector<int>& v) 
{
   if (v.empty())    // base case
   {
      return 0;  
   } else            // recursive case
   {
      return v[0] + sum1(rest(v));
   }
}
```

A more efficient approach is to simulate rest by re-writing sum1 to accept begin and end parameters specifying the range of values in v that we want summed.
Then we can efficiently access any sub-vector:

```
// returns v[begin] + v[begin + 1] + ... + v[end - 1]
int sum2(const vector<int>& v, int begin, int end) 
{
   if (begin >= end) 
   {
     return 0;
   } else 
   {
     return v[begin] + sum2(v, begin + 1, end);
   }
}

// returns the sum of all the elements in v
int sum2(const vector<int>& v) 
{
   return sum2(v, 0, v.size());
}
```
