[< BACK TO INDEX](README.md)

In JavaScript, the task of creating a new array that is populated with the contiguous pairwise (any 2 neighboring elements) sums of the elements of an iterable can be accomplished by using a generator function.

Here is an example of how to accomplish this in JavaScript:
```javascript
function* pairwiseSums(iterable) {
    for (let i = 0; i < iterable.length - 1; i++) {
        yield iterable[i] + iterable[i + 1];
    }
}

let originalArray = [1, 9, 2, 4, 1, 4];
let newArray = [];
let pairwiseSumsGenerator = pairwiseSums(originalArray);
for(let num of pairwiseSumsGenerator) {
  newArray.push(num);
}
console.log(newArray);
```
In this example, the generator function pairwiseSums takes an iterable as its input. It uses a for loop to iterate through the elements of the input iterable, and for each iteration, it yield the sum of the element at the current index and the element at the next index.

You can use this generator function to generate an iterable of pairwise sums by calling the next() method on the generator object. Each time next() method is called, the generator function resumes execution from where it left off and returns the next pairwise sum in the sequence.

In summary, the task of creating a new array that is populated with the contiguous pairwise sums of the elements of an iterable can be accomplished by using a generator function.
It allows to iterate over the elements of an array, calculating the sum of the element and the next element and returning the result one by one, allowing you to work with large collections of data and do not want to load all the data into memory at once.