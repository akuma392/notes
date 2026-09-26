# Move All Zeros to the End

Given an array, move all `0` values to the **end of the array** while keeping the relative order of the non-zero elements.

### Example

```text
Input:
[0, 1, 2, 7, 0, 11, 13, 6, 0, 17]

Output:
[1, 2, 7, 11, 13, 6, 17, 0, 0, 0]
```

The important point is that the **order of non-zero elements remains unchanged**.

---

## JavaScript Solution

```javascript
function zerosAtEnd(arr) {
  let pos = 0;

  for (let i = 0; i < arr.length; i++) {
    if (arr[i] !== 0) {
      [arr[pos], arr[i]] = [arr[i], arr[pos]];

      pos++;
    }
  }

  return arr;
}

let arr = [0, 1, 2, 7, 0, 11, 13, 6, 0, 17];

console.log(zerosAtEnd(arr));
```

### Output

```text
[1, 2, 7, 11, 13, 6, 17, 0, 0, 0]
```

---

# How It Works

We use a pointer called `pos`.

```javascript
let pos = 0;
```

`pos` represents the **next position where a non-zero element should be placed**.

The `i` pointer scans the entire array.

```text
pos → position for next non-zero element
 i  → current element being checked
```

---

## Step-by-Step Example

Given:

```text
[0, 1, 2, 7, 0, 11, 13, 6, 0, 17]
```

Initially:

```text
pos = 0
```

### 1. `i = 0`

```text
arr[i] = 0
```

Since it is zero, we do nothing.

```text
[0, 1, 2, 7, 0, 11, 13, 6, 0, 17]
 ↑
pos
```

---

### 2. `i = 1`

```text
arr[i] = 1
```

It is non-zero, so we put it at `pos`.

```javascript
[arr[pos], arr[i]] = [arr[i], arr[pos]];
```

Array becomes:

```text
[1, 0, 2, 7, 0, 11, 13, 6, 0, 17]
```

Then:

```javascript
pos++;
```

Now:

```text
pos = 1
```

---

### 3. `i = 2`

Current value:

```text
2
```

Move it to `pos = 1`:

```text
[1, 2, 0, 7, 0, 11, 13, 6, 0, 17]
```

Then:

```text
pos = 2
```

---

### 4. `i = 3`

Current value:

```text
7
```

Move it to `pos = 2`:

```text
[1, 2, 7, 0, 0, 11, 13, 6, 0, 17]
```

Then:

```text
pos = 3
```

---

### 5. `i = 4`

Current value:

```text
0
```

Do nothing.

```text
pos = 3
```

---

### 6. `i = 5`

Current value:

```text
11
```

Move it to `pos = 3`:

```text
[1, 2, 7, 11, 0, 0, 13, 6, 0, 17]
```

Then:

```text
pos = 4
```

The same process continues for `13`, `6`, and `17`.

Final result:

```text
[1, 2, 7, 11, 13, 6, 17, 0, 0, 0]
```

---

# Understanding the Swap

This line:

```javascript
[arr[pos], arr[i]] = [arr[i], arr[pos]];
```

uses **array destructuring** to swap two values.

For example:

```javascript
let arr = [0, 5];

let pos = 0;
let i = 1;

[arr[pos], arr[i]] = [arr[i], arr[pos]];
```

After swapping:

```text
[5, 0]
```

It is equivalent to the traditional temporary-variable approach:

```javascript
let temp = arr[pos];

arr[pos] = arr[i];

arr[i] = temp;
```

---

Because we process the array from left to right, the **relative order of non-zero elements is preserved**.

---

# Two Pointers

Although there is only one explicit loop, this is essentially a **two-pointer technique**.

### `i` pointer

Scans every element:

```text
i → 0 1 2 3 4 5 6 7 8 9
```

### `pos` pointer

Tracks where the next non-zero element should go:

```text
pos → next available position
```

So:

```text
i   = current element
pos = next position for non-zero element
```

---

# Complexity

### Time Complexity

```text
O(n)
```

We traverse the array only once.

### Space Complexity

```text
O(1)
```

No additional array is created. The original array is modified **in place**.

---

# Important Points

* Moves all zeros to the end.
* Keeps the relative order of non-zero elements.
* Modifies the original array.
* Uses the two-pointer technique.
* Uses array destructuring for swapping.
* Time complexity: **O(n)**
* Space complexity: **O(1)**

### Core Logic

```javascript
if (arr[i] !== 0) {
  [arr[pos], arr[i]] = [arr[i], arr[pos]];
  pos++;
}
```

The key idea is:

> **Scan the array with `i` and use `pos` to keep track of where the next non-zero element belongs.**
