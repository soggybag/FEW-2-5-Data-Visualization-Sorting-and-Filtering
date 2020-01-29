# FEW 2.5 Data Visualization With JS sorting and filtering 

Sometimes you need to sort and filter data. You do it everyday in your head. Often you need to do it in code. In code it follows the same processes that you would use in your head. 

## Sorting 

Array.sort() is a method that looks at two element from a collection and decies which element should come before the other. 

By default is makes the decision alphabetically. For strings this works. 

```JS
const arr = 'javascript'.split('')
arr.sort()
console.log(arr) // ["a", "a", "c", "i", "j", "p", "r", "s", "t", "v"]
```

For numbers you''ll get: 

`console.log([9,10,22,333,4,55].sort()) // [10, 22, 333, 4, 55, 9]`

Which is usually not what you expect. 

Provide sort witb with a compare function. This function should take two values (a and b) and return -1 (when a comes before b), 0 (when the order of the elements should not change), and +1 (when b comes before a). 

```JS
console.log([9,10,22,333,4,55].sort((a, b) => a - b)) 
// [4, 9, 10, 22, 55, 333]
```

## Creating a distribution 

A distribution shows the number of ocurrnaces of a value. Essentially this is counting the number of times a value appears in a dataset. 

There are several solutions, an easy way to create a distribution it to use an Object. Where the property/keys are the values and the values at each property/key is count. 

Here is a sample function that takes an array and returns an object. 

```JS
// Create a distribution 
function createDistribution(data) {
  return data.reduce((acc, value) => {
    if (acc[value] !== undefined) {
      acc[value] += 1
    } else {
      acc[value] = 1
    }
    return acc
  }, {})
}

console.log(createDistribution('javascript'.split('')))
// {j: 1, a: 2, v: 1, s: 1, c: 1, r:1, p:1, t:1}
```

You might want to convert the results, an object, into an array of 'rolls' and values. 

```JS
const d = [0, 1, 1, 3, 6, 6, 6, 7, 7, 8, 8, 8, 9, 9, 9, 10, 11, 12, 12, 12]
const dDist = createDistribution(d)
const dDist = []
const dArr = []
for(let key in dDist) {
  dArr.push({roll:Number(key), value: dDist[key]})
}
// The base distribution
console.log(dArr)
// Sort on rolls
dArr.sort((a,b) => a.roll - b.roll)
console.log(dArr.map(a => `${a.roll}, ${a.value}`))
// Sort on values 
dArr.sort((a,b) => a.value - b.value)
console.log(dArr.map(a => `${a.roll}, ${a.value}`))
```

## Filtering Data

[`Array.filter()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter) returns a new array that is a subset of the source array. 

Use Filter when you don't want to display everything or when you want to get matching values from a dataset. 

Filter takes a filter function that receives an element from the array, and should return true if the element should be included, and false if element should not be included. 

```JS 

```

