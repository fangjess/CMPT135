**Binary Search**
- Data given to search algorithm in sorted order
- Picks the middle most element, if desired element is *greater* than it:
  - Erase all elements to the *left* of the selection (remove all smaller elements)
- If desired element is *less* than selection:
  - Erase all elements to the *right* of the selection (remove all larger elements)
- Binary search continues to do this until the desired element is found/ all elements have been searched
  - Pick the middle element
  - Compare; is the element you're looking for greater or larger?
    - If it's equal, search is complete.
  - Erase the irrelevant half of the data
  - Repeat
 
**Performance of Binary Search**
- 
