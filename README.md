# 791.-Custom-Sort-String
You are given two strings order and s. All the characters of order are unique and were sorted in some custom order previously.

Permute the characters of s so that they match the order that order was sorted. More specifically, if a character x occurs before a character y in order, then x should occur before y in the permuted string.

Return any permutation of s that satisfies this property.

 

Example 1:

Input: order = "cba", s = "abcd"
Output: "cbad"
Explanation: 
"a", "b", "c" appear in order, so the order of "a", "b", "c" should be "c", "b", and "a". 
Since "d" does not appear in order, it can be at any position in the returned string. "dcba", "cdba", "cbda" are also valid outputs.
Example 2:

Input: order = "cbafg", s = "abcd"
Output: "cbad"
 

Constraints:

class Solution {
    public String customSortString(String order, String s) {
     int[] charCount = new int[26];

        // Count occurrences of each character in s
        for (char c : s.toCharArray()) {
            charCount[c - 'a']++;
        }

        StringBuilder result = new StringBuilder();

        // Append characters in the specified order
        for (char c : order.toCharArray()) {
            while (charCount[c - 'a'] > 0) {
                result.append(c);
                charCount[c - 'a']--;
            }
        }

        // Append remaining characters that are not in the order
        for (char c = 'a'; c <= 'z'; c++) {
            while (charCount[c - 'a'] > 0) {
                result.append(c);
                charCount[c - 'a']--;
            }
        }

        return result.toString();
    }
}
