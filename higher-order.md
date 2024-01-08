# what is higher-order function ?

- a higher-order function is a function that does at least one of the following:
    ## 1. Takes one or more functions as arguments.

    ``` javascript
    function multiplier(factor, fn) {
        return function(x) {
            return fn(x) * factor;
        };
    }

    // Example usage
    function square(x) {
        return x * x;
    }

    const double = multiplier(2, square);
    console.log(double(3));  // Output: 18 (3 * 3 * 2)
    ```

     ## 2. Returns a function as its result.

    ``` javascript
    function power(exp) {
        return function(x) {
            return Math.pow(x, exp);
        };
    }

    // Example usage
    const square = power(2);
    console.log(square(4));  // Output: 16 (4^2)

    const cube = power(3);
    console.log(cube(3));    // Output: 27 (3^3)
    ```