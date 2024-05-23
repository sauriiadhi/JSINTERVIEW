```javascript
function PromiseFill(execute) {
  let isRes, isRej;
  let value;
  let isCalled = false;
  let isResolved = false;
  let isRejected = false;

  function resolve(val) {
    if (!isResolved && !isRejected) {
      isResolved = true;
      value = val;
      if (typeof isRes === 'function' && !isCalled) {
        isRes(value);
        isCalled = true;
      }
    }
  }

  function reject(val) {
    if (!isRejected && !isResolved) {
      isRejected = true;
      value = val;
      if (typeof isRej === 'function' && !isCalled) {
        isRej(value);
        isCalled = true;
      }
    }
  }

  this.then = function (cb) {
    isRes = cb;
    if (!isCalled && isResolved) {
      isRes(value);
      isCalled = true;
    }
    return this;
  };

  this.catch = function (cb) {
    isRej = cb;
    if (!isCalled && isRejected) {
      isRej(value);
      isCalled = true;
    }
    return this;
  };

  try {
    execute(resolve, reject);
  } catch (error) {
    reject(error);
  }
}

// Static method for Promise.all
PromiseFill.all = function (promises) {
  return new PromiseFill((resolve, reject) => {
    let results = [];
    let completed = 0;

    promises.forEach((promise, index) => {
      PromiseFill.resolve(promise).then((value) => {
        results[index] = value;
        completed += 1;

        if (completed === promises.length) {
          resolve(results);
        }
      }).catch(reject);
    });
  });
};

// Static method for Promise.race
PromiseFill.race = function (promises) {
  return new PromiseFill((resolve, reject) => {
    promises.forEach((promise) => {
      PromiseFill.resolve(promise).then(resolve).catch(reject);
    });
  });
};

// Static method to resolve a value or a promise
PromiseFill.resolve = function (value) {
  if (value instanceof PromiseFill) {
    return value;
  }
  return new PromiseFill((resolve) => resolve(value));
};

// Static method to reject a value
PromiseFill.reject = function (value) {
  return new PromiseFill((_, reject) => reject(value));
};

// Example

```
