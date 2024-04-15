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
```
