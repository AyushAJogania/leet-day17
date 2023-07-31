# leet-day17

## Minimum ASCII Delete Sum for Two Strings

Given two strings `s1` and `s2`, this problem asks us to find the lowest ASCII sum of deleted characters from both strings to make them equal.

### Example

#### Input

```cpp
s1 = "sea", s2 = "eat"
```

#### Output

```cpp
231
```

#### Explanation

Deleting "s" from "sea" adds the ASCII value of "s" (115) to the sum. Deleting "t" from "eat" adds 116 to the sum. At the end, both strings are equal, and 115 + 116 = 231 is the minimum sum possible to achieve this.

### Constraints

- 1 <= `s1.length`, `s2.length` <= 1000
- `s1` and `s2` consist of lowercase English letters.

### Approach

To solve this problem efficiently, we can use dynamic programming. We create a 2D DP table, `dp`, where `dp[i][j]` represents the lowest ASCII sum of deleted characters to make the substrings `s1[0:i]` and `s2[0:j]` equal.

The DP table is filled in a bottom-up manner. The base cases are when one of the strings is empty, in which case we calculate the sum of ASCII values of all characters in the non-empty string.

Next, we traverse through both strings and fill the DP table. If the characters at the current positions are equal, we don't need to delete anything, so we copy the value from the diagonal element (`dp[i - 1][j - 1]`). If the characters are not equal, we have two options: delete the character from `s1` or delete the character from `s2`. We choose the minimum value among these two options and add the ASCII value of the deleted character to it.

Finally, the value at `dp[m][n]`, where `m` and `n` are the lengths of `s1` and `s2`, respectively, represents the minimum sum to make both strings equal.

### Complexity Analysis

The time complexity of this approach is O(m * n), where m and n are the lengths of `s1` and `s2` respectively. The space complexity is also O(m * n) as we use a 2D DP table to store the intermediate results. Since the input strings have a maximum length of 1000, this solution is efficient and will work well within the given constraints.
