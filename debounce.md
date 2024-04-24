```javascript
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Debouncing Example</title>
<style>
  #searchInput {
    width: 300px;
    padding: 8px;
    font-size: 16px;
  }
</style>
</head>
<body>
  <h1>Debouncing Example</h1>
  <input type="text" id="searchInput" placeholder="Type something...">
  <div id="searchResults"></div>

  <script>
    function debounce(func, delay) {
      let timeoutId;

      return function(...args) {
        const context = this;

        clearTimeout(timeoutId);
        timeoutId = setTimeout(() => {
          func.apply(context, args);
        }, delay);
      };
    }

    function performSearch(query) {
      document.getElementById('searchResults').innerText = `Searching for: ${query}`;
      // Perform search operation here
    }

    const debouncedSearch = debounce(performSearch, 300); // Debounce search function with a delay of 300ms

    document.getElementById('searchInput').addEventListener('input', function(event) {
      debouncedSearch(event.target.value); // Call debounced search function on input change
    });
  </script>
</body>
</html>
```
