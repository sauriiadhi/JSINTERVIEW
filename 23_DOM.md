# Document Object Model

- Document Object Model, is a programming interface for web documents. It represents the structure of a document as a tree of objects, where each object corresponds to a part of the document, such as elements, attributes, and text. The DOM provides a way for programs to manipulate the structure, style, and content of HTML, XML, or XHTML documents dynamically

  

## Event delegation

- Event delegation is a programming pattern in JavaScript where instead of attaching an event listener to each individual element, you attach a single event listener to a common ancestor, typically a parent element, of all the elements you are interested in. This single event listener then watches for events that bubble up from the child elements, and based on the event target, it can take appropriate actions.

  

- The key idea behind event delegation is efficiency and simplicity. Rather than attaching multiple event listeners to many individual elements, you can use a single event listener on a common ancestor, reducing the amount of memory and making the code more maintainable.

## addEventListener
- The `addEventListener` method in JavaScript is used to attach an event handler function to an HTML element. It enables you to respond to events such as user actions (e.g., clicks, mouse movements, keyboard inputs) or other browser-related events.

### create and remove elements
- `document.createElement()`
- `innerHTML`
- `removeChild()`
- `remove`
- `parentNode.removeChild`

### event propagation

 1.  **Capturing Phase:**
-  During the capturing phase, the event travels from the outermost ancestor down 					to the target element.
-   It allows you to capture the event at a higher level in the DOM hierarchy before reaching the actual target

2.  **Target Phase:**
    
    -   The event reaches the target element, triggering the event listeners attached to that specific element.
3.  **Bubbling Phase:**
    
    -   After the target phase, the event starts to bubble up from the target element to the outermost ancestor.
    -   This phase allows you to handle the event as it propagates back up through the DOM.

When you use `addEventListener`, you have the option to specify whether you want to capture the event during the capturing phase (`true`) or during the bubbling phase (`false` or omitted, as it defaults to `false`).

Here's an example to illustrate event propagation:

```javascript
<div id="outer">
  <div id="middle">
    <button id="inner">Click me</button>
  </div>
</div>

<script>
  document.getElementById('outer').addEventListener('click', function () {
    console.log('Outer div clicked!');
  }, true);

  document.getElementById('middle').addEventListener('click', function () {
    console.log('Middle div clicked!');
  }, true);

  document.getElementById('inner').addEventListener('click', function () {
    console.log('Button clicked!');
  });
</script>
```

