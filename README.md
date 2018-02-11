JavaScript Natural Multisort
=======

Description
---------------
Based on javascript-natural-sort by Jim Palmer, JavaScript Natural Multisort adds support for "naturally" sorting arrays of objects by a property and also for sorting an array in descending order.

Usage
---------------
```javascript
var sortedArray = jsMultisort({array: array, property: "property", insensitive: insensitive, reverse: reverse});
```

* **array**: the array to be sorted
* **property**: the object property to sort on in string format, defaults to undefined
* **insensitive**: whether or not to ignore capitalization, defaults to false
* **reverse**: whether or not to sort in descending order, defaults to false

All configuration options are optional except for array. For example, if you want to sort a simple array in reverse order, you would use jsMultisort({array: array, reverse: true}).

**Note:** You can also sort an array of complex objects, but only on a property with a scalar value (not an array or an object) in the first dimension.

Tests
---------------
* [QUnit test suite](https://miyakoj.github.io/javascript-natural-multisort/unit-tests.html)
* [Speed tests](https://miyakoj.github.io/javascript-natural-multisort/speed-tests.html)


### By default - case-sensitive sorting

```javascript
>>> var sortedArray = jsMultisort({array: ['a', 'B']});
['B', 'a']
```

### Case-insensitive sorting
```javascript
>>> var sortedArray = jsMultisort({array: ['a', 'B']});
['a', 'B']
```

### Simple numerics

```javascript
>>> var sortedArray = jsMultisort({array: ['10', 9, 2, '1', '4']});
['1', 2, '4', 9, '10']
```

### Floats

```javascript
>>> var sortedArray = jsMultisort({array: ['10.0401', 10.022, 10.042, '10.021999']});
['10.021999', 10.022, '10.0401', 10.042]
```

### Float & decimal notation

```javascript
>>> var sortedArray = jsMultisort({array: ['10.04f', '10.039F', '10.038d', '10.037D']});
['10.037D', '10.038d', '10.039F', '10.04f']
```

### Scientific notation

```javascript
>>> var sortedArray = jsMultisort({array: ['1.528535047e5', '1.528535047e7', '1.528535047e3']});
['1.528535047e3', '1.528535047e5', '1.528535047e7']
```

### IP addresses

```javascript
>>> var sortedArray = jsMultisort({array: ['192.168.0.100', '192.168.0.1', '192.168.1.1']});
['192.168.0.1', '192.168.0.100', '192.168.1.1']
```

### Filenames

```javascript
>>> var sortedArray = jsMultisort({array: ['car.mov', '01alpha.sgi', '001alpha.sgi', 'my.string_41299.tif']});
['001alpha.sgi', '01alpha.sgi', 'car.mov', 'my.string_41299.tif']
```

### Dates

```javascript
>>> var sortedArray = jsMultisort({array: ['10/12/2008', '10/11/2008', '10/11/2007', '10/12/2007']});
['10/11/2007', '10/12/2007', '10/11/2008', '10/12/2008']
```

### Money

```javascript
>>> var sortedArray = jsMultisort({array: ['$10002.00', '$10001.02', '$10001.01']});
['$10001.01', '$10001.02', '$10002.00']
```

### Movie Titles

```javascript
>>> var sortedArray = jsMultisort({array: ['1 Title - The Big Lebowski', '1 Title - Gattaca', '1 Title - Last Picture Show']});
['1 Title - Gattaca', '1 Title - Last Picture Show', '1 Title - The Big Lebowski']
```

### Sorting a simple array of objects
```javascript
>>> var array = [
    {name: "antelope1", number: 1},
    {name: "elephant5", number: 5},
    {name: "jaguar10", number: 10},
    {name: "yeti25", number: 25},
    {name: "bear2", number: 2}
];
>>> var sortedArray = jsMultisort({array: array, property: "name"});
[
    {name: "antelope1", number: 1},
    {name: "bear2", number: 2},
    {name: "elephant5", number: 5},
    {name: "jaguar10", number: 10},
    {name: "yeti25", number: 25}
]
```

### Sorting an array of complex objects
```javascript
>>> var array = [
    {letter: 'a', animals: [{name: 'antelope', number: 1}, {name: 'alligator', number: 2}]},
    {letter: 'e', animals: [{name: 'elephant', number: 3}, {name: 'elk', number: 4}]},
    {letter: 'c', animals: [{name: 'cat', number: 5}, {name: 'canary', number: 6}]},
    {letter: 'b', animals: [{name: 'bear', number: 7}, {name: 'buffalo', number: 8}]},
    {letter: 'd', animals: [{name: 'dog', number: 9}, {name: 'dragon', number: 10}]}
];
>>> var sortedArray = jsMultisort({array: array, property: "letter"});
[
    {letter: 'a', animals: [{name: 'antelope', number: 1}, {name: 'alligator', number: 2}]},
    {letter: 'b', animals: [{name: 'bear', number: 7}, {name: 'buffalo', number: 8}]},
    {letter: 'c', animals: [{name: 'cat', number: 5}, {name: 'canary', number: 6}]},
    {letter: 'd', animals: [{name: 'dog', number: 9}, {name: 'dragon', number: 10}]},
    {letter: 'e', animals: [{name: 'elephant', number: 3}, {name: 'elk', number: 4}]}            
]
```