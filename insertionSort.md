## 📌 Insertion Sort (JavaScript)

### 💻 Code

```javascript
function insertionSort(arr) {
  for (let i = 1; i < arr.length; i++) {
    let currentVal = arr[i];
    let j = i - 1;

    while (j >= 0 && arr[j] > currentVal) {
      arr[j + 1] = arr[j];
      j--;
    }

    arr[j + 1] = currentVal;
  }
  return arr;
}

# 📌 Insertion Sort Examples

## ▶️ Example 1

```javascript
const arr = [5, 2, 4, 6, 1, 3];

| Case         | Time Complexity | Explanation                      |
| ------------ | --------------- | -------------------------------- |
| Best Case    | O(n)            | Already sorted, only comparisons |
| Average Case | O(n²)           | Partial shifting                 |
| Worst Case   | O(n²)           | Reverse order, maximum shifts    |



