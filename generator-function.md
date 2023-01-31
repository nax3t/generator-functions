[< BACK TO INDEX](README.md)

A generator function in JavaScript is a special type of function that allows you to generate a sequence of values over time. It is defined using the `function*` keyword and it can use the `yield` keyword to return a value and pause execution. The function can then be resumed later on, allowing it to yield new values.

Here's an example of a simple generator function that generates a sequence of numbers:

```javascript
function* countGenerator() {
    let count = 0;
    while (true) {
        yield count;
        count++;
    }
}
```
You can use this generator function to generate an infinite sequence of numbers by calling the `next()` method on the generator object:

```javascript
let count = countGenerator();
console.log(count.next().value); // 0
console.log(count.next().value); // 1
console.log(count.next().value); // 2
```

One real-world use case for generator functions is implementing infinite scrolling on a web page. Instead of loading all the content at once, a generator function can be used to load a certain number of items at a time as the user scrolls down the page. This way, the website will not load all the items at once and will save memory.

Another use case is for an iterator object that can be used with the for...of loop. The generator function can create an iterator object that can be used to iterate through a collection of data, such as an array of items, without the need to load all the data into memory at once.

In summary, generator functions are a powerful tool in JavaScript that allow you to generate a sequence of values over time, and they are useful in creating iterator objects that can be used with the for...of loop.

### Additional examples
##### Pagination
```JS
function* getPage(list, pageSize = 1) {
  for (let index = 0; index < list.length; index += pageSize) {
    yield list.slice(index, index + pageSize);
  }
}

const list = [1, 2, 3, 4, 5, 6, 7, 8]
const page = getPage(list, 3);            // Generator { }

page.next();                              // { value: [1, 2, 3], done: false }
page.next();                              // { value: [4, 5, 6], done: false }
page.next();                              // { value: [7, 8], done: false }
page.next();                              // { value: undefined, done: true }
```

##### Passing a value to .next()
```JS
function* adder() {
  let num = 0;
  while (true) {
    num += yield num;
  }
}

const generator = adder();

console.log(generator.next().value); // 0
console.log(generator.next(5).value); // 5
console.log(generator.next(10).value); // 15
```