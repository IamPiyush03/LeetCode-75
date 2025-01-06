
---

# 151. Reverse Words in a String

## Problem Description

Given a string `s`, reverse the order of words in the string. A word is defined as a sequence of non-space characters. The words in `s` are separated by at least one space. Return a string of the words in reverse order concatenated by a single space.

### Constraints:
1. Input string may contain leading or trailing spaces.
2. Input string may have multiple spaces between words.

---

## Solution Explanation

This solution processes the string to extract words and then reverses their order. It uses two main steps:  
1. **Extract Words**: Traverse the string to collect words by skipping spaces and grouping characters until a space or the end of the string is encountered.  
2. **Reverse Word Order**: Append each word to the result in reverse order (prepend each new word).

---

## Code Implementation

```cpp
class Solution {
public:
    string reverseWords(string s) {
        int n = s.size();
        string ans = "";
        int i = 0;

        // Traverse the string
        while (i < n) {
            string temp = "";

            // Skip leading spaces
            while (i < n && s[i] == ' ') i++;

            // Collect characters for the current word
            while (i < n && s[i] != ' ') {
                temp += s[i];
                i++;
            }

            // Add the word to the result in reverse order
            if (temp.size() > 0) {
                if (ans.size() == 0) {
                    ans = temp; // First word
                } else {
                    ans = temp + " " + ans; // Prepend to reverse order
                }
            }
        }

        return ans;
    }
};
```

---

## Algorithm Explanation

1. **Initialize Variables**:  
   - `ans`: Stores the final reversed string.
   - `temp`: Temporarily stores the current word.
   - `i`: Pointer to traverse the string.

2. **Traverse the String**:  
   - Skip any leading spaces.
   - Collect characters for the current word until a space or end of string is encountered.

3. **Process Each Word**:  
   - If a word is found, prepend it to the `ans` string. This ensures words are reversed in order.

4. **Return the Result**:  
   - Return the `ans` string containing the words in reverse order with single spaces between them.

---

## Complexity Analysis

1. **Time Complexity**:  
   - The solution traverses the string once and processes each character, resulting in \(O(n)\), where \(n\) is the length of the input string.

2. **Space Complexity**:  
   - The space complexity is \(O(n)\) for the result string `ans` and temporary variables.

---

## Example Usage

### Example 1

#### Input
```cpp
string s = "the sky is blue";
```

#### Output
```cpp
"blue is sky the"
```

#### Explanation
- Words are reversed: `["the", "sky", "is", "blue"]` → `["blue", "is", "sky", "the"]`.

---

### Example 2

#### Input
```cpp
string s = "  hello world  ";
```

#### Output
```cpp
"world hello"
```

#### Explanation
- Leading and trailing spaces are ignored.
- Words are reversed: `["hello", "world"]` → `["world", "hello"]`.

---

### Example 3

#### Input
```cpp
string s = "a good   example";
```

#### Output
```cpp
"example good a"
```

#### Explanation
- Consecutive spaces are reduced to a single space in the output.
- Words are reversed: `["a", "good", "example"]` → `["example", "good", "a"]`.

---

## Edge Cases

1. **Empty String**:  
   Input: `""` → Output: `""`

2. **All Spaces**:  
   Input: `"     "` → Output: `""`

3. **Single Word**:  
   Input: `"word"` → Output: `"word"`

4. **Multiple Spaces Between Words**:  
   Input: `"a  b   c"` → Output: `"c b a"`

---

## Key Points

1. **Handles Spaces**:  
   - Skips leading and trailing spaces.
   - Reduces multiple spaces between words to a single space in the output.

2. **Reverses Words in Place**:  
   - Appends words in reverse order while traversing the string.

3. **Optimal Time Complexity**:  
   - The algorithm ensures \(O(n)\) time complexity by processing the string in one pass.

---

