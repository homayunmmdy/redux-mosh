## Function as First Class Citizen

In javascript

- we can assign function into variable
- we can pass it as an argument
- we can also return function into another function

## Higher Order Functions

higher order function is function that takes the

- funtion as an argument
- or return the function

## Function Compositions

a powerful technique that allows developers to combine multiple functions into a single function

```javascript
let input = " JavaScript ";
const trim = (str) => str.trim();
const wrapInDiv = (str) => `<div>${str}</div>`;
const toLowerCase = (str) => str.toLowerCase();

const result = wrapInDiv(toLowerCase(trim(input)));
```

## Composing and Piping

```javascript
import { pipe } from "lodash/fp";

let input = " JavaScript ";
const trim = (str) => str.trim();
const wrapInDiv = (str) => `<div>${str}</div>`;
const toLowerCase = (str) => str.toLowerCase();

const transform = pipe(trim, toLowerCase, wrapInDiv);

transform(input);
```

## Currying

transforms a function with multiple arguments into a nested series of functions, each taking a single argument

```javascript
import { pipe } from "lodash/fp";

let input = " JavaScript ";
const trim = (str) => str.trim();
// const wrapInDiv = (str) => `<div>${str}</div>`;
const wrap = (type) => (str) => `<${type}>${str}</${type}>`;
const toLowerCase = (str) => str.toLowerCase();

const transform = pipe(trim, toLowerCase, wrap("dev"));

console.log(transform(input));
```

## Pure function

same (arg) => same (result)

we use theses in pure functions

- No random values
- No current date/time
- No global state (DOM , files , db , etc)
- No mutation of parameters

here are the benefits of the pure functions

- Self-documenting
- Easily testable
- Concurrency
- Cacheable

# Immutablitiy

Once created , cannot be changed!
const is not immutable we can't reassign it we can change it

<b>benefit of immutablity</b>

- Predictability
- Faster Changes detection
- Concurrency

<b>Cons</b>

- Performance
- Memmory overhead

## Update Object

the rest operator do shallow copy which like refrance in primitve and refrence values.

```javascript
const person = {
  name: "john",
  address: {
    country: "USA",
    citry: "San Francisco",
  },
};
const updated = { ...person, name: "Homayoun" };
console.log(updated);
```

if example if we change update like this and log person

```javascript
updated.address.city = "New York";
console.log(person)
```
we see that the city of person will change so we need to take deep copy for nested object

```javascript
const person = {
  name: "john",
  address: {
    country: "USA",
    citry: "San Francisco",
  },
};

const updated = {
  ...person,
  address: {
    ...person.address,
    city: "New York",
  },
  name: "Homayoun",
};
console.log(updated);
```

## Update Array
```javascript
const numbers = [1, 2, 3];

// Adding
const index = numbers.indexOf(2);
[...numbers.slice(0, index), 2, ...numbers.slice(index)];

// Removing
numbers.filter((n) => n !== 2);

// Updating
numbers.map((n) => (n === 2 ? 20 : n));


```