# 643. Maximum Average Subarray I

## Problem Description

Given an array `nums` consisting of `n` integers, find a contiguous subarray whose length is equal to `k` that has the maximum average value and return this value.

### Constraints:
1. `1 <= k <= n <= 30,000`
2. The elements of `nums` are in the range `[-10,000, 10,000]`.

---

## Solution Explanation

The solution uses a sliding window approach to find the maximum average of any subarray of length `k`. The algorithm maintains a running sum of the current window and updates the maximum average as it slides the window across the array.

### Steps:
1. **Initialize the Sum**: Calculate the sum of the first `k` elements.
2. **Calculate Initial Average**: Compute the average of the first `k` elements.
3. **Slide the Window**: Slide the window across the array, updating the sum and the maximum average.
4. **Return the Maximum Average**: Return the maximum average found.

---

## Code Implementation

```cpp
class Solution {
public:
    double findMaxAverage(vector<int>& nums, int k) {
        int n = nums.size();
        double sum = 0;
        for (int i = 0; i < k; i++) {
            sum += nums[i];
        }
        double ans = sum / k;

        for (int i = k; i < n; i++) {
            sum += nums[i] - nums[i - k];
            ans = max(ans, sum / k);
        }
        return ans;
    }
};
```

---

## Algorithm Explanation

1. **Initialize the Sum**:
   - Calculate the sum of the first `k` elements.

   ```cpp
   double sum = 0;
   for (int i = 0; i < k; i++) {
       sum += nums[i];
   }
   ```

2. **Calculate Initial Average**:
   - Compute the average of the first `k` elements.

   ```cpp
   double ans = sum / k;
   ```

3. **Slide the Window**:
   - Slide the window across the array, updating the sum and the maximum average.

   ```cpp
   for (int i = k; i < n; i++) {
       sum += nums[i] - nums[i - k];
       ans = max(ans, sum / k);
   }
   ```

4. **Return the Maximum Average**:
   - Return the maximum average found.

   ```cpp
   return ans;
   ```

---

## Complexity Analysis

1. **Time Complexity**:
   - Calculating the initial sum takes \(O(k)\).
   - Sliding the window across the array takes \(O(n - k)\).
   - Thus, the total time complexity is \(O(n)\).

2. **Space Complexity**:
   - The solution uses a constant amount of extra space, so the space complexity is \(O(1)\).

---

## Example Usage

### Input
```cpp
vector<int> nums = {1, 12, -5, -6, 50, 3};
int k = 4;
```

### Output
```cpp
12.75
```

### Explanation
- The subarray with the maximum average is `[12, -5, -6, 50]`.
- The average is \((12 + (-5) + (-6) + 50) / 4 = 12.75\).

---

## Key Points

1. **Sliding Window Technique**:
   - The sliding window approach efficiently finds the maximum average by maintaining a running sum of the current window.

2. **Optimal Time Complexity**:
   - The algorithm ensures \(O(n)\) time complexity, making it suitable for large inputs.

3. **In-Place Operation**:
   - The solution uses constant extra space, making it memory efficient.

---

## Edge Cases

1. **Single Element Subarray**:
   - If `k = 1`, the maximum average is the maximum element in the array.
   - Input: `[1, 2, 3, 4]`, `k = 1` → Output: `4.0`

2. **All Elements Are the Same**:
   - If all elements are the same, the average is the same as any element.
   - Input: `[5, 5, 5, 5]`, `k = 2` → Output: `5.0`

3. **Negative Elements**:
   - The algorithm handles negative elements correctly.
   - Input: `[-1, -2, -3, -4]`, `k = 2` → Output: `-1.5`

---