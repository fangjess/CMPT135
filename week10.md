**Topics**
- Recursion
- Encryption
- Calculating large powers

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

**Passwords and Encryption**
- Encrypting means to scramble something in such a way that only someone with the key for decrypting it can read it.
- Web pages that use ``https`` automatically encrypt and decrypt information

```
> cat password.txt 
swordfish

❯ ccencrypt password.txt 
Enter encryption key: honeybee
Enter encryption key: (repeat) 

❯ cat password.txt.cpt 
��[��d�d#���3�;4�g�⏎   

❯ ccdecrypt password.txt.cpt 
Enter decryption key: honey

❯ cat password.txt
swordfish
```

- Unless you have the encryption key (i.e. the password string honeybee), it's practically impossible to determine the encrypted password.
- How do you communicate the encryption key to a site so it can decrypt your password?
  - You have to send them the key somehow, and if you send it unencrypted over the web then hackers could copy it.
  - If you encrypt the key, then that encryption needs its own key: how do you send that key securely?
- The RSA Cryptosystem solves this problem using an idea called public key cryptography.
  - The bank provides a special public key that anyone can use to encrypt a message that only the bank can decrypt.
  - The bank does the decryption with a private key that they don’t share with anyone else.

**Calculating Large Integer Powers**
- The "basic" way to calculate ``a^n`` is to multiply ``a`` by itself ``n - 1`` times.

```
// Pre-condition: 
//    n >= 0
// Post-condition: 
//    returns a to the power of n, i.e. a^n
int power_iter(int a, int n) 
{
    // check pre-condition
    if (n < 0) cmpt::error("exponent must be non-negative");

    if (a == 0 && n == 0) return 1;
    if (a == 0 && n != 0) return 0;
    if (a != 0 && n == 0) return 1;
    if (a == 1) return 1;
    
    int pow = 1;
    for(int i = 0; i < n; i++) 
    {
        pow *= a;
    }
    return pow;
}
```
- Note the use of contracts to specify what the function ought to do.
  - When a function is specified using a *pre-condition* and a *post-condition*, then we can say there is a contract between the function and the 
    rest of the program.

- Same algorithm implemented using *recursion*:
```
int power_recur(int a, int n) {
    // check pre-condition
    if (n < 0) cmpt::error("exponent must be non-negative");

    if (a == 0 && n == 0) return 1;
    if (a == 0 && n != 0) return 0;
    if (a != 0 && n == 0) return 1;
    if (a == 1) return 1;
    
    return a * power_recur(a, n - 1);
}
```
- While the source code is shorter than ``power_iter``, it's probably a little less efficient since each call to ``power_recur`` uses extra time 
  and call stack memory.
