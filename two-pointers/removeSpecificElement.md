# Remove a Specific Element from an Array

Given an array and a value, remove every occurrence of that value while keeping the order of the other elements.

This solution uses two pointers to move the values we want to keep to the beginning of the original array. It then returns a new array containing only that kept portion.

## JavaScript Solution

```javascript
function removeElement(arr, val) {
  let pos = 0;

  for (let i = 0; i < arr.length; i++) {
    if (arr[i] !== val) {
      [arr[i], arr[pos]] = [arr[pos], arr[i]];
      pos++;
    }
  }

  return arr.slice(0, pos);
}
```

## Example

```javascript
const nums = [3, 2, 2, 3];
const val = 3;

const result = removeElement(nums, val);
console.log(result);
```

Output:

```text
[2, 2]
```

After processing, the original `nums` array has its kept values at the beginning:

```text
[2, 2, 3, 3]
```

The function returns `nums.slice(0, 2)`, which is a new array containing just `[2, 2]`.

## How It Works

- `i` scans every element in the array.
- `pos` marks where the next value that is not `val` should be placed.
- When `arr[i] !== val`, the value is swapped into position `pos`, then `pos` advances.
- Once the scan is complete, `pos` is the number of values kept. `slice(0, pos)` returns those values.

For `[3, 2, 2, 3]` with `val = 3`:

| `i` | Value checked | Action | Array after action | `pos` |
|---:|---:|---|---|---:|
| 0 | 3 | Skip; it matches `val` | `[3, 2, 2, 3]` | 0 |
| 1 | 2 | Keep at the beginning | `[2, 3, 2, 3]` | 1 |
| 2 | 2 | Keep at the next position | `[2, 2, 3, 3]` | 2 |
| 3 | 3 | Skip; it matches `val` | `[2, 2, 3, 3]` | 2 |

## Complexity and Behavior

- **Time complexity:** `O(n)`, where `n` is the array length.
- The compaction is done in place with `O(1)` auxiliary space.
- The returned `slice` creates a new array of `k` kept elements, requiring `O(k)` space.
- The input array is modified; the function returns a separate array containing the kept values in their original order.

> **Key idea:** Use `i` to scan and `pos` to track the next slot for a value that should remain.
