**Filtering an Array**
- Write a function that takes an int* to an array as input, returns a pointer to a newly created array that is the same as the original, but all negative ints are removed.
- need to pass in result_size, use a loop to count number of positives/negatives.
  ```
  int* remove_negs(int* a, int size, int& result_size)
  {
    results_size = 0;
    for (int i = 0; i < size; i++) {
      if (arr[i] >= 0) {
        result_size++;
      }
    }
    
    int* p = new int[result_size];
    // Copy all positives into p:

    int j =0;
    for (int i = 0; i < size; i++) {
      if (arr[i] >= 0) {
        result[j] = arr[i];
        j++;
      }
    }
    return result;
  }
  ```
  
  
    
