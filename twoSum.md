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

console.log(twoSum(arr,24))
