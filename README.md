# Important Questions of DSA
## BASIC QUESTIONS:-
<br>

### 1. Find the Largest element in an array
<br>

#### ✨ Example 1:

**Input:**
 arr[] = {2,5,1,3,0};
**Output:**
 5
Explanation:
 5 is the largest element in the array. 

#### ✨ Example 2:
**Input:**
 arr[] = {8,10,5,7,9};
**Output:*
 10
Explanation:
 10 is the largest element in the array.

```bash
    
#include <bits/stdc++.h>
 
using namespace std;
int findLargestElement(int arr[], int n) {
 
  int max = arr[0];
  for (int i = 0; i < n; i++) {
    if (max < arr[i]) {
      max = arr[i];
    }
  }
  return max;
}
int main() {
  int arr1[] = {2,5,1,3,0};
  int n = 5;
  int max = findLargestElement(arr1, n);
  cout << "The largest element in the array is: " << max << endl;
 
  int arr2[] =  {8,10,5,7,9};
  n = 5;
  max = findLargestElement(arr2, n);
  cout << "The largest element in the array is: " << max<<endl;
  return 0;
}

```
#### ✨ Complexity Analysis:

**Time Complexity:** O(N), where N is the size of the array (as we traverse the array once).

**Space Complexity:** O(1), as we use a constant amount of extra space.


### 2. Find Second Smallest and Second Largest Element in an array



