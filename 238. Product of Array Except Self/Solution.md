
---

# 238. Product of Array Except Self

## Problem Description

Given an integer array `nums`, return an array `answer` such that `answer[i]` is equal to the product of all elements of `nums` except `nums[i]`.  

### Constraints:
1. You must solve the problem without using division.
2. The algorithm must run in \(O(n)\) time.

---

## Solution Explanation

To solve the problem, the algorithm calculates the product of all elements except the current one using **prefix** and **suffix** products.  

### Key Observations:
- The product of all elements except `nums[i]` can be expressed as the product of:
  - All elements **before** `nums[i]` (prefix).
  - All elements **after** `nums[i]` (suffix).

### Steps:
1. Use a single array `pre` to store the intermediate results:
   - Initially, `pre` is populated with the prefix products.
   - Then, it is updated with the suffix products to compute the final result.
2. Avoid using extra space for suffix products by directly multiplying the prefix product in reverse order.

---

## Code Implementation

```cpp
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int n = nums.size();
        vector<int> pre(n);  // Array to store prefix products and final result

        // Initialize prefix product
        int p = nums[0];
        pre[0] = 1;  // First element has no prefix product
        for (int i = 1; i < n; i++) {
            pre[i] = p;  // Store the prefix product
            p *= nums[i];
        }

        // Calculate suffix product and multiply with prefix product
        p = nums[n - 1];
        for (int i = n - 2; i >= 0; i--) {
            pre[i] *= p;  // Multiply prefix with suffix
            p *= nums[i];
        }

        return pre;
    }
};
```

---

## Algorithm Explanation

1. **Prefix Product Array**:
   - Traverse the array from left to right.
   - For each index \(i\), compute the product of all elements before \(i\) and store it in `pre[i]`.
   - Start with `pre[0] = 1` since there is no prefix product for the first element.

2. **Suffix Product Calculation**:
   - Traverse the array from right to left.
   - For each index \(i\), multiply the current value of `pre[i]` (prefix product) by the suffix product.
   - Update the suffix product during traversal.

3. **Return Result**:
   - The array `pre` now contains the product of all elements except the one at each index.

---

## Complexity Analysis

1. **Time Complexity**:  
   - The solution involves two traversals of the array (one for prefix and one for suffix), so the time complexity is \(O(n)\).

2. **Space Complexity**:  
   - The solution uses the `pre` array of size \(n\), so the space complexity is \(O(n)\).  
   - Note: If the output array is reused (e.g., by modifying `nums`), space complexity can be reduced to \(O(1)\) additional space.

---

## Example Usage

### Example 1

#### Input
```cpp
vector<int> nums = {1, 2, 3, 4};
```

#### Output
```cpp
{24, 12, 8, 6}
```

#### Explanation
- For \(nums[0]\): Product of all elements except \(1\) → \(2 \times 3 \times 4 = 24\).  
- For \(nums[1]\): Product of all elements except \(2\) → \(1 \times 3 \times 4 = 12\).  
- For \(nums[2]\): Product of all elements except \(3\) → \(1 \times 2 \times 4 = 8\).  
- For \(nums[3]\): Product of all elements except \(4\) → \(1 \times 2 \times 3 = 6\).  

---

### Example 2

#### Input
```cpp
vector<int> nums = {-1, 1, 0, -3, 3};
```

#### Output
```cpp
{0, 0, 9, 0, 0}
```

#### Explanation
- For \(nums[2]\), the result is \(1 \times (-1) \times (-3) \times 3 = 9\).  
- Other elements result in \(0\) due to multiplication with \(0\).

---

## Edge Cases

1. **Array with Single Element**:  
   Input: `nums = [5]`  
   Output: `{1}`  
   Explanation: There are no other elements to multiply.

2. **Array with Zeros**:  
   Input: `nums = [0, 4, 0]`  
   Output: `{0, 0, 0}`  
   Explanation: Any product involving \(0\) results in \(0\).

3. **Negative Numbers**:  
   Input: `nums = [-1, -2, -3]`  
   Output: `{6, 3, 2}`  
   Explanation: The algorithm handles negative numbers correctly.

---

## Key Points

1. **No Division**:  
   The solution avoids using division to meet the problem constraints.

2. **Optimal Time Complexity**:  
   The algorithm processes the input in \(O(n)\) time.

3. **Single Output Array**:  
   Both prefix and suffix products are combined in a single array to save space.

---

