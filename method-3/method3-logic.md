Logic Notes for method-3
===============================

1. Purpose:
===========  
   - Check if each binary string in a list contains a "dangerous position" — 7 consecutive `0`s or 7 consecutive `1`s.



2. Input:  
===========*
   - A list `l` containing binary strings.


3. Output Example:
==================*
   - For the provided input, the output is a print result for each input on new lines "Yes" or "No"
Eg.
YES
NO
YES
YES
---

4. Logic:
===========
   - Case 1: Strings with length less than 7:
     - Directly append `"No"` since they cannot contain 7 consecutive identical digits.
   - Case 2: Strings exactly 7 characters:
     - Check if the string equals `"0000000"` or `"1111111"`.
     - Append `"Yes"` if true; otherwise append `"No"`.
   - Case 3: Strings longer than 7 characters:
     - Use a sliding window approach:
       - Start from the beginning and check every substring of length 7.
       - If a substring equals `"0000000"` or `"1111111"`, append `"Yes"` and stop further checks for that string.
       - If no such substring is found by the end of the string, append `"No"`.



5. Steps:
===========
   - Initialize an empty list `result`.
   - Iterate over each binary string `val` in `l`:
     - If the length of `val` is less than 7, append `"No"`.
     - If the length is exactly 7, check for an exact match with `"0000000"` or `"1111111"` and append the result accordingly.
     - If the length is greater than 7, use a `while` loop to slide through the string:
       - Check each 7-character substring (`val[i:i+7]`).
       - If a match is found, append `"Yes"` and break the loop.
       - If no match is found, append `"No"`.


6. Edge Cases:
===============
   - Empty strings → Return `"No"`.
   - Strings shorter than 7 → Return `"No"`.
   - Strings exactly 7 characters → Directly compare to `"0000000"` or `"1111111"`.
   - Strings longer than 7 → Slide through and check for dangerous positions.

