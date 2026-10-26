# Software Engineering Cheatsheets

Coding-interview patterns transcribed from the cheatsheet images in this folder (`arrays.png`, `two-pointers.png`, `Stacks.png`), grouped by data structure. Each problem is a collapsible with its core idea, approach, and time/space complexity. There are 18 problems across 3 categories.

Jump to: [Arrays](#1-arrays) · [Two Pointers](#2-two-pointers) · [Stack](#3-stack)

---

## 1. Arrays

<details>
<summary><b>1. Contains Duplicate</b></summary>

**Core idea:** Detect repetition fast.

**Approach:**
- Insert into dictionary.
- If the current element is already in dict, duplicate found.

**Time:** O(n) · **Space:** O(n)

</details>

<details>
<summary><b>2. Valid Anagram</b></summary>

**Core idea:** Same multiset of characters.

**Approach:**
- Count with fixed-size array (a–z) or Dict and compare; or
- Sort both strings and compare.

**Time:** O(n) counting · O(n log n) sorting

**Space:** O(1) counting (fixed alphabet) · O(1)–O(n) sorting

</details>

<details>
<summary><b>3. Two Sum</b></summary>

**Core idea:** Complement lookup.

**Approach:**
- `dict[value: index]`
- For x, check (target - x) before storing x, to avoid using the same element twice.
- Sorted? Use two pointers.

**Time:** O(n) hash map · O(n) two pointers on sorted

**Space:** O(n) hash map · O(1) two pointers on sorted

</details>

<details>
<summary><b>4. Group Anagrams</b></summary>

**Core idea:** Bucket by signature of letters.

**Approach:**
- Sorted key: `''.join(sorted(s))` as key → map to list.
- Count key: 26-length frequency tuple/string as key.

**Time:** Sorted key: O(n·L log L) · Count key: O(n·L)

**Space:** O(n·L)

</details>

<details>
<summary><b>5. Product of Array Except Self</b></summary>

**Core idea:** Prefix × Suffix products.

**Approach:**
- Pass 1: `res[i] = prefixProductSoFar`
- Pass 2 (right→left): `res[i] *= suffixProductSoFar`

**Time:** O(n) · **Space:** O(1) extra (excluding output)

</details>

<details>
<summary><b>6. Encode and Decode Strings</b></summary>

**Core idea:** Robust serialization.

**Approach:**
- Length-prefix each word: `len + '/' + word`.
- Decode: read digits to '/', parse length, then read exactly len chars.

**Time:** O(total chars) · **Space:** O(total chars)

</details>

## 2. Two Pointers

<details>
<summary><b>7. Valid Palindrome</b></summary>

**Core idea:** Check if a string reads the same forward and backward.

**Approach:**
- Use two pointers at start and end.
- Move inward skipping non-alphanumeric.
- Compare lowercase chars.

**Time:** O(n) · **Space:** O(1)

</details>

<details>
<summary><b>8. Two Sum II (Input Sorted)</b></summary>

**Core idea:** Find two numbers in a sorted array that add up to a target.

**Approach:**
- Start pointers at both ends.
- If sum < target, move left (pointer inward).
- If sum > target, move right (pointer inward).
- If equal, return indices.

**Time:** O(n) · **Space:** O(1)

</details>

<details>
<summary><b>9. 3Sum</b></summary>

**Core idea:** Find all unique triplets that sum to zero.

**Approach:**
- Sort the array.
- Fix one element.
- Run two pointers on the rest.
- Skip duplicates.

**Time:** O(n²) · **Space:** O(1) (ignoring output list)

</details>

<details>
<summary><b>10. Container With Most Water</b></summary>

**Core idea:** Maximize the area between two vertical lines.

**Approach:**
- Two pointers at ends.
- Compute `area = min(height[l], height[r]) × (r − l)`.
- Move shorter pointer inward.

**Time:** O(n) · **Space:** O(1)

</details>

<details>
<summary><b>11. Trapping Rain Water</b></summary>

**Core idea:** Calculate trapped water using boundary heights.

**Approach:**
- Two pointers at both ends.
- Track leftMax & rightMax.
- Move side with smaller height.
- `water = maxSoFar − currentHeight`

**Time:** O(n) · **Space:** O(1)

</details>

## 3. Stack

<details>
<summary><b>12. Valid Parentheses</b></summary>

**Core idea:** Check if brackets are correctly balanced.

**Approach:**
- Use a stack.
- Push opening brackets.
- On closing, pop & check match.
- At end stack must be empty.

**Time:** O(n) · **Space:** O(n)

</details>

<details>
<summary><b>13. Min Stack</b></summary>

**Core idea:** Support push, pop, top, and retrieving minimum in O(1).

**Approach:**
- Maintain two stacks (values + mins).
- On push, also store `min(new, currentMin)`.
- On pop, remove from both stacks.

**Time:** O(1) per operation · **Space:** O(n)

</details>

<details>
<summary><b>14. Evaluate Reverse Polish Notation</b></summary>

**Core idea:** Evaluate postfix expressions efficiently.

**Approach:**
- Use a stack.
- For numbers → push.
- For operators → pop last 2, apply, push result.
- Final value remains.

**Time:** O(n) · **Space:** O(n)

</details>

<details>
<summary><b>15. Generate Parentheses</b></summary>

**Core idea:** Generate all valid parentheses of length 2n.

**Approach:**
- Backtracking.
- Add `(` if open < n.
- Add `)` if close < open.

**Time:** O(4ⁿ / √n) · **Space:** O(n) recursion depth

</details>

<details>
<summary><b>16. Daily Temperatures</b></summary>

**Core idea:** Find the next warmer day for each day.

**Approach:**
- Use monotonic decreasing stack of indices.
- While current temp > stack top → pop & update.
- Push current index.

**Time:** O(n) · **Space:** O(n)

</details>

<details>
<summary><b>17. Car Fleet</b></summary>

**Core idea:** Count fleets reaching destination.

**Approach:**
- Sort cars by starting position (descending).
- Compute time to reach target for each car.
- Use stack: if current time > top, new fleet; else merge.

**Time:** O(n log n) · **Space:** O(n)

</details>

<details>
<summary><b>18. Largest Rectangle in Histogram</b></summary>

**Core idea:** Find max area rectangle in histogram.

**Approach:**
- Use monotonic increasing stack of indices.
- While current height < stack top → pop & compute area.
- Push index of current bar.
- Append sentinel 0 height to flush.

**Time:** O(n) · **Space:** O(n)

</details>
