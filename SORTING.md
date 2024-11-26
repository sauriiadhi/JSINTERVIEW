#BubbleSort
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
