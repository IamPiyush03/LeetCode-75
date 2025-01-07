# 11. Container With Most Water

## Problem Description

Given `n` non-negative integers `height` where each represents a point at coordinate `(i, height[i])`, `n` vertical lines are drawn such that the two endpoints of the line `i` are at `(i, 0)` and `(i, height[i])`. Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return the maximum amount of water a container can store.

### Constraints:
1. `n` is at least 2.
2. The height of each line is a non-negative integer.

---

## Solution Explanation

The solution uses a two-pointer approach to find the maximum area of water that can be contained. The algorithm starts with two pointers, one at the beginning and one at the end of the array, and iteratively moves the pointers towards each other to find the maximum area.

### Steps:
1. **Initialize Pointers**: Start with two pointers, `i` at the beginning (index 0) and `j` at the end (index `n-1`) of the array.
2. **Calculate Area**: Calculate the area formed by the lines at the two pointers and update the maximum area if the current area is larger.
3. **Move Pointers**: Move the pointer pointing to the shorter line towards the other pointer to potentially find a larger area.
4. **Repeat**: Continue the process until the two pointers meet.

---

## Code Implementation

```cpp
class Solution {
public:
    int maxArea(vector<int>& height) {
        int n = height.size();
        if (n <= 1) return 0;
        int i = 0;
        int j = n - 1;
        int area = 0;
        while (i < j) {
            area = max(area, (j - i) * min(height[i], height[j]));
            if (height[i] < height[j]) i++;
            else j--;
        }
        return area;
    }
};
```

---

## Algorithm Explanation

1. **Initialize Variables**:
   - `i`: Pointer starting at the beginning of the array.
   - `j`: Pointer starting at the end of the array.
   - `area`: Variable to store the maximum area found.

2. **Calculate Area**:
   - Calculate the area using the formula `(j - i) * min(height[i], height[j])`.
   - Update `area` if the calculated area is larger than the current `area`.

3. **Move Pointers**:
   - If `height[i]` is less than `height[j]`, increment `i` to potentially find a taller line.
   - Otherwise, decrement `j` to potentially find a taller line.

4. **Return Result**:
   - Return the maximum area found.

---

## Complexity Analysis

1. **Time Complexity**:
   - The solution involves a single traversal of the array with two pointers, so the time complexity is \(O(n)\), where \(n\) is the size of the array.

2. **Space Complexity**:
   - The solution uses a constant amount of extra space, so the space complexity is \(O(1)\).

---

## Example Usage

### Example 1

#### Input
```cpp
vector<int> height = {1, 8, 6, 2, 5, 4, 8, 3, 7};
```

#### Output
```cpp
49
```

#### Explanation
- The maximum area is formed between the lines at index 1 and index 8, with height 8 and 7 respectively.
- Area = (8 - 1) * min(8, 7) = 7 * 7 = 49.

---

### Example 2

#### Input
```cpp
vector<int> height = {1, 1};
```

#### Output
```cpp
1
```

#### Explanation
- The maximum area is formed between the lines at index 0 and index 1, both with height 1.
- Area = (1 - 0) * min(1, 1) = 1 * 1 = 1.

---

## Edge Cases

1. **Minimum Input Size**:
   - Input: `height = {1, 2}`
   - Output: `1`
   - Explanation: The only possible container is formed by the two lines.

2. **All Lines of Equal Height**:
   - Input: `height = {3, 3, 3, 3}`
   - Output: `9`
   - Explanation: The maximum area is formed by the lines at the two ends.

3. **Decreasing Heights**:
   - Input: `height = {5, 4, 3, 2, 1}`
   - Output: `6`
   - Explanation: The maximum area is formed by the lines at index 0 and index 2.

---

## Key Points

1. **Two-Pointer Technique**:
   - The two-pointer approach efficiently finds the maximum area by considering all possible containers formed by the lines.

2. **Optimal Time Complexity**:
   - The algorithm ensures \(O(n)\) time complexity, making it suitable for large inputs.

3. **In-Place Operation**:
   - The solution uses constant extra space, making it memory efficient.

---

## Conclusion

The two-pointer approach provides an efficient and optimal solution to the "Container With Most Water" problem, ensuring both time and space efficiency. The algorithm effectively finds the maximum area by iteratively adjusting the pointers based on the heights of the lines.