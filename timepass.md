```javascript
let count = 0;
(function (){
  if(count===0){
    let count = 1
    console.log(count)
  }
  console.log(count)
})()

function find(index){
  let a = [];
  for(let i=0;i <100000;i++){
    a[i] = i*i;
  }
  return function(index){
    console.log(a[index])
  };
}

let findtask = find()
console.time("6");
findtask(6);
console.timeEnd("6");

console.time("40");
findtask(40);
console.timeEnd("40");
function a(){
  for(var i=0;i<3;i++){
    function inner(ind){
      console.log(i)
    }
    setTimeout(inner(i),100)
  }
}
a()

function a(){
  for(var i=0;i<3;i++){
    (function(index){
      setTimeout(()=> {
      console.log(index)
    },100)
    })(i)
  }
}
a()
private counter in closure
function counter(){
  let _counter = 0;
  function add(increment){
    _counter += increment;
  }
  function retive(){
    return "counter:" + _counter
  }

  function reset(){
    _counter = 0;
  }

  return {add,retive,reset}
}

let oper = counter();
console.log(oper.retive())
console.log(oper)
oper.add(5)
oper.add(10)
console.log(oper.retive())
oper.reset()
console.log(oper.retive())


function once(func,context){
  let run;
  return function (){
    if(func){
      run = func.apply(context || this ,arguments);
      func = null
    }
    return run;
  };
}

const hell = once((a,b)=>console.log("hello",a,b))
hell(1,3)
hell()

function mymemo(func, context) {
  let res = {};
  return function (...args) {
    let argsCache = JSON.stringify(args);
    if (!res[argsCache]) {
      res[argsCache] = func.call(context || this, ...args);
    }
    return res[argsCache];
  };
}

let clumsy = function (...args) {
  let result = 0;
  for (let i = 0; i < 100000; i++) {
    for (let j = 0; j < args.length; j++) {
      result += args[j];
    }
  }
  return result;
};

let memo = mymemo(clumsy);

console.log(memo(1, 8, 9, 9));
function sum(...args) {
  if (args.length === 0) {
    return 0;
  } else if (args.length === 1) {
    return function(b) {
      return args[0] + b;
    };
  } else {
    return args.reduce((total, num) => total + num, 0);
  }
}

// Using currying
let addOne = sum(1);
console.log(addOne(4)); 
console.log(sum(1, 2, 3, 4)); 

// infinite currying

function add(a){
  return function(b){
    if (b) return add(a+b);
    return a;
  }
}

console.log(add(1)(1)(2)(3)(4)(2)(3)(4)())

function curry(func) {
  return function curriedFunc(...args) { 
    if(args.length >= func.length) {
      return func(...args)
    } else {
      return function(...next) {
        return curriedFunc(...args,...next);
      }
    }
  }
}

const join = (a, b, c) => {
   return `${a}_${b}_${c}`
}
const curriedJoin = curry(join)

curriedJoin(1, 2)(3) // '1_2_3'
function changeAgeAndReference(person) {
    person.age = 25;
    person = {
      name: 'John',
      age: 50
    };

    return person;
}

const personObj1 = {
    name: 'Alex',
    age: 30
};

const personObj2 = changeAgeAndReference(personObj1);

console.log(personObj1); // -> ?
console.log(personObj2); // -> ?
const arr = [0, 1, 2,2,,3,3,0];
let index = 0;

const intervalid = setInterval(()=>{
  if(arr.length > index){
    console.log(arr[index])
    index++
  }else{
    clearInterval(intervalid)
  }
},200)


let largest = arr[0];
let secondLargest = arr[1];

for(let i=2;i<arr.length;i++){
  if(arr[i] > largest){
    secondLargest = largest
    largest = arr[i];
  }else if(arr[i] > secondLargest && arr[i] !== largest){
    secondLargest = arr[i]
  }
}

console.log("Second largest element:", secondLargest);

let car = 41214;


function isPal(arr){
  return (car == car.toString().split("").reverse().join("")) ? console.log("palin") : console.log("not palin")
}

isPal(car)

function fiboS(n){
  let arr = [0,1];
  for(let i= 2; i<n;i++){
    arr.push(arr[i - 1] + arr[i - 2])
  }
  return arr;
}

console.log(fiboS(6))


const fib = (n) => {
  if(n<=1) return n;
  return fib(n-1) + fib(n-2)
}

console.log(fib(3))

let a = "anagram";
let b = "naagmr";

function isAna(a,b){
  if(a.length !== b.length) return false;
  let obj1 = {};
  let obj2 = {};
  for (let i=0;i<a.length;i++){
    obj1[a[i]] = (obj1[a[i]] || 0) + 1;
    obj2[b[i]] = (obj2[b[i]] || 0) + 1;
  }

  for (let k in obj1){
    if(obj1[k] !== obj2[k]) return false;
  }
  return true;
}

console.log(isAna(a,b))
function twoSum(arr,target){
  var obj = {};
  for (let i=0;i < arr.length; i++){
    let num = arr[i];
    if(obj[target - num] >= 0){
      return[obj[target - num],i]
    }else{
      obj[num] = i
    }
  }
  return -1
}

function rotateArrayOptimised(arr,k){
  let size = arr.length;
  if (size > k) {
    k = k % size
  }
  let newArr = arr.splice(size - k,k)
  arr.unshift(...newArr)
  return arr
}

console.log(rotateArrayOptimised([-1, -100, 3, 99], 2));
```
