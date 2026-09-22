# Two Sum Using Two Pointers

The **Two Sum** problem asks us to find two elements in an array whose sum is equal to a given `target`.

For example:

```text
Array  = [2, 3, 7, 11, 13, 19, 20]
Target = 24
```

Here:

```text
11 + 13 = 24
```

So the indexes are:

```text
[3, 4]
```

## JavaScript Solution

```javascript
function twoSum(arr, target) {
  let start = 0;
  let end = arr.length - 1;

  while (end > start) {
    let sum = arr[start] + arr[end];

    if (sum === target) {
      return [start, end];
    } else if (sum > target) {
      end--;
    } else {
      start++;
    }
  }

  return -1;
}

let arr = [2, 3, 7, 11, 13, 19, 20];

console.log(twoSum(arr, 24));
```

### Output

```text
[3, 4]
```

## How It Works

The **two-pointer approach** uses two pointers:

* `start` → points to the first element
* `end` → points to the last element

Initially:

```text
start                     end
  ↓                        ↓
[ 2, 3, 7, 11, 13, 19, 20 ]
```

We calculate:

```javascript
let sum = arr[start] + arr[end];
```

### Case 1: Sum equals target

If:

```javascript
sum === target
```

we found the required pair.

```javascript
return [start, end];
```

For our example:

```text
11 + 13 = 24

       start end
         ↓   ↓
[2, 3, 7, 11, 13, 19, 20]
         3   4
```

Result:

```text
[3, 4]
```

### Case 2: Sum is greater than target

If:

```javascript
sum > target
```

we need a **smaller sum**.

Because the array is sorted, we move the `end` pointer to the left:

```javascript
end--;
```

Example:

```text
2 + 20 = 22
```

If the target were `21`, then `22` is too large, so we decrease `end`.

### Case 3: Sum is smaller than target

If:

```javascript
sum < target
```

we need a **larger sum**.

Because the array is sorted, we move the `start` pointer to the right:

```javascript
start++;
```

For example:

```text
2 + 20 = 22
```

If the target were `24`, the sum is too small, so we increase `start`.

## Step-by-Step Example

For:

```text
arr = [2, 3, 7, 11, 13, 19, 20]
target = 24
```

### Step 1

```text
start = 0 → 2
end   = 6 → 20

2 + 20 = 22
```

`22 < 24`, so:

```text
start++
```

### Step 2

```text
start = 1 → 3
end   = 6 → 20

3 + 20 = 23
```

`23 < 24`, so:

```text
start++
```

### Step 3

```text
start = 2 → 7
end   = 6 → 20

7 + 20 = 27
```

`27 > 24`, so:

```text
end--
```

### Step 4

```text
start = 2 → 7
end   = 5 → 19

7 + 19 = 26
```

`26 > 24`, so:

```text
end--
```

### Step 5

```text
start = 2 → 7
end   = 4 → 13

7 + 13 = 20
```

`20 < 24`, so:

```text
start++
```

### Step 6

```text
start = 3 → 11
end   = 4 → 13

11 + 13 = 24
```

Target found:

```text
[3, 4]
```

## Important Requirement

The **two-pointer approach shown above requires the array to be sorted**.

For example:

```javascript
[2, 3, 7, 11, 13, 19, 20]
```

is sorted in ascending order.

If the array is not sorted:

```javascript
[11, 2, 20, 7, 3, 13]
```

this approach cannot be directly used because moving `start` or `end` would no longer reliably make the sum larger or smaller.

## Time and Space Complexity

### Time Complexity

```text
O(n)
```

Each pointer moves through the array at most once.

### Space Complexity

```text
O(1)
```

Only two pointer variables are used, so no additional data structure is required.

## Summary

| Condition        | Action         |
| ---------------- | -------------- |
| `sum === target` | Return indexes |
| `sum > target`   | `end--`        |
| `sum < target`   | `start++`      |

The key idea is:

> **Sorted array + two pointers = O(n) Two Sum solution with O(1) extra space.**
