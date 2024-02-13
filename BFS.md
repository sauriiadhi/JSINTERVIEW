```javascript
// Graph represented as an adjacency list
const graph = {
  'A': ['B', 'C'],
  'B': ['D', 'E'],
  'C': ['F'],
  'D': [],
  'E': ['F'],
  'F': []
};

function bfs(startNode) {
  const visited = {};
  const queue = [];

  // Initialize with the start node
  visited[startNode] = true;
  queue.push(startNode);

  while (queue.length !== 0) {
    const currentNode = queue.shift();
    console.log(currentNode);

    // Visit neighbors and enqueue unvisited neighbors
    graph[currentNode].forEach(neighbor => {
      if (!visited[neighbor]) {
        visited[neighbor] = true;
        queue.push(neighbor);
      }
    });
  }
}

// Example usage
bfs('A');

```
