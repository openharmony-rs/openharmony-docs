---
kits: ["ArkTS Kit"]
description: "Introduces ArkTS collection types, including arrays, tuples, Set, Map, and read-only collections, and explains iteration and collection selection for different scenarios."
keywords: ["collection types", "arrays", "Array", "Map", "tuples", "Set", "forEach", "ReadonlyArray", "iterators"]
doctype: guide
status: active
---

# Collection Types
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=8923bda514baa1452b967ea964ea779c7417bd8e translatedAt=2026-11-12T12:34:02.308Z pushedAt=2026-10-30T06:21:33.935Z nl=1 -->

Collection types store multiple data items. ArkTS provides arrays, tuples, `Set`, `Map`, and other collection types, each with specific uses and characteristics. Understanding the differences among the three core collections is essential for choosing a type: an array (`Array`) is an ordered list that allows duplicate elements, supports index-based access, and suits ordered data; a set (`Set`) stores unique elements and suits deduplication and membership checks; a map (`Map`) stores key-value pairs with keys of any type and suits fast value lookup by key. Collections can also be classified by mutability as mutable or read-only (such as `ReadonlyArray`).

## Array

An array is the most commonly used data structure for storing an ordered collection of elements. Elements in an array are arranged by index, starting from 0, and can be dynamically added and removed.

Arrays are commonly used to store ordered data lists (such as user lists, product lists, and log records), represent sequence data (such as time series and event streams), process batch data (such as batch operations, batch conversions, and batch queries), or serve as stacks or queues (such as task queues and history records). Their core characteristics include: elements are stored in insertion order with indexes starting from 0 (ordering), elements can be dynamically added, removed, and modified (mutability), all elements must be of the same type or a union type (type constraint), and the length can change at any time (dynamic length).

### Array Declaration and Initialization

An array can be created using a literal or a constructor. Specify the element type at declaration to ensure type safety.

