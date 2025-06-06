# Important Questions of DSA
## BASIC QUESTIONS:-
<br>

### 1. Find the Largest element in an array
<br>

#### ✨ Example 1:

**Input:**
<br>
 arr[] = {2,5,1,3,0};<br>
**Output:**
 5<br>
 
**Explanation:**
 5 is the largest element in the array. 

### ✨ Example 2:
**Input:**<br>
 arr[] = {8,10,5,7,9};<br>
**Output:**
 10<br>
 
**Explanation:**
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

<br>

___

### 2. Find Second Smallest and Second Largest Element in an array
<br>

### ✨ Example 1:

**Input:**

**arr[] = {1,2,4,7,7,5}**

**Output:**
<br>

**Second Smallest : 2**
<br>
**Second Largest : 5**

### Explanation:
 Since there is only one element in the array, it is the largest and smallest element present in the array. There is no second largest or second smallest element present.
 ```bash



#include<bits/stdc++.h>
using namespace std;
int secondSmallest(int arr[],int n)
{
    if(n<2)
        return -1;
    int small = INT_MAX;
    int second_small = INT_MAX;
    int i;
    for(i = 0; i < n; i++) 
    {
       if(arr[i] < small)
       {
          second_small = small;
          small = arr[i];
       }
       else if(arr[i] < second_small && arr[i] != small)
       {
          second_small = arr[i];
       }
    }
   return second_small;     
}
int secondLargest(int arr[],int n)
{
	if(n<2)
	return -1;
    int large=INT_MIN,second_large=INT_MIN;
    int i;
    for (i = 0; i < n; i++) 
    {
        if (arr[i] > large) 
        {
            second_large = large;
            large = arr[i];
        }
 
        else if (arr[i] > second_large && arr[i] != large) 
        {
            second_large = arr[i];
        }
    }
    return second_large;                
}

int main() {
    int arr[]={1,2,4,7,7,5};  
    int n=sizeof(arr)/sizeof(arr[0]);
        int sS=secondSmallest(arr,n);
        int sL=secondLargest(arr,n);
    cout<<"Second smallest is "<<sS<<endl;
    cout<<"Second largest is "<<sL<<endl;
    return 0;
}

```
**Time Complexity: O(N), Single-pass solution**

**Space Complexity: O(1)**

<br>

___

### 3. Remove Duplicates in-place from Sorted Array
<br>

**Problem Statement:**
Given an integer array sorted in non-decreasing order, remove the duplicates in place such that each unique element appears only once. The relative order of the elements should be kept the same.

If there are k elements after removing the duplicates, then the first k elements of the array should hold the final result. It does not matter what you leave beyond the first k elements.

**Note:** Return k after placing the final result in the first k slots of the array.

### ✨ Example 1:

**arr = {1,1,2,2,2,3,3}**

**Output:**

 **arr = [1,2,3,_,_,_,_,_]**
<br>

```bash


#include<bits/stdc++.h>

using namespace std;
int removeDuplicates(int arr[], int n)
{
  int i = 0;
  for (int j = 1; j < n; j++) {
    if (arr[i] != arr[j]) {
      i++;
      arr[i] = arr[j];
    }
  }
  return i + 1;
}
int main() {
  int arr[] = {1,1,2,2,2,3,3};
  int n = sizeof(arr)/sizeof(arr[0]);
  int k = removeDuplicates(arr, n);
  cout << "The array after removing duplicate elements is " << endl;
  for (int i = 0; i < k; i++) {
    cout << arr[i] << " ";
  }
}

```
**Complexity Analysis**

**Time Complexity: O(N)**

**Space Complexity: O(1)**
___

### 4. Sort an array of 0s, 1s and 2s
<br>

**Problem Statement:** Given an array consisting of only 0s, 1s, and 2s. Write a program to in-place sort the array without using inbuilt sort functions. ( Expected: Single pass-O(N) and constant space)
<br>

#### ✨ Example 1:

<br>

**Input:**
 **nums = [2,0,2,1,1,0]**
 <br>
 
**Output**
**: [0,0,1,1,2,2]**

