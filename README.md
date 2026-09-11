# LeetCode 167 - Two Sum II: Input Array Is Sorted

## Problem

Given a **1-indexed** array of integers `numbers` that is already sorted in non-decreasing order, find two numbers such that their sum is equal to a given `target`.

Return the indices of the two numbers.

The answer should be returned as:

```text
[index1, index2]
```

where:

```text
index1 < index2
```

The array contains exactly one solution.

---

## Example 1

**Input:**

```text
numbers = [2,7,11,15]
target = 9
```

**Output:**

```text
[1,2]
```

**Explanation:**

```text
2 + 7 = 9
```

Therefore, the required indices are `1` and `2`.

---

## Example 2

**Input:**

```text
numbers = [2,3,4]
target = 6
```

**Output:**

```text
[1,3]
```

**Explanation:**

```text
2 + 4 = 6
```

So the answer is `[1,3]`.

---

## Example 3

**Input:**

```text
numbers = [-1,0]
target = -1
```

**Output:**

```text
[1,2]
```

**Explanation:**

```text
-1 + 0 = -1
```

---

## Approach

Since the array is already sorted, we can use the **Two Pointer technique**.

We use two pointers:

* `left` → starts from the beginning.
* `right` → starts from the end.

Then calculate:

```text
numbers[left] + numbers[right]
```

There are three possible cases.

### Case 1: Sum equals target

If:

```text
numbers[left] + numbers[right] == target
```

we found the answer.

Return:

```text
[left + 1, right + 1]
```

The `+1` is required because the problem uses **1-based indexing**.

---

### Case 2: Sum is smaller than target

If:

```text
sum < target
```

we need a larger value.

Because the array is sorted, move the left pointer forward:

```text
left += 1
```

---

### Case 3: Sum is greater than target

If:

```text
sum > target
```

we need a smaller value.

So move the right pointer backward:

```text
right -= 1
```

---

## Algorithm

1. Set `left = 0`.
2. Set `right = len(numbers) - 1`.
3. Calculate the sum of the values at both pointers.
4. If the sum equals `target`, return their 1-based indices.
5. If the sum is smaller than `target`, move `left` forward.
6. If the sum is greater than `target`, move `right` backward.
7. Continue until the two pointers meet.

---

## Example Walkthrough

Consider:

```text
numbers = [2,7,11,15]
target = 9
```

Initially:

```text
left = 0
right = 3
```

Values:

```text
2 + 15 = 17
```

Since:

```text
17 > 9
```

move `right`:

```text
right = 2
```

Now:

```text
2 + 11 = 13
```

Again:

```text
13 > 9
```

Move `right`:

```text
right = 1
```

Now:

```text
2 + 7 = 9
```

The sum matches the target.

The array uses 1-based indexing, so:

```text
left + 1 = 1
right + 1 = 2
```

Final answer:

```text
[1,2]
```

---

## Why Two Pointers?

A brute-force approach would check every possible pair.

For example:

```text
2 + 7
2 + 11
2 + 15
7 + 11
...
```

This takes **O(n²)** time.

But because the array is sorted, we can eliminate unnecessary possibilities using two pointers.

This reduces the time complexity to **O(n)**.

---

## Time Complexity

**O(n)**

Each pointer moves only in one direction through the array.

Therefore, the array is traversed at most once.

---

## Space Complexity

**O(1)**

Only two pointers and a few variables are used.

No extra data structure is required.

---

## Key Concepts

* Arrays
* Two Pointers
* Sorted Array
* Searching
* 1-Based Indexing
* Comparison of Values

---

## Important Difference from LeetCode 1

LeetCode 1 uses an **unsorted array**, so a hash map is commonly used.

LeetCode 167 gives us a **sorted array**, so the Two Pointer technique is more efficient and uses constant extra space.

---

## Edge Cases

### Two elements

```text
numbers = [2,7]
target = 9
```

Output:

```text
[1,2]
```

### Negative numbers

```text
numbers = [-3,-1,0,2,4]
target = 1
```

Output:

```text
[2,5]
```

Because:

```text
-1 + 2 = 1
```

### Duplicate values

```text
numbers = [2,3,3,4]
target = 6
```

Output:

```text
[2,4]
```

Because:

```text
2 + 4 = 6
```

---

## What I Learned

This problem helped me understand how a sorted array can make searching much more efficient.

The main concept is the **Two Pointer technique**. By starting from both ends and deciding which pointer to move based on the current sum, we can find the required pair without checking every possible combination.

I also practiced handling **1-based indexing**, which is important because Python normally uses 0-based indexing.

---

## LeetCode Details

* **Problem Number:** 167
* **Problem Name:** Two Sum II: Input Array Is Sorted
* **Difficulty:** Medium
* **Topics:** Array, Two Pointers, Binary Search
* **Language:** Python

---

## Author

T.Nandhini
