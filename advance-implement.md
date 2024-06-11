```javascript 
//Method chaining in JavaScript
const ComputeAmount = function(){
  
  return {
    store: 0,
    crore: function(val){
      this.store += val * Math.pow(10, 7);
      return this;
    },

    lacs: function(val){
      this.store += val * Math.pow(10, 5);
      return this;
    },

    thousand: function(val){
      this.store += val * Math.pow(10, 3);
      return this;
    },

    hundred: function(val){
      this.store += val * Math.pow(10, 2);
      return this;
    },

    ten: function(val){
      this.store += val * 10;
      return this;
    },

    unit: function(val){
      this.store += val;
      return this;
    },

    value: function(){
      return this.store;
    }
  }
}

const amount = ComputeAmount().lacs(9).lacs(1).thousand(10).ten(1).unit(1).value();
console.log(amount === 1010011);

//Retry promises N number of times

const wait = ms => new Promise((resolve) => {
setTimeout(() => resolve(), ms);
});

async function retryWithDelay (
    fn, retries = 3, interval = 50,
    finalErr = 'Retry failed'
) {

    try {
        // try
      console.log(`Attempt: ${retries}`);
        await fn();
    } catch (err) {
        // if no retries left
        // throw error
        if (retries <= 0) {
            return Promise.reject(finalErr);
        }
        //delay the next call
        await wait(interval);
        //recursively call the same func
        return retryWithDelay(fn, (retries - 1), interval, finalErr);
    }
}
const getTestFunc = () => {
    let callCounter = 0;
    return async () => {
        callCounter += 1;
        // if called less than 5 times
        // throw error
        if (callCounter < 5) {
            throw new Error('Not yet');
        }
      
    }
}
// Test the code
const test = async () => {
    await retryWithDelay(getTestFunc(), 10,1000);
    console.log('success');
    await retryWithDelay(getTestFunc(), 3,1000);
    console.log('will fail before getting here');
}
test().catch(console.error);


//Create Pausable auto incrementer

const timer = (init = 0, step = 1) => {
  let intervalId;
  let count = init;

  const startTimer = () => {
    if (!intervalId){
      intervalId = setInterval(() => {
        console.log(count);
        count += step;
      }, 1000);
    }
  }

  const stopTimer = () => {
    clearInterval(intervalId);
    intervalId = null;
  }

  return {
    startTimer,
    stopTimer,
  };
}
const timerObj = timer(10, 10);
timerObj.startTimer()
setTimeout(() => {
    timerObj.stopTimer();
}, 6000);
```
