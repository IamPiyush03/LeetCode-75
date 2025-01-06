
---

# 1431. Kids With the Greatest Number of Candies

## Problem Description

Given the array `candies` where each element represents the number of candies a child has, and an integer `extraCandies`, determine if giving the `extraCandies` to each child would make their candy count equal to or greater than the greatest candy count among all the children.

Return a boolean array `ans` where `ans[i]` is `true` if, after giving the `extraCandies` to the `i-th` child, they have the greatest number of candies among all children, or `false` otherwise.

---

## Solution Explanation

The solution involves the following steps:

1. **Determine the Current Maximum**:  
   Identify the maximum number of candies any child currently has.

2. **Iterate Through Each Child**:  
   For each child, check if their candy count, after adding the `extraCandies`, is greater than or equal to the current maximum.

3. **Build the Result**:  
   Return a vector of booleans representing whether each child can have the greatest number of candies.

---

## Code Implementation

```cpp
class Solution {
public:
    vector<bool> kidsWithCandies(vector<int>& candies, int extraCandies) {
        // Number of children
        int n = candies.size();

        // Find the maximum number of candies among all children
        int maxCandies = *max_element(candies.begin(), candies.end());

        // Initialize the result vector
        vector<bool> ans(n);

        // Iterate through each child and check if they can have the greatest number of candies
        for (int i = 0; i < n; i++) {
            ans[i] = (candies[i] + extraCandies >= maxCandies);
        }

        return ans;
    }
};
```

---

## Algorithm Explanation

1. **Find the Maximum Candies**:  
   Use the `max_element` function to find the maximum number of candies in the input array. This step helps identify the threshold for comparison.

   ```cpp
   int maxCandies = *max_element(candies.begin(), candies.end());
   ```

2. **Check Each Child**:  
   For each child, add `extraCandies` to their current candy count and check if it is greater than or equal to `maxCandies`.

   ```cpp
   ans[i] = (candies[i] + extraCandies >= maxCandies);
   ```

3. **Store the Result**:  
   Populate the `ans` vector with `true` or `false` based on the comparison.

4. **Return the Result**:  
   Finally, return the `ans` vector.

---

## Complexity Analysis

1. **Time Complexity**:  
   - Finding the maximum element takes \(O(n)\), where \(n\) is the size of the `candies` array.  
   - Iterating through the array to compute the result also takes \(O(n)\).  
   - Thus, the total time complexity is \(O(n)\).

2. **Space Complexity**:  
   - The solution uses an additional vector `ans` of size \(n\) to store the results.  
   - The space complexity is \(O(n)\).

---

## Example Usage

### Input
```cpp
vector<int> candies = {2, 3, 5, 1, 3};
int extraCandies = 3;
```

### Output
```cpp
vector<bool> ans = {true, true, true, false, true};
```

### Explanation
1. The maximum candies initially are 5.  
2. After adding `extraCandies`:
   - Child 1: \(2 + 3 = 5 \geq 5\) → `true`
   - Child 2: \(3 + 3 = 6 \geq 5\) → `true`
   - Child 3: \(5 + 3 = 8 \geq 5\) → `true`
   - Child 4: \(1 + 3 = 4 < 5\) → `false`
   - Child 5: \(3 + 3 = 6 \geq 5\) → `true`

---

## Key Points

1. This solution avoids unnecessary sorting of the array, making it more efficient.
2. The use of `max_element` simplifies finding the current maximum candies.
3. The algorithm ensures \(O(n)\) time complexity, which is optimal for this problem.

---

## Edge Cases

1. **Single Child**:  
   If there is only one child, they will always have the greatest number of candies after adding `extraCandies`.  
   Input: `[5]`, `extraCandies = 3` → Output: `[true]`

2. **All Children Have Equal Candies**:  
   If all children have the same number of candies, they will all have the greatest number of candies after adding `extraCandies`.  
   Input: `[4, 4, 4]`, `extraCandies = 2` → Output: `[true, true, true]`

3. **No Extra Candies**:  
   If `extraCandies = 0`, the output depends only on the current candy count.  
   Input: `[1, 2, 3]`, `extraCandies = 0` → Output: `[false, false, true]`

---
