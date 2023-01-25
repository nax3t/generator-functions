[< BACK TO INDEX](README.md)

Finding two consecutive entries in a list that sum to a specified value can be accomplished using a generator function in JavaScript.

Here is an example of how to accomplish this:
```javascript
function* findConsecutivePairs(iterable, target) {
    for (let i = 0; i < iterable.length - 1; i++) {
        if (iterable[i] + iterable[i + 1] === target) {
            yield [iterable[i], iterable[i + 1]];
        }
    }
}

let originalArray = [1, 9, 2, 4, 7, 4];
let targetSum = 11;
let pairsGenerator = findConsecutivePairs(originalArray, targetSum);
console.log(pairsGenerator.next().value); // [9, 2]
console.log(pairsGenerator.next().value); // [4, 7]
```
In this example, the generator function findConsecutivePairs takes an iterable and a target sum as its input. It uses a for loop to iterate through the elements of the input iterable, and for each iteration, it checks if the sum of the element at the current index and the element at the next index equals the target sum. If it does, it yields a new array containing the pair of elements.

You can use this generator function to generate an iterable of pairs that sum to the target value by calling the next() method on the generator object. Each time next() method is called, the generator function resumes execution from where it left off and returns the next pair that sums to the target value in the sequence.

In summary, the task of finding two consecutive entries in a list that sum to a specified value can be accomplished using a generator function in JavaScript. It allows to iterate over the elements of an array, checking if the sum of the element and the next element is equal to the target sum, and returning the pair one by one, allowing you to work with large collections of data and only returning the pairs that match the target sum.