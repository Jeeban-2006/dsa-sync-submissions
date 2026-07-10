# Convert a sentence into its equivalent mobile numeric keypad sequence

## Problem Link
[Convert a sentence into its equivalent mobile numeric keypad sequence](https://www.geeksforgeeks.org/problems/convert-a-sentence-into-its-equivalent-mobile-numeric-keypad-sequence0547/1)

## Difficulty
Easy

## Notes
Create a keypad mapping array that stores the numeric sequence for each alphabet from A to Z.
Traverse the input string character by character using a loop.
For each character:
If it is a space, append "0" to the result.
Otherwise, convert the character into an index using:
ch - 'A'
Use that index to fetch the corresponding keypad sequence from the array:
keypad[index]
Append the sequence to the result string.
Return the final generated numeric sequence.
Time Complexity
O(N) → We traverse the string once.
Space Complexity
O(1) → Fixed-size keypad array (26 elements).

## Code
```txt
// User function Template for Java
class Solution {
    String printSequence(String S) {
        // code here
        int n=S.length();
        String[] keypad = {
    "2", "22", "222",        // A B C
    "3", "33", "333",        // D E F
    "4", "44", "444",        // G H I
    "5", "55", "555",        // J K L
    "6", "66", "666",        // M N O
    "7", "77", "777", "7777", // P Q R S
    "8", "88", "888",        // T U V
    "9", "99", "999", "9999" // W X Y Z
};
String s="";
        for(int i=0;i<n;i++){
            if(S.charAt(i)==' '){
                s+="0";
            }
            else{
                char ch = S.charAt(i);
                int index = ch - 'A';
                s += keypad[index];
            }
        }
        
        return s;
    }
}
```
