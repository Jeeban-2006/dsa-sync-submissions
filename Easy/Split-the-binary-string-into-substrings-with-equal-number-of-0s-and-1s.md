# Split the binary string into substrings with equal number of 0s and 1s

## Problem Link
[Split the binary string into substrings with equal number of 0s and 1s](https://www.geeksforgeeks.org/problems/split-the-binary-string-into-substrings-with-equal-number-of-0s-and-1s/1)

## Difficulty
Easy

## Notes
Initialize three variables:

count0 → number of 0s

count1 → number of 1s

ans → number of balanced substrings

Traverse the binary string character by character.

For each character:

If it is '0', increment count0.

If it is '1', increment count1.

Whenever count0 == count1, it means the current segment has equal 0s and 1s, so:

Increment ans (one balanced substring found).

After completing the traversal:

If the total number of 0s and 1s are not equal, splitting fully is impossible → return -1.

Otherwise return ans.

Complexity

Time Complexity: O(N)

Space Complexity: O(1)

## Code
```txt
// User function Template for Java

class Solution {
    public static int maxSubStr(String str) {
        // Write your code here
      int c0 = 0, c1 = 0, count = 0;

        for (char ch : str.toCharArray()) {
            if (ch == '0') c0++;
            else c1++;

            if (c0 == c1) count++;
        }

        return (c0 == c1) ? count : -1;
       
    }
}
```
