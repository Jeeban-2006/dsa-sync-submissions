# Parenthesis Checker

## Problem Link
[Parenthesis Checker](https://www.geeksforgeeks.org/problems/parenthesis-checker2744/1)

## Difficulty
Easy

## Notes
🧠 Parenthesis Checker – Approach Summary
🔑 Core Idea

Use a stack (LIFO) to track opening brackets and ensure correct matching order.

📌 Steps

1️⃣ Initialize an empty stack

2️⃣ Traverse the string character by character

If character is an opening bracket
(, {, [
→ push it into stack

If character is a closing bracket
), }, ]

👉 Then:

If stack is empty → ❌ invalid
Else check:
) matches (
} matches {
] matches [
If match → pop from stack
Else → ❌ invalid

3️⃣ After traversal

If stack is empty → ✅ valid
Else → ❌ invalid
⚠️ Key Points
Order matters (LIFO)
Always match with top of stack
Don’t skip empty check before pop
🧠 One-line intuition

“Every closing bracket must close the most recent unmatched opening bracket.”

## Code
```txt
import java.util.*;
class Solution {
    public boolean isBalanced(String s) {
        // code here
        Deque<Character> st=new ArrayDeque<>();
        
        for(char ch: s.toCharArray()){
            if(ch=='(' || ch=='{' || ch == '['){
                st.push(ch);
            }
            
            else{
                if (st.isEmpty()){
                return false;
            }
            else if (
   (ch == ')' && st.peek() == '(') ||
   (ch == '}' && st.peek() == '{') ||
   (ch == ']' && st.peek() == '[')
){
    st.pop();
}

else {
    return false;
}
                
            
        }
    }
    
    if(st.isEmpty()){
        return true;
    }
    else{
        return false;
    }
}
    
}

```
