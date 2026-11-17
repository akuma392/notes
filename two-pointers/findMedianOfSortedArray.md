# Find the Median of Two Sorted Arrays

The **median** is the middle value of a sorted collection. Given two arrays sorted in ascending order, we can merge them into one sorted array and then select its middle value.

- If the merged array has an **odd** number of values, the median is the one middle value.
- If it has an **even** number of values, the median is the average of the two middle values.

This solution uses two pointers to merge the input arrays in order.

## JavaScript Solution

```javascript
function findMedianSortedArrays(nums1, nums2) {
  let i = 0;
  let j = 0;
  const merged = [];

  while (i < nums1.length && j < nums2.length) {
    if (nums1[i] <= nums2[j]) {
      merged.push(nums1[i]);
      i++;
    } else {
      merged.push(nums2[j]);
      j++;
    }
  }

  while (i < nums1.length) {
    merged.push(nums1[i]);
    i++;
  }

  while (j < nums2.length) {
    merged.push(nums2[j]);
    j++;
  }

  const middle = Math.floor(merged.length / 2);

  if (merged.length % 2 === 0) {
    return (merged[middle - 1] + merged[middle]) / 2;
  }

  return merged[middle];
}
```

## Example: Odd Number of Values

```javascript
const result = findMedianSortedArrays([1, 3], [2]);
console.log(result);
```

The merged array is:

```text
[1, 2, 3]
```

It has three values, so the middle value is the median.

```text
Output: 2
```

## Example: Even Number of Values

```javascript
const result = findMedianSortedArrays([1, 2], [3, 4]);
console.log(result);
```

The merged array is:

```text
[1, 2, 3, 4]
```

The two middle values are `2` and `3`, so their average is the median.

```text
Output: 2.5
```

## How It Works

The pointers `i` and `j` track the next unmerged value in `nums1` and `nums2`.

1. Compare `nums1[i]` with `nums2[j]`.
2. Add the smaller value to `merged` and advance its pointer.
3. Continue until one input array has no values left.
4. Append the remaining values from the other array.
5. Use the merged array's length to select the middle value or average the two middle values.

For the odd-length example:

| Comparison | Value added | Merged array |
|---|---:|---|
| `1` and `2` | `1` | `[1]` |
| `3` and `2` | `2` | `[1, 2]` |
| Append remaining value | `3` | `[1, 2, 3]` |

## Requirements and Complexity

- Both input arrays must already be sorted in ascending order.
- At least one array must contain a value; two empty arrays do not have a median.
- **Time complexity:** `O(m + n)`, where `m` and `n` are the input lengths.
- **Space complexity:** `O(m + n)` for the merged array.

> **Key idea:** Use one pointer per sorted array to merge values in order, then find the middle of the merged result.
