# prevent modification of object

you can prevent modification of object properties in several ways. The goal is often to make certain properties read-only or to prevent the addition or removal of properties. Here are some techniques:

1.  **Object.freeze:** The `Object.freeze()` method prevents modifications to an object. This means you cannot add, update, or delete properties from the object, nor can you modify the values of its existing properties. It operates on the object itself and returns the frozen object.
    
```javascript
	var person = {
      name: "John",
      age: 25
    };
    
    Object.freeze(person);
    // Attempts to modify the object will not work
    person.age = 30; // This change will be ignored
    person.city = "New York"; // This addition will be ignored
   ```
    
2.  **Object.seal:** The `Object.seal()` method seals an object, preventing the addition or deletion of properties. While you can still modify existing property values, you cannot add new properties or remove existing ones.
    
```javascript
	var car = {
      brand: "Toyota",
      model: "Camry"
    };
    
    Object.seal(car);
    
    // Modifying existing properties is allowed
    car.model = "Corolla"; // This change is allowed
    
    // Adding or deleting properties is not allowed
    car.year = 2022; // This addition will be ignored
    delete car.brand; // This deletion will be ignored
   ```
    
3.  **Object.defineProperty:** The `Object.defineProperty()` method allows you to define or modify properties on an object. You can use this method to make properties read-only.
    
```javascript
	var laptop = {};
    
    Object.defineProperty(laptop, "brand", {
      value: "Dell",
      writable: false, // Make the property read-only
      enumerable: true
    });
    
    laptop.brand = "HP"; // This change will be ignored
   ```
    
   In this example, the `brand` property is made read-only by setting `writable: false`.
    

Choose the method that best fits your requirements based on whether you want to prevent modifications entirely (`Object.freeze`), allow modifications of existing properties but not addition or deletion (`Object.seal`), or make specific properties read-only (`Object.defineProperty`).