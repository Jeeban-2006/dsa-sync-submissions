# Word Wrap

## Problem Link
[Word Wrap](https://www.geeksforgeeks.org/problems/word-wrap1646/1)

## Difficulty
Hard

## Notes
Start from first word

Place the first word in the current line

Track spaces = characters used in current line

At each word (curr) you have 2 choices

👉 Choice 1: Continue in same line

Add current word to the line

New space used:

spaces + 1 + arr[curr]

(+1 for space between words)

Only valid if:

newSpaces ≤ k
👉 Choice 2: Break the line here

End current line

Add cost:

(k - spaces)²

Start new line with current word:

spaces = arr[curr]

Recursive Decision

At every step:

min(
   continue same line,
   break line + cost
)

Base Case

If all words are placed:

return 0

(last line has no cost)

State Definition (Important)

(curr index, spaces used)

This uniquely defines a subproblem.

Optimization (DP)

Store result for each (curr, spaces)

Avoid recomputation

Makes solution efficient

## Code
```txt
class Solution {
    int[][] dp;

    public int solveWordWrap(int[] arr, int k) {
        int n = arr.length;
        dp = new int[n][k + 1];

        // initialize dp with -1
        for (int i = 0; i < n; i++) {
            for (int j = 0; j <= k; j++) {
                dp[i][j] = -1;
            }
        }

        // start from index 1, first word already placed
        return helper(1, arr[0], arr, k);
    }

    public int helper(int curr, int spaces, int[] arr, int k) {

        // base case
        if (curr == arr.length) {
            return 0; // last line cost = 0
        }

        if (dp[curr][spaces] != -1) return dp[curr][spaces];

        int a = Integer.MAX_VALUE;
        int b;

        // 👉 Choice 1: continue same line
        int newSpaces = spaces + 1 + arr[curr];
        if (newSpaces <= k) {
            a = helper(curr + 1, newSpaces, arr, k);
        }

        // 👉 Choice 2: break line here
        int cost = (k - spaces) * (k - spaces);
        b = cost + helper(curr + 1, arr[curr], arr, k);

        return dp[curr][spaces] = Math.min(a, b);
    }
}
```