```bash

#include <bits/stdc++.h>
using namespace std;

void sortArray(vector<int>& arr, int n) {

    int low = 0, mid = 0, high = n - 1; // 3 pointers

    while (mid <= high) {
        if (arr[mid] == 0) {
            swap(arr[low], arr[mid]);
            low++;
            mid++;
        }
        else if (arr[mid] == 1) {
            mid++;
        }
        else {
            swap(arr[mid], arr[high]);
            high--;
        }
    }
}

int main()
{
    int n = 6;
    vector<int> arr = {0, 2, 1, 2, 0, 1};
    sortArray(arr, n);
    cout << "After sorting:" << endl;
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
    return 0;
}

```

**Time Complexity: O(N), where N = size of the given array.**

<br>

**Reason: We are using a single loop that can run at most N times**
<br>

**Space Complexity: O(1) as we are not using any extra space.**


___

### 5. Stock Buy And Sell

<br>

**Problem Statement:** You are given an array of prices where prices[i] is the price of a given stock on an ith day.

<br>
You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock. Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

<br>

#### ✨ Example 1:

<br>

**Input:**
<br>

 **prices = [7,1,5,3,6,4]**

 <br>
 
**Output: 5**

<b>
Explanation:
 Buy on day 2 (price = 1) and 
sell on day 5 (price = 6), profit = 6-1 = 5.
</b>

<b>
	
**Note**
<b>: That buying on day 2 and selling on day 1 
is not allowed because you must buy before 
you sell.
</b>

<br>

```bash

#include<bits/stdc++.h>
using namespace std;

int maxProfit(vector<int> &arr) {
    int maxPro = 0;
    int n = arr.size();
    int minPrice = INT_MAX;

    for (int i = 0; i < arr.size(); i++) {
        minPrice = min(minPrice, arr[i]);
        maxPro = max(maxPro, arr[i] - minPrice);
    }
    
    return maxPro;
}

int main() {
    vector<int> arr = {7,1,5,3,6,4};
    int maxPro = maxProfit(arr);
    cout << "Max profit is: " << maxPro << endl;
}

```

**Complexity Analysis**

<br>

**Time complexity: O(n)**

<br>

**Space Complexity: O(1)**

___

<br>

### 6. Kadane's Algorithm : Maximum Subarray Sum in an Array
**Problem Statement: Given an integer array arr, find the contiguous subarray (containing at least one number) which
has the largest sum and returns its sum and prints the subarray.**
<br>
#### ✨ Example 1:

<br>

**Example 1:
Input:
 arr = [-2,1,-3,4,-1,2,1,-5,4]**

 <br>

**Output:
 6**
```bash

#include <bits/stdc++.h>
using namespace std;

long long maxSubarraySum(int arr[], int n) {
    long long maxi = LONG_MIN; // maximum sum
    long long sum = 0;

    for (int i = 0; i < n; i++) {

        sum += arr[i];

        if (sum > maxi) {
            maxi = sum;
        }

        // If sum < 0: discard the sum calculated
        if (sum < 0) {
            sum = 0;
        }
    }

    // To consider the sum of the empty subarray
    // uncomment the following check:

    //if (maxi < 0) maxi = 0;

    return maxi;
}

int main()
{
    int arr[] = { -2, 1, -3, 4, -1, 2, 1, -5, 4};
    int n = sizeof(arr) / sizeof(arr[0]);
    long long maxSum = maxSubarraySum(arr, n);
    cout << "The maximum subarray sum is: " << maxSum << endl;
    return 0;
}

```
**Time Complexity: O(N), where N = size of the array.
Reason: We are using a single loop running N times.**

**Space Complexity: O(1) as we are not using any extra space**

___

<br>

### 7. next_permutation : find next lexicographically greater permutation
<br>

**Problem Statement: Given an array Arr[] of integers, rearrange the numbers of the given array into the lexicographically next greater permutation of numbers.
If such an arrangement is not possible, it must rearrange to the lowest possible order (i.e., sorted in ascending order).**
<br>
#### ✨ Example 1:

<br>

**Input format:
 Arr[] = {1,3,2}**
 <br>
 
**Output
: Arr[] = {2,1,3}**
<br>

**Explanation: 
All permutations of {1,2,3} are {{1,2,3} , {1,3,2}, {2,13} , {2,3,1} , {3,1,2} , {3,2,1}}. So, the next permutation just after {1,3,2} is {2,1,3}.**

