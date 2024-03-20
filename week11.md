**Topics**
- Linear search
- Average case performance
- Linear insertion sort

**Searching**
- Linear search:
  - Pseudocode:
  ```
  Step 1: Does item 0 = x? If so, stop and return 0.
  Step 2: Does item 1 = x? If so, stop and return 1.
  ...
  Step n: Does item (n-1) = x? If so, stop and return (n-1).
  Step n + 1: Otherwise, stop and return -1.
  ```
  - If you have some idea where *x* might be, then searching in different order may be faster in some cases.
  - Suppose you're looking for ``.`` character in a file name, usually near right-end, so searching from *right to left* is probably faster
  - Most importantly, each element of the vector/array is checked once.
  - Ideally want to check elements in order from msot likely to be *x* to least likely.

 **Average Case Performance**
 - What is the expected *average* number of comparisons done by linear search?
 - Consider two cases:
   - **Case 1:** *x* is in *v*
   - **Case 2:** *x* is not in *v*
   - Assume each case occurs 50% of the time.
   - Total number of comparisons will be the average of the two cases.
   - E.i. (1/2)(# of case 1 comparisons) + (1/2)(# of case 2 comparisons)
  
- How to find how many comparisons in each case?
  - Assume:
    - *v* (vector we're searching) contains *n* unique items.
    - the probability *x* is in *v* is 1/2
    - if *x* is in *v*, then it has an equal chance of being at any location. (1/*n*)

- **When *x* is in *v***:
  - If *x* is at index ``0``, 1 comparison is done
  - If *x* is at index ``1``, 2 comparisons are done
  - If *x* is at index ``2``, 3 comparisons are done
  - If *x* is at index ``n-1``, *n* comparisons are done
- Thus:
  - 1/*n* of the time 1 comparison is done
  - 1/*n* of the time 2 comparisons are done
  - 1/*n* of the time 3 comparisons are done
  - etc.
- The total amount of work done is the **sum** of each case:
    (1/*n*) * **1** + (1/*n*) * **2** + ... + (1/*n*) * ***n***
      = (1/*n*)(1 + 2 + ... + *n*)
      = (1/*n*) * ((*n*(*n* + 1)/2)
      = (*n* + 1)/2
      = (*n*/2) + (1/2)

- **When *x* is NOT in *v***:
  - Exactly *n* comparisons are done
  - Average case performance expression becomes:
    (1/2) * (# of comparisons done when *x* is in *v*) + (1/2)*n*

- So assuming there's a 50/50 chance *x* is in *v*, and assuming if *x* is in *v* it has an equal chance of being at any position, on average we would expect linear search to do:
  
  (1/2)((*n* + 1)/2) + (1/2)*n*
  
calls to ``==``.

**Insertion Sort**
- Insertion sort divides the list into a sorted part and unsorted part.
- Start with the first element as the sorted part.
- Then take the first element of unsorted, and insert it into its corrected position in the sorted part.
- Finding the correct insertion point requires searching through the sorted part.

Implementation example:

```
void insertion_sort(vector<int>& v) 
{
   for(int i = 1; i < v.size(); ++i) 
   {

     // key is the value we are going to insert
     // into the sorted part of v
     int key = v[i];      

     // j points to one position before the 
     // (possible) insertion point of the key;
     // thus, key will eventually be inserted at 
     // v[j + 1]
     int j = i - 1;

     //
     // This loop determines where to insert the key 
     // into the sorted part of v. It does this by 
     // searching backwards through the sorted part 
     // for the first value that is less than, or equal 
     // to, key.
     //
     // This loop combines searching with element 
     // moving. Every time an element bigger than the 
     // key is found, it is moved up one position.
     //
     // It's possible that there is no value in the 
     // sorted part that is smaller than key, in which 
     // case key gets inserted at the very start of v. 
     // This is a special case that is handled by j >= 0 
     // in the loop condition.
     //
     while (j >= 0 && v[j] > key) 
     {
        v[j + 1] = v[j];
        --j;
     }
     // After loop ends this is true: 
     // (j < 0 || v[j] <= key)

     v[j + 1] = key;   // j points to the location 
                       // *before* the one where key 
                       // will be inserted
   }
}
```

**Performance of Linear Insertion Sort**
- Insertion sort will do at most *n* - 1 insertions
  - Because each insertion reomves one item from sorted
- Each insertion also requires doing a linear search to find out where the element goes.
- In general, in the worst case insertion sort does (*n*(*n* - 1))/2 comparisons to sort *n* objects.
  - Expression is quadratic
  - When *n* is big, term *n*/2 doesn't make much difference so it can be ignored.
  - Thus, when *n* is big, insertion sort does *n*^2 comparisons.
  - Same for number of elements *moved* by insertion sort.
- Quite slow when *n* is large
- Should only be used for sorting a small number of items.

