function duplicate(arr) {
  let pos = 0;
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] !== arr[i + 1]) {
      [arr[i], arr[pos]] = [arr[pos], arr[i]];
      pos++;
    }
  }
  return arr.slice(0, pos);
}

console.log(duplicate([1, 1, 2, 2, 3, 3, 3, 4, 5, 6]));
