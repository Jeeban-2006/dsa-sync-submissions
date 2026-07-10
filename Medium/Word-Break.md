# Word Break

## Problem Link
[Word Break](https://www.geeksforgeeks.org/problems/word-break1352/1)

## Difficulty
Medium

## Notes
🧠 Word Break — Approach Summary
🔹 Goal

👉 Check if the string can be split into valid dictionary words

🔹 Step 1: Use a Set

👉 Store all dictionary words in a HashSet
✔️ Fast checking: “is this word valid?”

🔹 Step 2: Create DP array

👉 dp[i] = true
means → first i characters can be formed

👉 Initialize:

dp[0] = true (empty string)
🔹 Step 3: Build answer step-by-step

For each position i:

Try all possible splits at j

👉 Check:

Left part is valid → dp[j] == true
Right part is a word → s[j...i] in dictionary

👉 If both true → dp[i] = true

🔹 Step 4: Final answer

👉 Return dp[n]

true → possible
false → not possible
🔥 Core Logic

👉 “If I can reach position j, and substring (j → i) is a word, then I can reach i”

💡 Example Thinking
leetcode = leet + code

👉 dp[4] = true
👉 dp[8] = true

🚀 Complexity
Time: O(n²)
Space: O(n)
💡 One-line memory trick

👉 Valid left + valid word = valid position

## Code
```txt
class Solution {
    public boolean wordBreak(String s, String[] dictionary) {
        
        HashSet<String> set = new HashSet<>();
        int maxLen = 0;
        
        for(String word : dictionary){
            set.add(word);
            maxLen = Math.max(maxLen, word.length());
        }
        
        int n = s.length();
        boolean[] dp = new boolean[n + 1];
        dp[0] = true;
        
        for(int i = 1; i <= n; i++){
            for(int j = i - 1; j >= Math.max(0, i - maxLen); j--){
                
                if(dp[j] && set.contains(s.substring(j, i))){
                    dp[i] = true;
                    break;
                }
            }
        }
        
        return dp[n];
    }
}
```
