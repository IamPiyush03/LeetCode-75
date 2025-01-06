
---

# 1768. Merge Strings Alternately

## Problem Description

You are given two strings, `word1` and `word2`. You need to merge these strings alternately by taking characters from each string one by one. If one string is longer than the other, append the remaining characters from the longer string to the result.

Return the merged string.

---

## Solution Explanation

The solution iterates through both strings, merging them alternately until one of the strings is exhausted. If one string is longer, its remaining characters are appended to the result.

---

## Code Implementation

```cpp
class Solution {
public:
    string mergeAlternately(string word1, string word2) {
        string ans;
        int i = 0, j = 0;

        // Merge characters alternately from word1 and word2
        while (i < word1.size() && j < word2.size()) {
            ans += word1[i++];
            ans += word2[j++];
        }

        // Append remaining characters from word1 (if any)
        while (i < word1.size()) {
            ans += word1[i++];
        }

        // Append remaining characters from word2 (if any)
        while (j < word2.size()) {
            ans += word2[j++];
        }

        return ans;
    }
};
```

---

## Algorithm Explanation

1. **Initialize Pointers and Result String**:  
   Use two pointers `i` and `j` to iterate through `word1` and `word2`, respectively. Initialize an empty string `ans` to store the merged result.

2. **Merge Characters Alternately**:  
   While both strings have characters left:
   - Append the character from `word1` at position `i` to `ans`.
   - Append the character from `word2` at position `j` to `ans`.
   - Increment both `i` and `j`.

3. **Handle Remaining Characters**:  
   If `word1` has remaining characters, append them to `ans`. Similarly, if `word2` has remaining characters, append them to `ans`.

4. **Return the Result**:  
   Return the merged string `ans`.

---

## Complexity Analysis

1. **Time Complexity**:  
   - The algorithm iterates through both strings exactly once.  
   - The time complexity is \(O(\text{max}(m, n))\), where \(m\) and \(n\) are the lengths of `word1` and `word2`, respectively.

2. **Space Complexity**:  
   - The solution uses a string `ans` to store the result.  
   - The space complexity is \(O(m + n)\), where \(m + n\) is the total length of the merged string.

---

## Example Usage

### Example 1

#### Input
```cpp
string word1 = "abc";
string word2 = "pqr";
```

#### Output
```cpp
"apbqcr"
```

#### Explanation
- Merge "a" from `word1` and "p" from `word2`.  
- Merge "b" from `word1` and "q" from `word2`.  
- Merge "c" from `word1` and "r" from `word2`.  

### Example 2

#### Input
```cpp
string word1 = "ab";
string word2 = "pqrs";
```

#### Output
```cpp
"apbqrs"
```

#### Explanation
- Merge "a" from `word1` and "p" from `word2`.  
- Merge "b" from `word1` and "q" from `word2`.  
- Append the remaining characters "rs" from `word2`.

### Example 3

#### Input
```cpp
string word1 = "abcd";
string word2 = "pq";
```

#### Output
```cpp
"apbqcd"
```

#### Explanation
- Merge "a" from `word1` and "p" from `word2`.  
- Merge "b" from `word1` and "q" from `word2`.  
- Append the remaining characters "cd" from `word1`.

---

## Key Points

1. The algorithm efficiently handles merging by alternating characters and appending any leftovers from the longer string.
2. Both strings are traversed only once, ensuring optimal performance.
3. The solution covers edge cases such as one string being empty.

---

## Edge Cases

1. **One Empty String**:  
   If either `word1` or `word2` is empty, the result is the other string.  
   - Input: `word1 = ""`, `word2 = "abc"` → Output: `"abc"`  
   - Input: `word1 = "abc"`, `word2 = ""` → Output: `"abc"`

2. **Strings of Equal Length**:  
   If both strings have the same length, characters are alternated completely without leftovers.  
   - Input: `word1 = "abc"`, `word2 = "xyz"` → Output: `"axbycz"`

3. **Strings of Different Lengths**:  
   The remaining characters of the longer string are appended after alternating.  
   - Input: `word1 = "ab"`, `word2 = "pqrs"` → Output: `"apbqrs"`

---

