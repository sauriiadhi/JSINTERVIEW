```javascriptlet 
arr = [0, 1, 2, 3,9,8]

function sumOf(arr) {
  let res = [];
  for (let i = 0; i < arr.length; i++) {
    let sum = 0;
    for (let j = 0; j < arr.length; j++) {
      if (i !== j) {
        sum += arr[j]
      }
    }
    res.push(sum)
  }
  return res
}

console.log(sumOf(arr))

let obj1={a:1,b:2,c:3,e:3,d:5}
let obj2={a:0,b:4,c:3,d:5,e:3}

function similarObj(obj1,obj2){
  objres={};
  for(let i in obj1){
    if(obj1[i] === obj2[i]){
      objres[i] = obj1[i]
    }
  }
  return objres
}

console.log(similarObj(obj1, obj2))

function mergeObjectsWithBiggerValue(obj1, obj2) {
  let mergedObj = {};

  for (let key in obj1) {
    mergedObj[key] = Math.max(obj1[key], obj2[key]);
  }

  for (let key in obj2) {
    if (!(key in obj1)) {
      mergedObj[key] = obj2[key];
    }
  }

  return mergedObj;
}

console.log(mergeObjectsWithBiggerValue(obj1, obj2))

function secondSmall(arr){
  let L = Math.max(arr[0], arr[1]);
  let sL = Math.min(arr[0], arr[1]);
  for(let i=2;i<arr.length;i++){
    if(arr[i] > L){
      sL = L;
      L =arr[i];
    } else if (arr[i] > sL && arr[i] !== L){
      sL = arr[i];
    }
  }
  return sL
}

console.log(secondSmall([4,4]))


function rotate(arr,k){
  if(k>arr.length){
    k = k % arr.length;
  }
  let newArr = arr.splice(arr.length-k,k);
  arr.unshift(...newArr)
  return arr
}
console.log(rotate([4, 4,5,7],2))


let oddArr = [3,5,7,9,13,17]

function findOdd(arr){
  let min = Math.min(...arr)
  let max = Math.max(...arr)
  let missingno;
  for (let i=min;i<max;i++){
    if(i % 2 && !arr.includes(i)){
      missingno = i; break;
    } 
  }
  return missingno
}

console.log(findOdd(oddArr))

let str ="this is coolo"

function rev(str){
  return str.split(" ").map((item)=> {
    return item.split("").reverse().join("")
  }).join(" ")
}

console.log(rev(str))

function repeatingChar(char){
  let charMap = {};
  let maxStr= '';
  let maxCount = 0;

  for (let chars of char.replace(/\s/g, '')){
    charMap[chars] = charMap[chars] ? charMap[chars]+1 : 1;
  }

  for (let char in charMap){
    if (charMap[char] > maxCount){
      maxCount = charMap[char];
      maxStr = char
    }
  }
  console.log("maxrepeted:",maxStr)
}

repeatingChar(str)

```
