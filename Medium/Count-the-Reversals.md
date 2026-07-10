# Count the Reversals

## Problem Link
[Count the Reversals](https://www.geeksforgeeks.org/problems/count-the-reversals0401/1)

## Difficulty
Medium

## Notes
Step 1: Check if balancing is possible

A balanced bracket expression always has even number of brackets.

So:

Odd length → impossible
Return -1

Example:

"{{}"

Length = 3 (odd)

Cannot be balanced.

Step 2: Remove already balanced {} pairs using stack

Traverse the string character by character.

If current character is {

Push into stack.

st.push(ch);
If current character is }

Check top of stack:

Case 1: Top is {

We found:

{}

This is already balanced.

So remove pair:

st.pop();
Case 2: No matching {

This } is unmatched.

Push it into stack.

Example walkthrough

Input:

}{{}}{{{

Process:

}   → push
{   → push
{   → push
}   → pop (matched {})
{   → push
}   → pop (matched {})
{   → push
{   → push

Remaining stack:

}{{{

Only invalid brackets remain.

Step 3: Count remaining unmatched brackets

Now count:

how many {
how many }

Example:

}{{{

Count:

open = 3
close = 1
Step 4: Calculate reversals

Every 2 same brackets need 1 reversal.

Examples:

{{ → 1 reversal
}} → 1 reversal

Formula:

(open + 1) / 2 + (close + 1) / 2

Example:

open = 3
close = 1

Calculation:

(3+1)/2 + (1+1)/2
= 2 + 1
= 3

Answer = 3

Time Complexity

We traverse string once:

O(n)

Stack operations are constant time.

Space Complexity

In worst case stack stores all characters:

O(n)

## Code
```txt
class Solution {
    public int countMinReversals(String s) {
        // code here
        Deque<Character> st=new ArrayDeque<>();
        if(s.length()%2!=0)
           return -1;
        
        for(char ch:s.toCharArray()){
            if(ch=='{'){
                st.push(ch);
            }
            else{
                if(!st.isEmpty() && st.peek()=='{'){
                    st.pop();
                }
                else{
                    st.push(ch);
                }
            }
        }
        
        int open=0;
        int close=0;
        
        while(!st.isEmpty()){
            char ch=st.pop();
            if (ch == '{') {
        open++;
    } else {
        close++;
    }
}

return (open + 1) / 2 + (close + 1) / 2;
        }
          
           
    }

```
