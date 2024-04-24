```javascript
function removeDuplicateslength(nums) {
  if (nums.length === 0) return 0;
  let i = 0;

  for (let j = 1; j < nums.length; j++) {
    if (nums[i] !== nums[j]) {
      i++;
      nums[i] = nums[j];
    }
  }

  return i + 1;
}
console.log(removeDuplicateslength([0, 0, 1, 1, 1, 2, 2, 3, 3, 4]));

function removeDuplicatesNew(nums) {
  if (nums.length === 0) return [];
  
  let uniqueArray = [];
  let seen = {};

  for (let i = 0; i < nums.length; i++) {
    if (!seen[nums[i]]) {
      seen[nums[i]] = true;
      uniqueArray.push(nums[i]);
    }
  }
  console.log(seen)

  return uniqueArray;
}

// Example usage
console.log(removeDuplicatesNew([0, 0, 1, 1, 1, 2, 2, 'hi', 'hi', 4]));
```
