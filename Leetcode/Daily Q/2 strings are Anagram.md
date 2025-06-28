Q:
https://leetcode.com/problems/valid-anagram/submissions/1679358801/

Solution:
https://www.youtube.com/watch?v=SFF3ND7TPc0

Code:
public class Solution 
{

    public boolean isAnagram(String s, String t) {
        if(s.length()!=t.length())
        return false;
        int[] alphabet = new int[26];
        for (int i = 0; i < s.length(); i++) alphabet[s.charAt(i) - 'a']++;
        for (int i = 0; i < t.length(); i++) alphabet[t.charAt(i) - 'a']--;
        for (int i : alphabet) if (i != 0) return false;
        return true;
    }
}

Approach:
> What is an Anagram?

An anagram is a rearrangement of a string's characters to form another string, with exactly the same characters and frequency.
Example: "act" and "tac" are anagrams.

> Problem Statement

Given two lowercase strings, determine if they are anagrams using a Boolean function isAnagram.
The strings must have the same length and identical character frequencies.

> Naive Solution: Sorting Method

Check if the lengths of the strings are equal; if not, they cannot be anagrams.
Convert both strings to character arrays and sort them.
Compare the sorted arrays; if all characters match, they are anagrams.
Time complexity is O(n log n) due to sorting.

> Optimized Solution: Frequency Counting

Create a frequency array of size 26 (for 'a' to 'z').
For each character in the first string, increment the count at its corresponding index.
For each character in the second string, decrement the count at its corresponding index.
After processing both strings, check if every count in the frequency array is zero.
If all are zero, the strings are anagrams; otherwise, they are not.
Time complexity is O(n), and space complexity is O(1) (constant size array).

>Step-by-Step Algorithm

- If the lengths of the two strings differ, return false immediately.
- Initialize a frequency array of size 26 to zero.
- In a single loop, increment for string A’s character and decrement for string B’s character.
- After the loop, verify if all counts in the frequency array are zero.
- Return true if all are zero, else return false.
  
>Key Terms & Definitions
Anagram — two strings with identical characters in any order, same frequency for each character.
Frequency array — an array representing the count of each character in the string.
Time complexity — the amount of time an algorithm takes as a function of input size (n).
