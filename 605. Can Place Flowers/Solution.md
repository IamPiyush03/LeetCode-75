
---

# 605. Can Place Flowers

## Problem Description

You are given a vector `flowerbed` representing a row of flowerbeds where `flowerbed[i]` is `1` if there is a flower planted in the \(i\)-th position and `0` if it is empty.  
You are also given an integer `n`, representing the number of flowers you need to plant.  
Flowers cannot be planted in adjacent positions.  

Return `true` if it is possible to plant all `n` flowers in the flowerbed without violating the adjacency rule; otherwise, return `false`.

---

## Solution Explanation

The solution iterates through the flowerbed and checks each position to see if a flower can be planted. The conditions for planting a flower at position \(i\) are:  
1. The position \(i\) is empty (`flowerbed[i] == 0`).  
2. The left neighbor (\(i-1\)) is either empty or does not exist.  
3. The right neighbor (\(i+1\)) is either empty or does not exist.  

If all conditions are satisfied, a flower is planted at \(i\), and \(n\) is decremented. If \(n\) reaches \(0\), return `true`. If the loop ends and \(n > 0\), return `false`.

---

## Code Implementation

```cpp
class Solution {
public:
    bool canPlaceFlowers(vector<int>& flowerbed, int n) {
        // If no flowers need to be planted, return true
        if (n == 0) return true;

        int s = flowerbed.size();

        // Iterate through the flowerbed
        for (int i = 0; i < s; i++) {
            // Check if current position is empty
            if (flowerbed[i] == 0) {
                // Check left and right neighbors
                bool left = (i == 0 || flowerbed[i - 1] == 0);
                bool right = (i == s - 1 || flowerbed[i + 1] == 0);

                // If both neighbors are empty, plant a flower
                if (left && right) {
                    flowerbed[i] = 1;
                    n--;

                    // If all flowers are planted, return true
                    if (n == 0) return true;
                }
            }
        }

        // If not all flowers could be planted, return false
        return false;
    }
};
```

---

## Algorithm Explanation

1. **Edge Case**:  
   If \(n = 0\), no flowers need to be planted, so return `true`.

2. **Iterate Through the Flowerbed**:  
   For each position \(i\):
   - Check if it is empty (`flowerbed[i] == 0`).
   - Check if the left neighbor (\(i-1\)) is either empty or does not exist (`i == 0 || flowerbed[i-1] == 0`).
   - Check if the right neighbor (\(i+1\)) is either empty or does not exist (`i == s-1 || flowerbed[i+1] == 0`).

3. **Plant a Flower**:  
   If the above conditions are satisfied:
   - Plant a flower at position \(i\) (`flowerbed[i] = 1`).
   - Decrement \(n\).
   - If \(n = 0\), return `true`.

4. **Return the Result**:  
   If the loop ends and \(n > 0\), return `false`.

---

## Complexity Analysis

1. **Time Complexity**:  
   - The solution iterates through the flowerbed once, making the time complexity \(O(s)\), where \(s\) is the size of the flowerbed.

2. **Space Complexity**:  
   - The solution uses the input `flowerbed` array to modify the state, so the space complexity is \(O(1)\).

---

## Example Usage

### Example 1

#### Input
```cpp
vector<int> flowerbed = {1, 0, 0, 0, 1};
int n = 1;
```

#### Output
```cpp
true
```

#### Explanation
- Position 2 is empty and satisfies the conditions (both neighbors are empty). A flower is planted at position 2.
- \(n = 0\), so the result is `true`.

---

### Example 2

#### Input
```cpp
vector<int> flowerbed = {1, 0, 0, 0, 1};
int n = 2;
```

#### Output
```cpp
false
```

#### Explanation
- Only one flower can be planted (at position 2). \(n = 1\) remains, so the result is `false`.

---

### Example 3

#### Input
```cpp
vector<int> flowerbed = {0, 0, 1, 0, 0};
int n = 2;
```

#### Output
```cpp
true
```

#### Explanation
- Flowers can be planted at positions 0 and 4. \(n = 0\), so the result is `true`.

---

## Edge Cases

1. **Empty Flowerbed**:  
   If `flowerbed` is empty, no flowers can be planted.  
   Input: `flowerbed = {}`, \(n = 1\) → Output: `false`.

2. **Single Empty Plot**:  
   If `flowerbed` has one plot and it is empty, one flower can be planted.  
   Input: `flowerbed = {0}`, \(n = 1\) → Output: `true`.

3. **No Need to Plant**:  
   If \(n = 0\), return `true` regardless of the flowerbed.  
   Input: `flowerbed = {1, 0, 0, 1}`, \(n = 0\) → Output: `true`.

---

## Key Points

1. The solution modifies the input `flowerbed` array, reducing space complexity.
2. It efficiently handles edge cases such as single plots or \(n = 0\).
3. The algorithm ensures \(O(s)\) time complexity, making it suitable for large inputs.

--- 

