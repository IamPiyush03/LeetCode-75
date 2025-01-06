
---

# 283 Move Zeroes

## Problem Description

Given an integer array `nums`, move all `0`s to the end of the array while maintaining the relative order of the non-zero elements.  

You must perform the operation **in-place** without making a copy of the array.

---

## Solution Explanation

The solution uses a two-pointer approach to move all non-zero elements to the front of the array, while shifting the zeroes to the end. The algorithm ensures the relative order of non-zero elements is preserved.

### Steps:
1. Use two pointers, `i` and `j`:
   - `i`: Tracks the position to place the next non-zero element.
   - `j`: Iterates through the array.
2. Traverse the array:
   - If `nums[j]` is non-zero, swap it with `nums[i]` and increment both `i` and `j`.
   - If `nums[j]` is zero, increment only `j`.
3. This ensures all non-zero elements are moved to the beginning, and all zeroes are shifted to the end.

---

## Code Implementation

```cpp
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int n = nums.size();
        int i = 0; // Pointer for non-zero placement
        int j = 0; // Pointer for traversal

        // Traverse the array
        while (j < n) {
            if (nums[j] != 0) {
                // Swap non-zero element to the position at i
                swap(nums[i], nums[j]);
                i++;
            }
            j++;
        }
    }
};
```

---

## Algorithm Explanation

1. **Initialization**:
   - Set `i` and `j` to `0`.
   - `i` keeps track of where the next non-zero element should go.

2. **Traverse Array**:
   - If `nums[j]` is non-zero, swap `nums[i]` and `nums[j]`, then increment `i` and `j`.
   - If `nums[j]` is zero, simply increment `j` to continue scanning.

3. **In-Place Operation**:
   - The swaps ensure the operation is performed in-place, with no additional space used for another array.

---

## Complexity Analysis

1. **Time Complexity**:  
   - The solution involves a single traversal of the array, so the time complexity is \(O(n)\), where \(n\) is the size of the array.

2. **Space Complexity**:  
   - Since the operation is done in-place without using extra space, the space complexity is \(O(1)\).

---

## Example Usage

### Example 1

#### Input
```cpp
vector<int> nums = {0, 1, 0, 3, 12};
```

#### Output
```cpp
{1, 3, 12, 0, 0}
```

#### Explanation
- Non-zero elements (`1`, `3`, `12`) are moved to the front.
- Zeroes are shifted to the end.

---

### Example 2

#### Input
```cpp
vector<int> nums = {0};
```

#### Output
```cpp
{0}
```

#### Explanation
- The array contains only one zero, so the output remains the same.

---

## Edge Cases

1. **All Zeroes**:
   - Input: `nums = {0, 0, 0}`
   - Output: `{0, 0, 0}`
   - Explanation: The array is already in the desired form.

2. **No Zeroes**:
   - Input: `nums = {1, 2, 3}`
   - Output: `{1, 2, 3}`
   - Explanation: The array remains unchanged as there are no zeroes.

3. **Mixed Elements**:
   - Input: `nums = {4, 2, 0, 0, 5, 0, 6}`
   - Output: `{4, 2, 5, 6, 0, 0, 0}`
   - Explanation: Non-zero elements maintain their relative order, and zeroes are shifted to the end.

---

## Key Points

1. **In-Place Operation**:
   - The algorithm performs swaps in-place, making it memory efficient.

2. **Maintains Order**:
   - The relative order of non-zero elements is preserved.

3. **Optimal Performance**:
   - Time complexity is \(O(n)\), which is the best achievable for this problem.

---
