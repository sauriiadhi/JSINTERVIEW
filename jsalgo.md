```javascript 
function twoSum(arr,target){
  let nums = new Map();
  for(let i=0;i<arr.length;i++){
    let comp = target - arr[i]
    if(nums.has(comp)){
      return [nums.get(comp), i]
    }
    nums.set(arr[i],i)
  }
  return -1
}

console.log(twoSum([2, 7, 11, 15], 9)); 
console.log(twoSum([3, 2,3, 4], 6));  
console.log(twoSum([3, 3], 6));    

function productExceptSelf(arr){
  let length = arr.length;
  let product = new Array(length);
  product[0] = 1;
  for(let i=1;i<length;i++){
    product[i] = arr[i-1]*product[i-1]
  }
  let right = 1;
  for(let i=length-1;i>=0;i--){
    product[i] = product[i] * right;
    right *= arr[i]
  }
  return product
}

console.log(productExceptSelf([1, 2, 3, 4]))

function maxSubArray(arr){
  let max_current = arr[0]
  let max_global = arr[0]
  for(let i=1;i<arr.length;i++){
    max_current = Math.max(max_current+arr[i],arr[i]);
    max_global = Math.max(max_current,max_global)
  }
  return max_global
}
console.log(maxSubArray([-2, 1, -3, 4, -1, 2, 1, -5, 4]));

```
