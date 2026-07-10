# Count Palindromic Subsequences

## Problem Link
[Count Palindromic Subsequences](https://www.geeksforgeeks.org/problems/count-palindromic-subsequences/1)

## Difficulty
Medium

## Notes
1. Brute Force Thinking

For every character:

take
not take

Generate all subsequences.

Example:

"aba"

Subsequences:

"", a, b, a, ab, aa, ba, aba

Check each one:

Palindrome means:

string == reverse(string)

Valid:

a, b, a, aa, aba

Answer = 5

Bruteforce Complexity
O(n × 2^n)

Too slow.

2. Optimization Idea (DP)

Problem in brute force:

Same work repeats.

Example:

solve(1,1)

can be called many times.

So:

Save answer after first calculation.

Use:

dp[i][j]

Meaning:

Number of palindromic subsequences from index i to j.

3. Base Cases
Single character

Always palindrome.

if(i == j) return 1;

Example:

"a"

→ 1

Invalid substring

If:

i > j

No substring exists.

return 0;
4. Memoization Check

Before solving:

if(dp[i][j] != -1)
    return dp[i][j];

Meaning:

Already solved? Reuse answer.

5. Main Logic
Case 1: Same Ends

If:

s[i] == s[j]

Example:

a b a
^   ^

Same ends can form new palindrome.

Formula:

solve(i+1,j)
+ solve(i,j-1)
+ 1

Memory trick:

same ends
→ new palindrome possible
→ +1
Case 2: Different Ends

Example:

a b c
^   ^

No new palindrome.

But middle counted twice.

So:

solve(i+1,j)
+ solve(i,j-1)
- solve(i+1,j-1)

Memory trick:

different ends
→ overlap counted twice
→ subtract middle
Final Formula
if(s.charAt(i) == s.charAt(j))
    left + right + 1;
else
    left + right - overlap;

## Code
```txt
class Solution {

   long[][]dp;

    public long countPS(String s) {

       int n=s.length();
       dp=new long[n][n];
       for(int i=0;i<n;i++){
           Arrays.fill(dp[i],-1);
       }
       
       return solve(0,n-1,s);
}

  long solve(int i,int j,String s){
      if(i==j) return 1;
      if(i>j) return 0;
      
      if(dp[i][j] != -1) {
            return dp[i][j];
        }
      
      if(s.charAt(i)==s.charAt(j)){
         return dp[i][j]= solve(i+1,j,s)+solve(i,j-1,s)+1;
      }
      else{
         return dp[i][j]= solve(i+1,j,s)+solve(i,j-1,s)-solve(i+1,j-1,s);
      }
  }

}
```
