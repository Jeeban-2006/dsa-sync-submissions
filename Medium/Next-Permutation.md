# Next Permutation

## Problem Link
[Next Permutation](https://www.geeksforgeeks.org/problems/next-permutation5226/1)

## Difficulty
Medium

## Notes
🧠 Next Permutation — Approach Summary
🔹 Goal

👉 Find the next lexicographically greater arrangement
👉 If not possible → return the smallest (sorted) arrangement

🔹 Step 1: Find Breakpoint
Traverse from right
Find first index where:
👉 current > previous
That index = pivot (breakpoint)

👉 If no breakpoint → go to Step 5

🔹 Step 2: Identify Right Side

👉 All elements after breakpoint are in descending order

🔹 Step 3: Find Next Greater Element
Traverse from right side
Find first element greater than pivot
👉 This ensures smallest possible increase
🔹 Step 4: Swap

👉 Swap pivot with that element

🔹 Step 5: Reverse Suffix

👉 Reverse everything after breakpoint
👉 Converts descending → ascending (minimum order)

🔹 Edge Case

👉 If no breakpoint found:
➡️ Reverse entire array/string

🔥 Core Intuition

👉 “Make the number/string just slightly bigger, then minimize the rest”

🚀 Complexity
Time: O(n)
Space: O(1) (in-place)
💡 One-line memory trick

👉 Find → Swap → Reverse

## Code
```txt
class Solution {
    void nextPermutation(int[] arr) {

        int breakp = -1;

        for(int i = arr.length - 1; i > 0; i--){
            if(arr[i] > arr[i - 1]){
                breakp = i - 1;
                break;
            }
        }

        if(breakp == -1){
            int i = 0, j = arr.length - 1;
            while(i < j){
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
                i++;
                j--;
            }
            return;
        }

        for(int i = arr.length - 1; i > breakp; i--){
            if(arr[i] > arr[breakp]){
                int temp = arr[i];
                arr[i] = arr[breakp];
                arr[breakp] = temp;
                break;
            }
        }

        int i = breakp + 1;
        int j = arr.length - 1;

        while(i < j){
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
            i++;
            j--;
        }
    }
}
```
