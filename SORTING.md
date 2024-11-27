# BubbleSort
```javascript
function BubbleSort(arr){
  let swapping
  do{
    swapping = false
    for(let i =0;i<arr.length;i++){
      if(arr[i] < arr[i+1]){
        let temp = arr[i];
        arr[i] = arr[i+1];
        arr[i+1] = temp
        swapping = true
      }
    }
  }while(swapping)
  return arr
}
console.log(BubbleSort(arr))
```
# InsertionSort
```javascript
function InsertionSort(arr){
  for(let i = 1;i<arr.length;i++){
    let numberToInsert = arr[i];
    let j = i - 1;
    while(j >= 0 && numberToInsert < arr[j]){
      arr[j+1] = arr[j];
      j= j-1
    }
    arr[j+1] = numberToInsert
  }
  return arr
}
console.log(InsertionSort(arr))
```
# QuickSort
```javascript
function QuickSort(arr){
  if (arr.length <= 1) return arr;
  let pivlot = arr[arr.length - 1];
  let left = [];
  let right =[]
  for(let i = 0;i<arr.length - 1;i++){
    if(arr[i] < pivlot){
      left.push(arr[i])
    }else{
      right.push(arr[i])
    }
  }
  return [...QuickSort(left),pivlot,...QuickSort(right)]
}
console.log(QuickSort(arr))
```
# MergeSort
```javascript
function MergeSort(arr){
  if (arr.length < 2) return arr;
  let mid = Math.floor(arr.length/2);
  let leftArr = arr.slice(0,mid);
  let rightArr = arr.slice(mid)
  return slice(MergeSort(leftArr),MergeSort(rightArr))
}

function slice(leftArr,rightArr){
  const sortedArray = [];
  while(leftArr.length && rightArr.length){
    if(leftArr[0] <= rightArr[0]){
      sortedArray.push(leftArr.shift())
    }else{
      sortedArray.push(rightArr.shift())
    }
  }
  return [...sortedArray,...leftArr,...rightArr]
}
console.log(MergeSort(arr))
```
