# 1679. Max Number of K-Sum Pairs

## Problem Description

Given an array `nums` and an integer `k`, return the maximum number of operations you can perform on the array. In one operation, you can pick two numbers from the array whose sum equals `k` and remove them from the array.

### Constraints:
1. Each element in the array can only be used once in each operation.
2. The array can contain both positive and negative integers.

---

## Solution Explanation

The solution uses a two-pointer approach to find the maximum number of pairs that sum up to `k`. The algorithm sorts the array and then uses two pointers to find valid pairs.

### Steps:
1. **Sort the Array**: Sort the array to facilitate the two-pointer approach.
2. **Initialize Pointers**: Start with two pointers, `i` at the beginning (index 0) and `j` at the end (index `n-1`) of the array.
3. **Find Pairs**: Move the pointers towards each other to find pairs that sum up to `k`.
4. **Count Valid Pairs**: Increment the count of valid pairs whenever a pair is found.
5. **Adjust Pointers**: Move the pointers based on the sum of the elements at the pointers.

---

## Code Implementation

```cpp
class Solution {
public:
    int maxOperations(vector<int>& nums, int k) {
        sort(nums.begin(), nums.end());
        int n = nums.size();
        int i = 0;
        int j = n - 1;
        int ans = 0;
        while (i < j) {
            if (nums[i] + nums[j] == k) {
                ans++;
                i++;
                j--;
            } else if (nums[i] + nums[j] < k) {
                i++;
            } else {
                j--;
            }
        }
        return ans;
    }
};
```

---

## Algorithm Explanation

1. **Sort the Array**:
   - Sorting the array helps in efficiently finding pairs using the two-pointer technique.

   ```cpp
   sort(nums.begin(), nums.end());
   ```

2. **Initialize Pointers**:
   - `i` starts at the beginning of the array.
   - `j` starts at the end of the array.

3. **Find Pairs**:
   - Use a while loop to iterate until the two pointers meet.
   - If the sum of the elements at `i` and `j` equals `k`, increment the count and move both pointers.
   - If the sum is less than `k`, move the left pointer `i` to the right.
   - If the sum is greater than `k`, move the right pointer `j` to the left.

   ```cpp
   if (nums[i] + nums[j] == k) {
       ans++;
       i++;
       j--;
   } else if (nums[i] + nums[j] < k) {
       i++;
   } else {
       j--;
   }
   ```

4. **Return Result**:
   - Return the count of valid pairs.

---

## Complexity Analysis

1. **Time Complexity**:
   - Sorting the array takes \(O(n \log n)\), where \(n\) is the size of the array.
   - Finding pairs using the two-pointer technique takes \(O(n)\).
   - Thus, the total time complexity is \(O(n \log n)\).

2. **Space Complexity**:
   - The solution uses a constant amount of extra space, so the space complexity is \(O(1)\).

---

## Example Usage

### Input
```cpp
vector<int> nums = {1, 2, 3, 4};
int k = 5;
```

### Output
```cpp
2
```

### Explanation
- The pairs (1, 4) and (2, 3) sum up to 5.
- Thus, the maximum number of operations is 2.

---

## Key Points

1. **Two-Pointer Technique**:
   - The two-pointer approach efficiently finds pairs that sum up to `k` after sorting the array.

2. **Optimal Time Complexity**:
   - The algorithm ensures \(O(n \log n)\) time complexity due to sorting, which is efficient for this problem.

3. **In-Place Operation**:
   - The solution uses constant extra space, making it memory efficient.

---

## Edge Cases

1. **No Valid Pairs**:
   - If no pairs sum up to `k`, the output is 0.
   - Input: `[1, 2, 3, 4]`, `k = 10` → Output: `0`

2. **All Elements Form Pairs**:
   - If all elements can form pairs that sum up to `k`, the output is `n/2`.
   - Input: `[1, 1, 1, 1]`, `k = 2` → Output: `2`

3. **Single Element**:
   - If the array has only one element, no pairs can be formed.
   - Input: `[1]`, `k = 2` → Output: `0`

---