```bash

#include <bits/stdc++.h>
using namespace std;

vector<int> nextGreaterPermutation(vector<int> &A) {
    int n = A.size(); // size of the array.

    // Step 1: Find the break point:
    int ind = -1; // break point
    for (int i = n - 2; i >= 0; i--) {
        if (A[i] < A[i + 1]) {
            // index i is the break point
            ind = i;
            break;
        }
    }

    // If break point does not exist:
    if (ind == -1) {
        // reverse the whole array:
        reverse(A.begin(), A.end());
        return A;
    }

    // Step 2: Find the next greater element
    //         and swap it with arr[ind]:

    for (int i = n - 1; i > ind; i--) {
        if (A[i] > A[ind]) {
            swap(A[i], A[ind]);
            break;
        }
    }

    // Step 3: reverse the right half:
    reverse(A.begin() + ind + 1, A.end());

    return A;
}

int main()
{
    vector<int> A = {2, 1, 5, 4, 3, 0, 0};
    vector<int> ans = nextGreaterPermutation(A);

    cout << "The next permutation is: [";
    for (auto it : ans) {
        cout << it << " ";
    }
    cout << "]n";
    return 0;
}

```

**Time Complexity: O(3N), where N = size of the given array
Finding the break-point, finding the next greater element, and reversal at the end takes O(N) for each, where N is the number of elements in the input array. This sums up to 3*O(N) which is approximately O(3N).**

<br>

**Space Complexity: Since no extra storage is required. Thus, its space complexity is O(1).**

___

### 3 Sum : Find triplets that add up to a zero
<br>
**Problem Statement:** Given an array of N integers, your task is to find unique triplets that add up to give a sum of zero. In short, you need to return an array of all the unique triplets [arr[a], arr[b], arr[c]] such that i!=j, j!=k, k!=i, and their sum is equal to zero.

<br>

<br>

#### ✨Example 1:

<br>

**Input
 nums = [-1,0,1,2,-1,-4]**
 <br>

**Output:
 [[-1,-1,2],[-1,0,1]]**

 <br>
 
 **Explanation:**
 <br>
 
 **Out of all possible unique triplets possible, [-1,-1,2] and [-1,0,1] satisfy the condition of summing up to zero with i!=j!=k**
 <br>
 
 ```bash



#include <bits/stdc++.h>
using namespace std;

vector<vector<int>> triplet(int n, vector<int> &arr) {
    vector<vector<int>> ans;
    sort(arr.begin(), arr.end());
    for (int i = 0; i < n; i++) {
        //remove duplicates:
        if (i != 0 && arr[i] == arr[i - 1]) continue;

        //moving 2 pointers:
        int j = i + 1;
        int k = n - 1;
        while (j < k) {
            int sum = arr[i] + arr[j] + arr[k];
            if (sum < 0) {
                j++;
            }
            else if (sum > 0) {
                k--;
            }
            else {
                vector<int> temp = {arr[i], arr[j], arr[k]};
                ans.push_back(temp);
                j++;
                k--;
                //skip the duplicates:
                while (j < k && arr[j] == arr[j - 1]) j++;
                while (j < k && arr[k] == arr[k + 1]) k--;
            }
        }
    }
    return ans;
}


int main()
{
    vector<int> arr = { -1, 0, 1, 2, -1, -4};
    int n = arr.size();
    vector<vector<int>> ans = triplet(n, arr);
    for (auto it : ans) {
        cout << "[";
        for (auto i : it) {
            cout << i << " ";
        }
        cout << "] ";
    }
    cout << "\n";
    return 0;
}

```
<br>

**Time Complexity: O(NlogN)+O(N2), where N = size of the array.
Reason: The pointer i, is running for approximately N times. And both the pointers j and k combined can run for approximately N times including the operation of skipping duplicates. So the total time complexity will be O(N2).** 

**Space Complexity: O(no. of quadruplets), This space is only used to store the answer. We are not using any extra space to solve this problem. So, from that perspective, space complexity can be written as O(1).**

### 8.Majority Element-I
**Given an integer array nums of size n, return the majority element of the array.**

**The majority element of an array is an element that appears more than n/2 times in the array. The array is guaranteed to have a majority element.**

<br>

#### ✨Example 1:

<br>

**Input: nums = [7, 0, 0, 1, 7, 7, 2, 7, 7]**

<br>

**Output: 7**

<br>

**Explanation: The number 7 appears 5 times in the 9 sized array**

```
 class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int n = nums.size();
        unordered_map<int, int> m;

        for(int i = 0; i<n; i++){
            m[nums[i]]++;
          
        }
        n= n/2;
        for(auto it: m){
            if(it.second > n){
                return it.first;
            }
        }
        return 0;

        }
        
    
};
```




