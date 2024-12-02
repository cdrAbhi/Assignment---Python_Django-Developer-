```markdown
# is_position_dangerous

## Overview

This function evaluates a list of binary strings to determine if they contain a "dangerous position" — defined as 7 consecutive `0`s or 7 consecutive `1`s.

---

## Input
- A list `inputs` containing binary strings.

---

## Output
- A list `result` where each entry is `"Yes"` or `"No"`, indicating whether the corresponding binary string contains a "dangerous position."

---

## Logic

### Case 1: Strings shorter than 7 characters
- Return `"No"` because they cannot contain 7 consecutive identical digits.

### Case 2: Strings exactly 7 characters
- Check if the string equals `"0000000"` or `"1111111"`.
- Append `"Yes"` if true, otherwise `"No"`.

### Case 3: Strings longer than 7 characters
- Loop through the string and check for a sequence of 7 consecutive identical digits.
- Use a counter (`c`) to track the length of consecutive identical digits.
- If `c == 7` at any point:
  - Append `"Yes"` and stop further checks for that string.
- If no sequence of 7 consecutive identical digits is found:
  - Append `"No"`.

---

## Steps
1. Initialize an empty list `result`.
2. Iterate over each binary string in `inputs`:
   - For strings with a length less than 7, append `"No"`.
   - For strings with a length equal to 7, check if they are `"0000000"` or `"1111111"`. Append `"Yes"` or `"No"` accordingly.
   - For strings longer than 7, use a sliding check:
     - If a substring of 7 consecutive identical digits is found, append `"Yes"` and break the loop.
     - Otherwise, append `"No"` after the loop.

---

## Edge Cases
1. **Empty strings** → Return `"No"`.
2. **Strings shorter than 7** → Return `"No"`.
3. **Strings exactly 7 characters** → Direct match with `"0000000"` or `"1111111"`.
4. **Strings longer than 7** → Check substrings for 7 consecutive identical digits.

---

## Example Usage

```python
def is_position_dangerous(inputs):
    result = []
    for val in inputs:
        if len(val) < 7:
            result.append("No")
        elif len(val) == 7:
            result.append("Yes" if val == "0000000" or val == "1111111" else "No")
        elif len(val) > 7:
            c = 1
            for i in range(1, len(val)):
                if len(val) - (i) + c < 7:
                    result.append("No")
                    break
                elif val[i - 1] != val[i]:
                    c = 1
                else:
                    c += 1
                    if c == 7:
                        result.append("Yes")
                        break
    return result

# Sample Input
inputs = [
    '0010', '10000000', '001001101111111', '111101111111111', '',
    '101001', '10100101000000000', '1010101', '0000000', '1111111'
]

# Call the function
result = is_position_dangerous(inputs)
print("\n".join(result))
```

### Expected Output
```
No
No
Yes
Yes
No
No
Yes
No
Yes
Yes
```

---
