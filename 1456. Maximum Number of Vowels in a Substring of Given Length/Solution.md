# 1456. Maximum Number of Vowels in a Substring of Given Length

## Problem Description

Given a string `s` and an integer `k`, return the maximum number of vowel letters in any substring of `s` with length `k`.

### Constraints:
1. `1 <= s.length <= 10^5`
2. `s` consists of lowercase English letters.
3. `1 <= k <= s.length`

---

## Solution Explanation

The solution uses a sliding window approach to find the maximum number of vowels in any substring of length `k`. The algorithm maintains a count of vowels in the current window and updates the maximum count as it slides the window across the string.

### Steps:
1. **Initialize the Vowel Count**: Count the number of vowels in the first `k` characters.
2. **Slide the Window**: Slide the window across the string, updating the vowel count and the maximum count.
3. **Return the Maximum Count**: Return the maximum number of vowels found in any substring of length `k`.

---

## Code Implementation

```cpp
class Solution {
public:
    bool isVowel(char c) {
        return c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u';
    }

    int maxVowels(string s, int k) {
        int n = s.size();
        int noOfV = 0;
        for (int i = 0; i < k; i++) {
            if (isVowel(s[i])) noOfV++;
        }
        int maxV = noOfV;
        for (int i = k; i < n; i++) {
            if (isVowel(s[i])) noOfV++;
            if (isVowel(s[i - k])) noOfV--;
            maxV = max(maxV, noOfV);
        }
        return maxV;
    }
};
```

---

## Algorithm Explanation

1. **Check if Character is Vowel**:
   - Define a helper function `isVowel` to check if a character is a vowel.

   ```cpp
   bool isVowel(char c) {
       return c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u';
   }
   ```

2. **Initialize the Vowel Count**:
   - Count the number of vowels in the first `k` characters.

   ```cpp
   int noOfV = 0;
   for (int i = 0; i < k; i++) {
       if (isVowel(s[i])) noOfV++;
   }
   ```

3. **Slide the Window**:
   - Slide the window across the string, updating the vowel count and the maximum count.

   ```cpp
   int maxV = noOfV;
   for (int i = k; i < n; i++) {
       if (isVowel(s[i])) noOfV++;
       if (isVowel(s[i - k])) noOfV--;
       maxV = max(maxV, noOfV);
   }
   ```

4. **Return the Maximum Count**:
   - Return the maximum number of vowels found in any substring of length `k`.

   ```cpp
   return maxV;
   ```

---

## Complexity Analysis

1. **Time Complexity**:
   - Counting the vowels in the first `k` characters takes \(O(k)\).
   - Sliding the window across the string takes \(O(n - k)\).
   - Thus, the total time complexity is \(O(n)\).

2. **Space Complexity**:
   - The solution uses a constant amount of extra space, so the space complexity is \(O(1)\).

---

## Example Usage

### Input
```cpp
string s = "abciiidef";
int k = 3;
```

### Output
```cpp
3
```

### Explanation
- The substring "iii" contains 3 vowels, which is the maximum number of vowels in any substring of length 3.

---

## Key Points

1. **Sliding Window Technique**:
   - The sliding window approach efficiently finds the maximum number of vowels by maintaining a running count of vowels in the current window.

2. **Optimal Time Complexity**:
   - The algorithm ensures \(O(n)\) time complexity, making it suitable for large inputs.

3. **In-Place Operation**:
   - The solution uses constant extra space, making it memory efficient.

---

## Edge Cases

1. **Single Character Substring**:
   - If `k = 1`, the maximum number of vowels is 1 if there is at least one vowel in the string.
   - Input: `"a"`, `k = 1` → Output: `1`

2. **No Vowels**:
   - If there are no vowels in the string, the output is 0.
   - Input: `"bcdfg"`, `k = 2` → Output: `0`

3. **All Vowels**:
   - If the string consists entirely of vowels, the output is `k`.
   - Input: `"aeiou"`, `k = 3` → Output: `3`

---