<!-- @[array_creation_methods](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
// Use the type suffix []
let numbers: number[] = [1, 2, 3, 4, 5];
let strings: string[] = ['a', 'b', 'c'];
let booleans: boolean[] = [true, false, true];

// Use the generic Array
let numbers2: Array<number> = [1, 2, 3];
let strings2: Array<string> = ['hello', 'world'];

// Empty array
let empty: number[] = [];
let empty2: string[] = [];

// Union type array
let mixed: (number | string)[] = [1, 'two', 3, 'four'];
let nullable: (number | null)[] = [1, null, 3];

// Create using the spread operator
let original: number[] = [1, 2, 3];
let copy: number[] = [...original];
let extended: number[] = [...original, 4, 5];
```

`number[]` and `Array<number>` are functionally equivalent. The `number[]` form is recommended because it is more concise, while the `Array<T>` syntax is suitable for scenarios where generics need to be emphasized. The spread operator `...original` creates a new array, and modifying the copy does not affect the original array.

### Accessing and Modifying Array Elements

Array elements are accessed and modified by index, commonly used in scenarios such as reading values, updating data, data processing, and runtime state updates.

<!-- @[array_element_access](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let arr: number[] = [10, 20, 30, 40, 50];

// Read an element.
let first: number = arr[0];   // 10
let second: number = arr[1];  // 20
let last: number = arr[arr.length - 1];  // 50

// Modify an element.
arr[0] = 100;
arr[1] = 200;
console.info(`${arr.join(', ')}`);  // 100, 200, 30, 40, 50

// Access out of bounds.
let outOfBounds: number | undefined = arr[10];
console.info(`${outOfBounds}`);  // undefined

// Safe access
let index: number = 5;
if (index >= 0 && index < arr.length) {
  let safe: number = arr[index];
}
```

Accessing an array out of bounds returns `undefined` instead of throwing an exception. Therefore, perform a boundary check before accessing an index that is not guaranteed to be valid.

### Iterating Over an Array

Array iteration is commonly used for data processing, searching, statistics, and transformation. When choosing an approach: use `for...of` when you only need the value, use a `for` loop when you need the index, use `forEach` for functional-style processing, and do not modify the array length during iteration.

<!-- @[array_for_loop_iteration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let iterArr: number[] = [1, 2, 3, 4, 5];

for (let value of iterArr) {
  console.info(`${value}`);
}

// Obtain the index and value.
for (let i = 0; i < iterArr.length; i++) {
  console.info(`Index ${i}: ${iterArr[i]}`);
}
```

The `forEach` method iterates over an array in a functional style and executes a callback for each element:

<!-- @[array_forEach_method](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let forEachArr: number[] = [1, 2, 3];

forEachArr.forEach((value: number, index: number): void => {
  console.info(`Index ${index}: ${value}`);
});
```

`forEach` does not support `break`. Use a `for...of` or `for` loop when you need to exit iteration early.

<!-- @[array_indexed_iteration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let iterArr2: number[] = [1, 2, 3];

for (let i = 0; i < iterArr2.length; i++) {
  console.info(`${iterArr2[i]}`);
}
```

To control iteration manually, obtain an iterator with `values()` and retrieve values one at a time with `next()`:

<!-- @[array_iterator_manual](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let manualArr: number[] = [1, 2, 3];
let arrIter: IterableIterator<number> = manualArr.values();

let iterResult: IteratorResult<number> = arrIter.next();
while (!iterResult.done) {
  console.info(`${iterResult.value}`);  // Outputs 1, 2, 3 in sequence.
  iterResult = arrIter.next();
}
```

### Common Array Operations

Arrays provide common methods such as `push`, `pop`, `shift`, and `splice` to add, remove, modify, and query elements.

<!-- @[array_add_elements](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let elemArr: number[] = [1, 2];

// push: append to the end
elemArr.push(3);
elemArr.push(4, 5);  // can add multiple
let newLength: number = elemArr.push(6);  // return the new length

// unshift: add to the beginning
elemArr.unshift(0);
elemArr.unshift(-1, -2);  // can add multiple elements

console.info(`${elemArr.join(', ')}`);  // -1, -2, 0, 1, 2, 3, 4, 5, 6
```

Use methods such as `pop`, `shift`, and `splice` to remove elements:

<!-- @[array_remove_elements](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let elemArr2: number[] = [1, 2, 3, 4, 5];

// pop: delete from the end
let elemLast: number | undefined = elemArr2.pop();  // 5
console.info(`${elemArr2.join(', ')}`);  // 1, 2, 3, 4

// shift: delete from the beginning
let elemFirst: number | undefined = elemArr2.shift();  // 1
console.info(`${elemArr2.join(', ')}`);  // 2, 3, 4

// splice: delete the specified position
let removed: number[] = elemArr2.splice(1, 2);  // Delete the two elements starting from index 1.
console.info(`${elemArr2.join(', ')}`);  // 2
console.info(`${removed.join(', ')}`);  // 3, 4
```

The `concat` and `slice` methods are used to concatenate and extract arrays. Both return a new array without modifying the original array:

<!-- @[array_concat_and_slice](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let arr1: number[] = [1, 2];
let arr2: number[] = [3, 4];

// concat: concatenate arrays
let combined: number[] = arr1.concat(arr2);
console.info(`${combined.join(', ')}`);  // 1, 2, 3, 4
let concatExtended: number[] = arr1.concat(3, 4, [5, 6]);
console.info(`${concatExtended.join(', ')}`);  // 1, 2, 3, 4, 5, 6

// slice: split/extract
let sliceArr: number[] = [1, 2, 3, 4, 5];
let sub: number[] = sliceArr.slice(1, 4);
console.info(`${sub.join(', ')}`);  // 2, 3, 4
let tail: number[] = sliceArr.slice(2);
console.info(`${tail.join(', ')}`);  // 3, 4, 5
let sliceCopy: number[] = sliceArr.slice();
console.info(`${sliceCopy.join(', ')}`);  // 1, 2, 3, 4, 5 (copy)
```

The search and filter methods of an array include `indexOf`, `includes`, `find`, and `filter`:

<!-- @[array_search_and_filter](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let filterArr: number[] = [1, 2, 3, 2, 1];

// indexOf: Find the index.
let filterIndex: number = filterArr.indexOf(2);  // 1 (first match)
let lastIndex: number = filterArr.lastIndexOf(2);  // 3 (last match)
let notFound: number = filterArr.indexOf(10);  // -1

// includes: check whether it contains
let has2: boolean = filterArr.includes(2);  // true
let has10: boolean = filterArr.includes(10);  // false

// find: conditional search
let filterNumbers: number[] = [1, 5, 10, 15, 20];
let found: number | undefined = filterNumbers.find((value: number): boolean => {
  return value > 10;
});  // 15

let foundIndex: number = filterNumbers.findIndex((value: number): boolean => {
  return value > 10;
});  // 3

// filter: filter
let allNumbers: number[] = [1, 2, 3, 4, 5, 6];
let evens: number[] = allNumbers.filter((value: number): boolean => {
  return value % 2 === 0;
});
console.info(`${evens.join(', ')}`);  // 2, 4, 6

let greaterThan3: number[] = allNumbers.filter((value: number): boolean => {
  return value > 3;
});
console.info(`${greaterThan3.join(', ')}`);  // 4, 5, 6
```

### Higher-Order Array Operations

Arrays also provide functional methods such as `map` (mapping), `filter` (filtering), `reduce` (reduction), `sort`/`reverse` (sorting), and `flat`/`flatMap` (flattening). These methods can be chained into a filter-transform-aggregate data processing pipeline. They return new arrays without modifying the original array, except for `sort` and `reverse`.

`map`: mapping each element

`map` applies a transformation to each element of the array and returns a new array.

<!-- @[array_map](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let amNumbers: number[] = [1, 2, 3, 4, 5];

let amDoubled: number[] = amNumbers.map((n: number): number => n * 2);
console.info(`${amDoubled.join(', ')}`);  // 2, 4, 6, 8, 10

let amStrings: string[] = amNumbers.map((n: number): string => `Item ${n}`);
console.info(`${amStrings.join(', ')}`);  // 'Item 1, Item 2, Item 3, Item 4, Item 5'
```

`filter`: filtering elements

The `filter` method runs a predicate function on each element of the array and returns a new array consisting of all elements that satisfy the condition, while the original array remains unchanged. It is commonly used for data filtering, such as filtering active users from a user list or filtering on-sale products from a product list.

<!-- @[array_filter](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let afNumbers: number[] = [1, 2, 3, 4, 5, 6];

let afEvens: number[] = afNumbers.filter((n: number): boolean => n % 2 === 0);
console.info(`${afEvens.join(', ')}`);  // 2, 4, 6
```

`reduce`: reducing an array

`reduce` reduces an array to a single value, and an initial value must be provided.

<!-- @[array_reduce](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let arNumbers: number[] = [1, 2, 3, 4, 5];

let arSum: number = arNumbers.reduce((acc: number, n: number): number => acc + n, 0);
console.info(`${arSum.toString()}`);  // 15

let arProduct: number = arNumbers.reduce((acc: number, n: number): number => acc * n, 1);
console.info(`${arProduct.toString()}`);  // 120
```

`sort` and `reverse`: sorting

The `sort` method sorts array elements in place and accepts a comparison function for custom sorting. The `reverse` method reverses the element order. Both modify the original array. To retain the original array, create a copy (for example, using `slice()` or the spread operator) before sorting.

<!-- @[array_sort](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let asNumbers: number[] = [3, 1, 4, 1, 5, 9, 2, 6];

let asAscending: number[] = [...asNumbers].sort((a: number, b: number): number => a - b);
console.info(`${asAscending.join(', ')}`);  // 1, 1, 2, 3, 4, 5, 6, 9

let asDescending: number[] = [...asNumbers].sort((a: number, b: number): number => b - a);
console.info(`${asDescending.join(', ')}`);  // 9, 6, 5, 4, 3, 2, 1, 1

let asReversed: number[] = [...asNumbers].reverse();
console.info(`${asReversed.join(', ')}`);  // 6, 2, 9, 5, 1, 4, 1, 3
```

Combining `map`, `filter`, and `reduce`

`map`, `filter`, and `reduce` can be combined through chained calls to implement a "filter → transform → aggregate" data processing pipeline. For example, use `filter` to select valid data, then `map` to extract key fields, and finally `reduce` to compute the aggregate value. In chained calls, each step returns a new array without affecting the original data.

<!-- @[array_chain](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let acPrices: number[] = [999, 25, 15, 75];

// Filter prices greater than 50, apply a 20% discount, and sum the results.
let acTotal: number = acPrices
  .filter((price: number): boolean => price > 50)
  .map((price: number): number => Math.round(price * 0.8))
  .reduce((acc: number, price: number): number => acc + price, 0);

console.info(`${acTotal}`);  // 859
```

`flat` and `flatMap`

`flat()` flattens nested arrays into a one-dimensional array and accepts a flattening depth. `flatMap()` applies a transformation to each element and then flattens the result by one level, equivalent to `map()` followed by `flat()`. It is commonly used to transform and flatten nested structures. The same effects can also be implemented manually using `reduce` and the spread operator.

<!-- @[flat_flatmap_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let ffnNested: number[][] = [[1, 2], [3, 4], [5, 6]];

// flat: Flatten a two-dimensional array into a one-dimensional array.
let ffnFlat: number[] = ffnNested.flat();
console.info(`${ffnFlat.join(', ')}`); // 1, 2, 3, 4, 5, 6

// flatMap: Map each element and then flatten by one level.
let ffnWords: string[] = ['hello world', 'foo bar'];
let ffnFlatMapped: string[] = ffnWords.flatMap((s: string): string[] => s.split(' '));
console.info(`${ffnFlatMapped.join(', ')}`); // 'hello, world, foo, bar'

// Use reduce and the spread operator instead of flat.
let ffnFlatReduce: number[] = ffnNested.reduce((acc: number[], arr: number[]): number[] => {
  return [...acc, ...arr];
}, []);
console.info(`${ffnFlatReduce.join(', ')}`); // 1, 2, 3, 4, 5, 6
```

## Tuple

A tuple is an ordered collection with a fixed length and fixed types. A tuple differs from an array: a tuple has a fixed length and each position can have a different type, whereas an array has a variable length and all elements share the same type.

- Represent data with a fixed structure, such as a coordinate point `[x, y]` or an RGB color `[r, g, b]`.
- Return multiple values, such as a function returning `[result, error]`.
- Represent a key-value pair, such as `[key, value]`.
- Defines data of specific types at specific positions (for example, `[id, name, age]`).

### Tuple Declaration and Initialization

A tuple is declared by explicitly specifying the element type at each position, with a fixed length and type sequence.

<!-- @[tuple_basics](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let tuple: [number, string] = [1, 'hello'];
let coordinate: [number, number] = [10, 20];
let user: [number, string, boolean] = [1, 'Alice', true];
```

In the type annotation above, the type at each position can be different, thereby expressing data with a fixed structure. In ArkTS, a simple fixed-length array can serve as a substitute for a tuple.

### Accessing Tuple Elements

Tuple elements are accessed by index. Each position has an explicit type, based on which the compiler performs type checking. Tuples are also commonly used to return multiple related values from a function.

<!-- @[tuple_element_access](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
// Index access.
let accessTuple: [number, string] = [1, 'hello'];
let num: number = accessTuple[0];    // 1
let str: string = accessTuple[1];    // 'hello'

// Access the tuple in array form.
let accessPair: number[] = [10, 20];
let accessFirst: number = accessPair[0];   // 10
let accessSecond: number = accessPair[1];  // 20
```

When accessing a tuple by index, the compiler retains precise type information for each position (for example, `accessTuple[0]` is `number` and `accessTuple[1]` is `string`). When using an array (such as `number[]`) to simulate a tuple, type information is less precise and bounds must be checked manually.

### Differences Between Tuples and Arrays

A tuple has a fixed length and a fixed sequence of types, whereas an array has a variable length and a uniform element type.

<!-- @[tuple_vs_array](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
// Tuple: fixed length and types
let point: [number, number] = [10, 20];  // Can contain only two numbers

// Array: variable length, uniform type
let tupleNumbers: number[] = [1, 2, 3, 4, 5];  // More number elements can be added.

// A tuple represents a fixed structure.
let userTuple: [number, string, boolean] = [1, 'Alice', true];
console.info(`${userTuple.join(', ')}`);  // '1, Alice, true'

// An array represents a dynamic collection.
let userIds: number[] = [1, 2, 3, 4, 5];
userIds.push(6);  // Can be added.
```

## Set

`Set` stores unique elements and is suitable for deduplication and membership checks. Unlike an array, a `Set` contains no duplicate elements.

### Set Declaration and Initialization

`Set` stores unique values. Create it using a constructor and specify the element type.

<!-- @[set_creation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
// Create an empty Set.
let emptySet: Set<number> = new Set();

// Create from an array.
let numbersSet: Set<number> = new Set([1, 2, 3, 4, 5]);

// Add initial elements.
let stringSet: Set<string> = new Set();
stringSet.add('a');
stringSet.add('b');
```

### Core Features of Set

`Set` ensures element uniqueness, automatically removes duplicates, and provides efficient membership checks.

<!-- @[set_uniqueness](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let set: Set<number> = new Set([1, 2, 2, 3, 3, 3]);
console.info(`${set.size}`);  // 3 (duplicates removed)

// Adding a duplicate element has no effect.
set.add(1);
console.info(`${set.size}`);  // 3 (unchanged)

// Remove duplicate elements from the array.
let uniqueArr: number[] = [1, 2, 2, 3, 3, 3];
let unique: number[] = Array.from(new Set(uniqueArr));
console.info(`${unique.join(', ')}`);  // 1, 2, 3
```

### Common Operations on Set

`Set` provides basic operations such as adding, deleting, searching, and iterating.

<!-- @[set_basic_operations](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let opsSet: Set<number> = new Set([1, 2, 3]);

// add: add an element (adding a duplicate has no effect).
opsSet.add(4);
let opsAddedSet: Set<number> = opsSet.add(5);  // Returns the Set itself.

// delete: remove an element and return whether it was removed.
let opsDeleteResult: boolean = opsSet.delete(2);  // true (removed successfully)
let opsRemoveResult: boolean = opsSet.delete(10); // false (not found)

// has: check whether an element exists.
let opsHas1: boolean = opsSet.has(1);   // true
let opsHas10: boolean = opsSet.has(10); // false

console.info(`${opsSet.size}`);  // 4 (elements are 1, 3, 4, 5)
```

Iterate over a `Set` using `for...of` or `forEach`, or obtain an iterator using `values()` or `keys()`:

<!-- @[set_iteration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let iterSet: Set<number> = new Set([1, 2, 3]);

// for...of loop
for (let value of iterSet) {
  console.info(`${value}`);
}

// forEach method
iterSet.forEach((value: number): void => {
  console.info(`${value}`);
});

// Obtain all values.
let values: IterableIterator<number> = iterSet.values();
for (let value of values) {
  console.info(`${value}`);
}

// Obtain all keys (in a Set, keys equal values).
let keys: IterableIterator<number> = iterSet.keys();
for (let key of keys) {
  console.info(`${key}`);
}
```

To control iteration manually, obtain an iterator with `values()` and retrieve values one at a time with `next()`:

<!-- @[set_iterator_manual](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let manualSet: Set<number> = new Set([1, 2, 3]);
let setIter: IterableIterator<number> = manualSet.values();

let setResult: IteratorResult<number> = setIter.next();
while (!setResult.done) {
  console.info(`${setResult.value}`);  // Outputs 1, 2, 3 in sequence.
  setResult = setIter.next();
}
```

A `Set` and an array can be converted to each other. Use the uniqueness of `Set` elements to remove duplicates from an array:

<!-- @[set_array_conversion](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
// Convert a Set to an array.
let convSet: Set<number> = new Set([1, 2, 3]);
let convArr: number[] = Array.from(convSet);
console.info(`${convArr.join(', ')}`);  // 1, 2, 3

// Convert an array to a Set.
let convNumbers: number[] = [1, 2, 2, 3];
let setFromArr: Set<number> = new Set(convNumbers);
console.info(`${Array.from(setFromArr).join(', ')}`);  // 1, 2, 3

// Remove duplicates.
let duplicates: number[] = [1, 1, 2, 2, 3, 3];
let convUnique: number[] = Array.from(new Set(duplicates));
console.info(`${convUnique.join(', ')}`);  // 1, 2, 3
```

The `clear` method removes all elements from a `Set`:

<!-- @[set_clear_method](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let clearSet: Set<number> = new Set([1, 2, 3]);
clearSet.clear();
console.info(`${clearSet.size}`);  // 0
```

### Higher-Order Set Operations

`Set` does not provide higher-order methods such as `map` and `filter`. Use `Array.from` to convert it to an array, apply the array's higher-order methods (see [Higher-Order Array Operations](#higher-order-array-operations)), and convert the result back to a `Set`:

<!-- @[set_high_order_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let hoSet: Set<number> = new Set([1, 2, 3, 4, 5]);

// Filter even numbers: convert the Set to an array, filter it, and convert back to a Set.
let hoEvens: Set<number> = new Set(
  Array.from(hoSet).filter((n: number): boolean => n % 2 === 0)
);
console.info(`${hoEvens.size}`);  // 2 (elements are 2, 4)
```

## Map

`Map` stores key-value pairs, where keys and values can be of any type.

### Map Declaration and Initialization

`Map` stores key-value pairs. Create it using a constructor and specify the key and value types.

<!-- @[map_creation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
// Create an empty Map.
let emptyMap: Map<string, number> = new Map();

// Create from an array (an array of key-value pairs).
let initMap: Map<string, number> = new Map([
  ['a', 1],
  ['b', 2],
  ['c', 3]
]);

// Add initial key-value pairs.
let map: Map<string, number> = new Map();
map.set('one', 1);
map.set('two', 2);
```

### Accessing, Adding, and Deleting Key-Value Pairs

`Map` uses `get`, `set`, and `delete` to access and modify key-value pairs, supporting dynamic data management.

<!-- @[map_basic_operations](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let opsMap: Map<string, number> = new Map();

// Add a key-value pair
opsMap.set('a', 1);
opsMap.set('b', 2);
opsMap.set('c', 3);

// Access a value
let valueA: number | undefined = opsMap.get('a');  // 1
let valueB: number | undefined = opsMap.get('b');  // 2
let opsNotFound: number | undefined = opsMap.get('x');  // undefined

// Check whether a key exists
let hasA: boolean = opsMap.has('a');  // true
let hasX: boolean = opsMap.has('x');  // false

// Delete the key-value pair.
let opsDeleted: boolean = opsMap.delete('b');  // true
let opsNotDeleted: boolean = opsMap.delete('x');  // false

// Update the value.
opsMap.set('a', 10);  // Update the value of 'a'.

// Clear the map.
opsMap.clear();
console.info(`${opsMap.size}`);  // 0
```

### Iterating Over a Map

Use `forEach` or `for...of` to iterate over the keys, values, or key-value pairs of a `Map`.

<!-- @[map_iteration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let iterMap: Map<string, number> = new Map([
  ['a', 1],
  ['b', 2],
  ['c', 3]
]);

// Iterate using forEach
iterMap.forEach((value: number, key: string): void => {
  console.info(`${key}: ${value}`);
});

// Iterate entries using for...of
for (let entry of iterMap.entries()) {
  let key: string = entry[0];
  let value: number = entry[1];
  console.info(`${key}: ${value}`);
}

// Iterate keys using for...of
for (let key of iterMap.keys()) {
  console.info(`${key}`);
}

// Iterate values using for...of.
for (let value of iterMap.values()) {
  console.info(`${value}`);
}

// Iterate without destructuring and explicitly read the entry element.
for (let entry of iterMap.entries()) {
  let key: string = entry[0];
  let value: number = entry[1];
  console.info(`${key}: ${value}`);
}
```

To control iteration manually, obtain an iterator with `entries()` and retrieve values one at a time with `next()`:

<!-- @[map_iterator_manual](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let manualMap: Map<string, number> = new Map([['a', 1], ['b', 2]]);
let mapIter: IterableIterator<[string, number]> = manualMap.entries();

let mapResult: IteratorResult<[string, number]> = mapIter.next();
while (!mapResult.done) {
  let entry: [string, number] = mapResult.value;
  console.info(`${entry[0]}: ${entry[1]}`);  // Outputs a: 1, b: 2 in sequence.
  mapResult = mapIter.next();
}
```

### Record<K,V> Type
<a id="recordkv-type"></a>

`Record<K, V>` is a built-in ArkTS utility type that maps key type `K` to value type `V`. It is suitable for representing objects with string keys. When keys are limited to strings or numbers and the structure is relatively simple, it is more lightweight than `Map` and is commonly initialized with an object literal.

<!-- @[record_type_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let ages: Record<string, number> = {
  'John': 25,
  'Mary': 21
};
ages['John']; // 25
```

The key type `K` can be `string` or `number` (excluding `bigint`), and the value type `V` can be any type. Reading by subscript returns `V | undefined`, so you must check for null before use.

When the value is a composite structure, you can use an interface to describe its shape:

<!-- @[record_type_complex](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
interface PersonInfo {
  age: number;
  salary: number;
}
let staff: Record<string, PersonInfo> = {
  'John': { age: 25, salary: 10},
  'Mary': { age: 21, salary: 20}
};
```

Compared with `Map`, `Record` is based on object literals, its keys can only be strings or numbers, it has no `size` property (you must use `Object.keys(obj).length` to compute it), and it does not support keys of arbitrary types. When you need keys of arbitrary types, dynamic addition and removal of key-value pairs, or preservation of insertion order, prefer `Map` (see [Differences Between Map and Ordinary Objects](#differences-between-map-and-ordinary-objects)).

### Differences Between Map and Ordinary Objects

`Map` keys can be of any type, whereas object keys can only be strings. `Map` is more suitable for dynamic key-value storage.

<!-- @[map_vs_object](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
// Map: any key type
let numKeyMap: Map<number, string> = new Map();
numKeyMap.set(1, 'one');
numKeyMap.set(2, 'two');

class KeyObject {
  public id: number;

  constructor(id: number) {
    this.id = id;
  }
}

let objMap: Map<KeyObject, string> = new Map();
let keyObj: KeyObject = new KeyObject(1);
objMap.set(keyObj, 'value');

// Record: suitable for expressing string-keyed objects
let obj: Record<string, number> = {};
obj['key1'] = 1;
obj['key2'] = 2;

let objValue: number | undefined = obj['key1'];
if (objValue !== undefined) {
  console.info(`${objValue}`);
}

// Map: preserves order
let orderedMap: Map<string, number> = new Map();
orderedMap.set('a', 1);
orderedMap.set('b', 2);
orderedMap.set('c', 3);
console.info(`${Array.from(orderedMap.keys()).join(', ')}`);  // a, b, c (order preserved)

// Map: obtain the size directly.
console.info(`${orderedMap.size}`);  // 3

// Object: compute the size.
let objSize: number = Object.keys(obj).length;
```

### Higher-Order Map Operations

`Map` does not provide higher-order methods such as `map` and `filter`. Use `Array.from` to convert it to an array, apply the array's higher-order methods (see [Higher-Order Array Operations](#higher-order-array-operations)), and convert the result back to a `Map`:

<!-- @[map_high_order_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let hoMap: Map<string, number> = new Map([['a', 1], ['b', 2], ['c', 3]]);

// Filter entries with values greater than 1: convert the Map to an array, filter it, and convert back to a Map.
let hoFiltered: Map<string, number> = new Map(
  Array.from(hoMap).filter((entry: [string, number]): boolean => entry[1] > 1)
);
console.info(`${hoFiltered.size}`);  // 2 ('b', 'c')

// Sum all values.
let hoTotal: number = Array.from(hoMap.values()).reduce(
  (acc: number, value: number): number => acc + value, 0
);
console.info(`${hoTotal}`);  // 6
```

## Read-only Collection Types

Read-only collection types prohibit modification operations and are suitable for passing immutable data.

### Read-Only Arrays

Declare a read-only array using `readonly number[]`, which is equivalent to `ReadonlyArray<number>`. It permits reads but prohibits modifications such as `push` and `pop`.

<!-- @[readonly_array_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
// readonly number[] and ReadonlyArray<number> are equivalent.
let readonlyArr: readonly number[] = [1, 2, 3];
let sameArr: ReadonlyArray<number> = readonlyArr;

// Read-only
// readonlyArr.push(4);   // Compilation error
// readonlyArr[0] = 10;   // Compilation error

// Can be read.
let roFirst: number = readonlyArr[0];       // 1
let roLength: number = readonlyArr.length;  // 3

// A mutable array can be assigned to a read-only array (one-way assignment).
let mutableNums: number[] = [1, 2, 3];
let readonlyNums: readonly number[] = mutableNums;
```

### Read-only Map and Read-only Set

Read-only collections are declared through the `ReadonlyMap` or `ReadonlySet` type to prevent accidental modification. `ReadonlyMap` and `ReadonlySet` are built-in read-only interfaces in ArkTS.

<!-- @[readonly_map_set_interfaces](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
// Use the built-in ReadonlyMap to return a read-only view.
function getReadOnlyMap(): ReadonlyMap<string, number> {
  let map: Map<string, number> = new Map();
  map.set('a', 1);
  return map;  // Return a read-only view.
}

// Use the built-in ReadonlySet to return a read-only view.
function getReadOnlySet(): ReadonlySet<number> {
  let set: Set<number> = new Set([1, 2, 3]);
  return set;  // Return a read-only view.
}
```

### Read-Only Tuples

A read-only tuple ensures that its data is not modified. It is suitable for scenarios such as configuration data, constant coordinates, and function parameter protection, where the compiler enforces checks on modification operations.

<!-- @[readonly_tuple](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let readonlyTuple: readonly [number, string] = [1, 'hello'];
// readonlyTuple[0] = 2;  // Compilation error
```

### When to Use Read-only Collections

Read-only collections are suitable for scenarios where data should not be modified, such as configuration data and constant lists.

<!-- @[readonly_collection_scenarios](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
// Configuration data: read-only, to prevent accidental modification.
const CONFIG: ReadonlyArray<string> = ['api', 'db', 'cache'];

// Function parameters: read-only, to protect the original data.
function processItems(items: ReadonlyArray<number>): number {
  let sum: number = 0;
  for (let item of items) {
    sum += item;
  }
  return sum;
}

let scenariosNumbers: number[] = [1, 2, 3];
processItems(scenariosNumbers);  // Pass a read-only view.

// Return a read-only result to prevent external modification.
function getConstants(): ReadonlyArray<string> {
  return ['CONST_A', 'CONST_B'];
}
```

## ArkTS Shared Containers (@arkts.collections)

In addition to the native collection types described here, ArkTS provides shared containers based on the `@arkts.collections` module (such as `collections.Array`, `collections.Map`, and `collections.Set`) for high-performance data transfer across Worker threads in concurrent scenarios. Import them using `import { collections } from '@kit.ArkTS';` (supported since API version 12 and available only in .ets files).

The main differences between shared containers and native collection types are as follows:

- **Transfer behavior**: Native collections are copied by value when transferred across threads (for example, to a `Worker`), so changes in one thread do not affect another. Shared containers are passed by reference between concurrent instances by default, allowing multiple concurrent instances to operate on the same container instance and avoiding repeated copies of large amounts of data.
- **Thread safety**: Shared containers are not thread-safe. They use a fail-fast mechanism that throws an exception when structural modifications by multiple concurrent instances are detected. Use asynchronous locks to ensure safe multithreaded reads and writes. Native collections are used only within a single thread and do not have this issue.
- **Property restrictions**: Properties cannot be added or updated on shared container instances using `.` or `[]`.
- **Selection guidance**: Use native collections for single-threaded scenarios. Use shared containers when data must be shared efficiently between `Worker` instances in concurrent scenarios.

For API details, see [@arkts.collections (ArkTS Containers)](../reference/apis-arkts/arkts-apis-arkts-collections.md).

## TypedArray

TypedArray is a family of array types optimized for numerical computation, including Int8Array, Uint8Array, Int16Array, Uint16Array, Int32Array, Uint32Array, and Float32Array. Each type stores numbers of a fixed bit width (for example, Int8Array stores 8-bit signed integers and Float32Array stores 32-bit floating-point numbers). Elements are contiguous in memory and require no boxing.

A regular array (`Array`) has a dynamically variable length, stores references for object elements, and incurs boxing and type-checking overhead when accessing numeric elements. In contrast, TypedArray stores raw numeric values directly, reducing access and computation overhead. Use TypedArray for purely numerical computation, such as image pixel processing, audio sample data, and scientific computing. Regular arrays suit general-purpose data such as objects and strings.

For TypedArray use cases and performance comparisons, see [High-Performance Programming Guide](arkts-high-performance-programming.md).

## Common Operations Quick Reference

The following tables summarize common operations by type and indicate whether each operation modifies the original collection in place or returns a new collection or value:

**Common array operations**

| Type | Operation | Behavior |
| --- | --- | --- |
| Array | `push`, `unshift`, `pop`, `shift`, `splice` | Modifies in place |
| Array | `sort`, `reverse` | Modifies in place |
| Array | `concat`, `slice`, `map`, `filter`, `flat`, `flatMap` | Returns a new array |
| Array | `reduce` | Returns the reduced value without modifying the original array |
| Array | `indexOf`, `includes`, `find`, `findIndex` | Returns the query result without modifying the original array |

**Common Set/Map and conversion operations**

| Type | Operation | Behavior |
| --- | --- | --- |
| `Set` | `add`, `delete`, `clear` | Modifies in place |
| `Set` | `has` | Returns the query result without modifying the original collection |
| `Map` | `set`, `delete`, `clear` | Modifies in place |
| `Map` | `get`, `has` | Returns the query result without modifying the original collection |
| Conversion | `Array.from(set)`, `Array.from(map)` | Returns a new array |
| Conversion | `new Set(arr)`, `new Map(entries)` | Returns a new collection |

## Procedure

1. Determine the data relationship: use `Array` for ordered lists, `Set` for collections of unique values, `Map` for key-value indexing, and prefer explicit interfaces or tuples for fixed-length data structures where positions correspond to types.
2. Specify element types: declare concrete types for array and `Set` elements and `Map` keys and values. Do not use `any` or `unknown` for collection contents.
3. Define mutability boundaries: use `readonly T[]` (equivalent to `ReadonlyArray<T>`) when a function only reads a collection. Restrict modifications to the creator or dedicated update functions.
4. Choose an access method: Access results that may return `undefined`, such as array indexing, `find`, and `Map.get`, must be checked before use.
5. Choose an iteration method: Use `for...of` for read-only values, use `for` or `forEach` with type annotations when an index is needed, and explicitly read `entry[0]` and `entry[1]` when iterating over a `Map`.
6. Check ArkTS restrictions: Do not use destructuring assignment to iterate over collections, do not use object keys as ordinary object indexes, and do not directly expose mutable collections to callers that should not modify them.
