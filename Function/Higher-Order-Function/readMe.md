// HIGHER ORDER FUNCTIONS

A function which takes another function as an argument or returns a function is known as a higher order function.
Functional Programming is a paradigm of building computer programs using expressions and functions without mutating state and data.
paradigm means pattern or model

// MAP , FILTER , REDUCE
// Map array is used to create a new array from existing one by applying function to each one of element in the first array.

// filter array takes each array and applies a condition. If the condition returns true it get pushed into the output array if the condition returns false the elements doest not pushed into the output array.

// the reduce method reduces an array of values down to just one value.
// accumulator is basically the result of the previous computation - initial value
// If there is not intial value , it takes first element of array as value for accumulator

const numbers = [1, 2, 3, 4, 5];
// map() in Arrays
const newNum = numbers.map((item, index, array) => {
console.log(item, index, array);
// first is the item you have given in an array, second is the index of those arrays and lastly array is the orginal array you have given
return item \* 2;
});

console.log(newNum);
// filter() in Arrays

const newFilter = numbers.filter((item, index, array) => {
// filters are similar to maps but in filter you will have the condition and return only those condition if they met
return item > 3;
});
console.log(newFilter);

// reduce() in Arrays

const newReduce = numbers.reduce((prev, curr, index, array) => {
// reduces try to do it into one value
return prev + curr;
}, 0);
console.log(newReduce);

// some() in Arrays
// some is similar to the filter it will checks the condition and return every single items , in some it's going to return true or false

const newSome = numbers.some((item, index, array) => {
return item > 3;
});
console.log(newSome);

// every() in Arrays
// it will check if every condition is true if its not then it will return false
const newEvery = numbers.every((item, index, array) => {
return item > 3;
});
console.log(newEvery);

// find() in Arrays
const newFind = numbers.find((item) => {
// Returns the value of the first element in the array where item is true, and undefined otherwise.
return item > 3;
});
console.log(newFind);

const findNumber = [1, 2, 3, 4, 5];
// findIndex() in Arrays
const index = findNumber.findIndex((item) => item === 3);
console.log(index);
