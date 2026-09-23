let arr = [2,5,1,3,4,7]

function slidingWindow(arr,k){
  let res= [];
  for(let i =0;i<=arr.length-k;i++){
    let max = arr[i]
    for(let j = 1;j<k;j++){
      if(arr[i+j] > max){
        max = arr[i+j]
      }
    }
    res.push(max)
  }
  return res
}

console.log(slidingWindow(arr,3))
