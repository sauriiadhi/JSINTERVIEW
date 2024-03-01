## findWordWithMaxRepeatingChars
```javascript
function findWordWithMaxRepeatingChars(inputString) {
  const words = inputString.split(" ");
  let maxwords = '';
  let maxFreq = 0;
  words.forEach((word)=>{
    let maxFreqcount = 0;
    let maxFreqword = {};
    for(let letter of word){
      maxFreqword[letter] = (maxFreqword[letter] || 0) + 1;
      maxFreqcount = Math.max(maxFreqword[letter],maxFreqcount);
    }
    if(maxFreqcount > maxFreq){
      maxFreq = maxFreqcount;
      maxwords = word;
    }
  })
  return maxwords;
}
const inputString = "hello world balloon programming";
const result = findWordWithMaxRepeatingChars(inputString);
console.log(result);
```
