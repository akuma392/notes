# Find the Second-Largest Number

The **second-largest** number is the greatest value in an array that is strictly smaller than the largest value. This solution finds it in one pass without sorting the array.

The function tracks two values:

- `max` — the largest number seen so far.
- `secondMax` — the largest number seen so far that is smaller than `max`.

## JavaScript Solution

```javascript
function secondLargest(arr) {
  let max = -Infinity;
  let secondMax = -Infinity;

  for (let i = 0; i < arr.length; i++) {
    if (arr[i] > max) {
      secondMax = max;
      max = arr[i];
    } else if (arr[i] > secondMax && arr[i] < max) {
      secondMax = arr[i];
    }
  }

  console.log(max, secondMax);
  return secondMax;
}
```

## Example

```javascript
const result = secondLargest([11, 10, 9, 26, 23, 20, 1, 8, 19]);
console.log(result);
```

Output:

```text
26 23
23
```

The largest value is `26`, and the greatest value strictly below it is `23`.

## How It Works

For each value:

1. If it is larger than `max`, move the old `max` into `secondMax`, then update `max`.
2. Otherwise, if it is between `secondMax` and `max`, update `secondMax`.
3. Ignore values that do not change either value.

For the example, the key updates are:

| Value | `max` | `secondMax` |
|---:|---:|---:|
| `11` | 11 | `-Infinity` |
| `10` | 11 | 10 |
| `26` | 26 | 11 |
| `23` | 26 | 23 |

Values such as `20`, `1`, `8`, and `19` do not exceed the current `secondMax`, so the result remains `23`.

## Complexity and Notes

- **Time complexity:** `O(n)`, where `n` is the number of array elements.
- **Space complexity:** `O(1)`; only two tracking variables are used.
- The result is the second-largest **distinct** value. For example, `[5, 5, 3]` returns `3`.
- If the array has fewer than two distinct numeric values, `secondMax` remains `-Infinity`.
- The function logs both tracked values and also returns `secondMax`.

> **Key idea:** Keep track of the largest and second-largest distinct values as you scan the array once.
