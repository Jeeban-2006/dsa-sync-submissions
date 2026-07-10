# Print all subsequences of a string

## Problem Link
[Print all subsequences of a string](https://www.geeksforgeeks.org/dsa/print-subsequences-string/)

## Difficulty
Medium

## Notes
Step 1: Define Recursive Function

Function parameters:

index → current position in string

current → subsequence built so far

🔹 Step 2: Base Case

If:

index == string length

It means:

No more characters left

Current subsequence is complete

Print/store it

Return

🔹 Step 3: Recursive Choices

For every character:

Choice 1 → Take the character

Move to next index and add character.

Choice 2 → Skip the character

Move to next index without adding it.

## Code
```txt
public class SubsequenceExample {

    public static void printSubsequence(String str, int index, String current) {

        // Base case
        if (index == str.length()) {
            System.out.println(current);
            return;
        }

        // Choice 1: Take the character
        printSubsequence(str, index + 1, current + str.charAt(index));

        // Choice 2: Skip the character
        printSubsequence(str, index + 1, current);
    }

    public static void main(String[] args) {
        String s = "abc";
        printSubsequence(s, 0, "");
    }
}
```
