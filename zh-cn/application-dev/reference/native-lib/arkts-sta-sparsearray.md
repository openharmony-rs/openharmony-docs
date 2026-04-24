# SparseArray
SparseArray模块提供稀疏数组操作的基本方法。稀疏数组使用Map作为底层存储，这使其在处理包含许多空槽的数组时（如图、矩阵等）具有内存高效性。当数组某个位置没有元素时，则代表空洞。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 本模块首批接口从API version 24开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## length

get length(): int

获取稀疏数组的当前长度。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| int | 稀疏数组的当前长度，对应于内部的this.actualLength。|

**示例：**

```ts
const arr = new SparseArray<int>(10); // 初始长度为 10
console.info(arr.length); // 10
```

## length

set length(value: int)

设置稀疏数组的新长度。如果新长度小于当前长度，超出新长度的元素将被删除。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | int | 是 | 稀疏数组的目标新长度。|

**示例：**

```ts
const arr = new SparseArray<int>(1, 2, 3); // 初始长度 3
arr.length = 1; 
console.info(arr.length); // 1
```

## $_get

\$_get(index: int): T | undefined

获取索引index处的值。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| index | int | 是 | 待获取元素的稀疏数组索引。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| T \| undefined | 稀疏数组中指定索引处的元素值，如果索引越界或元素不存在，则返回undefined。|

**示例：**

```ts
const arr = new SparseArray<string>(3);
arr[0] = "A";
console.info(arr[0]); // "A"
console.log(arr[1]) // undefined
```

## $_set

\$_set(index: int, value: T): void

设置索引index处的值为value。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| index | int | 是 | 待设置元素的稀疏数组索引。如果小于0，抛出RangeError。|
| value | T | 是 | 要设置到该索引处的新值。|

**示例：**

```ts
const arr = new SparseArray<int>();
arr[0] = 42
console.info(arr[0]); // 42
arr[1] = 22
console.info(arr[1]) // 22
```

## constructor

constructor()

创建一个新的空SparseArray实例。

**示例：**

```ts
const arr = new SparseArray<string>();
console.info(arr.length); // 0
```

## constructor

constructor(length: int)

创建一个新的SparseArray实例，并指定数组的初始长度，但不会预分配内存。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| length | int | 是 | 稀疏数组的初始长度。|

**示例：**

```ts
const arr = new SparseArray<int>(5);
console.info(arr.length); // 5
```

## constructor

constructor(...value: T[])

创建一个新的SparseArray实例，并用指定的元素从索引0开始进行初始化。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| ...d | T[] | 是 | 稀疏数组元素。|

**示例：**

```ts
const arr = new SparseArray<string>("apple", "banana", "cherry");
console.info(arr.length); // 3
console.info(arr[0]); // "apple"
```

## $_iterator

iterator(): IterableIterator\<T>

返回一个遍历稀疏数组中所有值的迭代器。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| IterableIterator\<T> | 包含稀疏数组元素的迭代器。|

**示例：**

```ts
const arr = new SparseArray<string>("x", "y");
const iterator = arr.$_iterator();
let result = iterator.next();
while (!result.done) {
    console.info(result.value);
    result = iterator.next();
}
```

## push

push(val: T): int

将指定元素添加到稀疏数组的末尾，并返回稀疏数组的新长度。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| val | T | 是 | 要添加到稀疏数组末尾的元素。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| int | 稀疏数组的新长度。|

**示例：**

```ts
const arr = new SparseArray<int>();
arr.push(10);
console.info(arr.length); // 1
```

## push

push(...val: T[]): int

将多个元素添加到稀疏数组的末尾，并返回稀疏数组的新长度。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| ...val | T[] | 否 | 要添加到稀疏数组末尾的元素列表。默认值为[]。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| int | 稀疏数组的新长度。|

**示例：**

```ts
const arr = new SparseArray<int>();
arr.push(10, 20);
console.info(arr.length); // 2
```

## from

from\<T>(arr: ArrayLike\<T>): SparseArray\<T>

通过ArrayLike对象来创建一个新的稀疏数组实例。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--------- | :--------- | :--------- | :--------- |
| arr | ArrayLike\<T> | 是 | 要转换为稀疏数组的ArrayLike对象。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| SparseArray\<T> | 转换后的稀疏数组实例。|

**示例：**

```ts
const arr = SparseArray.from<int>([1, 2, 3]);
console.info(arr[0]); // 1
console.info(arr[1]); // 2
console.info(arr[2]); // 3
```

## from

from\<T>(iterable: ArrayLike\<T> | Iterable\<T>): SparseArray\<T> 

通过ArrayLike对象或可迭代对象来创建一个新的稀疏数组实例。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--------- | :--------- | :--------- | :--------- |
| iterable | ArrayLike\<T> \| Iterable\<T> | 是 | 要转换为稀疏数组的ArrayLike对象或可迭代对象。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| SparseArray\<T> | 转换后的稀疏数组实例。|

**示例：**

```ts
const arr = SparseArray.from<int>([1, 2, 3]);
console.info(arr[0]); // 1
console.info(arr[1]); // 2
console.info(arr[2]); // 3
```

## from

from\<T, U>(iterable: ArrayLike\<T> | Iterable\<T>, mapfn: (v: T, k: int) => U): SparseArray\<U>

通过ArrayLike对象或可迭代对象和映射函数来创建一个新的稀疏数组实例。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--------- | :--------- | :--------- | :--------- |
| iterable | ArrayLike\<T> \| Iterable\<T> | 是 | 要转换为稀疏数组的ArrayLike对象或可迭代对象。|
| mapfn | (v: T, k: int) => U | 是 | 用于映射每个元素的函数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| SparseArray\<U> | 转换后的稀疏数组实例。|

**示例：**

```ts
const arr = SparseArray.from<int, string>([1, 2, 3], (v) => v.toString());
console.info(arr[0]); // "1"
console.info(arr[1]); // "2"
console.info(arr[2]); // "3"
```

## forEach

forEach(callbackfn: (value: T, index: int, array: SparseArray\<T>) => void): void

遍历稀疏数组，并对稀疏数组中的每个非空洞位置的元素执行一次指定的操作。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| callbackfn | (value: T, index: int, array: SparseArray\<T>) => void | 是 | 对稀疏数组中每个元素执行的函数。|

**示例：**

```ts
const arr = new SparseArray<string>("a", "b");
arr.forEach((value, index) => {
    console.info(value);
});
```

## toString

toString(): string

返回一个表示稀疏数组及其元素的字符串。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| string | 表示稀疏数组的字符串。|

**示例：**

```ts
const arr = new SparseArray<int>(1);
arr.push(1,2,3)
console.info(arr.toString()); // ",1,2,3"(第一位元素是空洞)
```

## find

find(predicate: (value: T, index: int, array: SparseArray\<T>) => boolean): T | undefined

返回稀疏数组中满足提供的测试函数的第一个元素的值。否则返回undefined(代表寻找的元素不存在)。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| predicate | (value: T, index: int, array: SparseArray\<T>) => boolean | 是 | 用于测试稀疏数组中每个元素的函数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| T \| undefined | 满足测试函数的第一个元素的值，否则返回 undefined。|

**示例：**

```ts
const arr = new SparseArray<int>(5);
arr.push(1, 2, 3, 4);
const found = arr.find((v) => v > 2);
console.info(found); // 3
```

## splice

splice(start: int): SparseArray\<T>

通过原地删除从 start 索起到数组末尾的元素来更改稀疏数组的内容。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| start | int | 是 | 开始修改数组的索引。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| SparseArray\<T> | 包含被删除元素的稀疏数组。|

**示例：**

```ts
const arr = new SparseArray<int>(10, 20, 30, 40, 50);
const deleted = arr.splice(2);
console.info(arr.toString());  // "10,20"
console.info(deleted.toString());  // "30,40,50"
```


## splice

splice(start: int, deleteCount: int | undefined, ...items: T[]): SparseArray\<T>

通过删除或替换现有元素以及原地添加新元素来更改稀疏数组的内容，返回值为被删除的元素，如果被删除的部分含有空洞，也会存入新的数组中。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| start | int | 是 | 开始修改的索引。|
| deleteCount | int \| undefined | 否 | 要删除的元素数量。|
| ...items | T[] | 否 | 要添加到稀疏数组中的元素。默认值为[]。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| SparseArray\<T> | 包含被删除元素的稀疏数组。|

**示例：**

```ts
const arr = new SparseArray<int>(6);
arr[2] = 10
arr[4] = 20
let newArray = arr.splice(2, 2, 50);
console.info(newArray.toString()); // "10,undefined"
```

## findIndex

findIndex(predicate: (value: T, index: int, array: SparseArray\<T>) => boolean): int

返回稀疏数组中满足提供的测试函数的第一个元素的索引，否则返回 -1。在查找过程中会跳过空洞位置，只对实际存在的元素进行测试。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| predicate | (value: T, index: int, array: SparseArray\<T>) => boolean | 是 | 用于测试稀疏数组中每个元素的函数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| int | 满足测试函数的第一个元素的索引，否则返回 -1。|

**示例：**

```ts
const arr = new SparseArray<int>(6);
arr[0] = 10;
arr[2] = 30;
arr[4] = 50;
const index = arr.findIndex((v) => v > 20);
console.info(index); // 2
```

## findLast

findLast(predicate: (elem: T, index: int, array: SparseArray<T>) => boolean): T | undefined

按反向迭代数组，返回满足提供的测试函数的第一个元素的值。在查找过程中会跳过空洞位置，只对实际存在的元素进行测试。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| predicate | (elem: T, index: int, array: SparseArray\<T>) => boolean | 是 | 对数组中的每个值执行的函数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| T \| undefined | 如果找到元素则返回元素的值；否则返回 undefined。|

**示例：**

```ts
const arr = new SparseArray<int>(5);
arr[0] = 10;
arr[2] = 30;
arr[4] = 50;
const found = arr.findLast((v) => v > 20);
console.info(found); // 50
```

## findLastIndex

findLastIndex(predicate: (elem: T, index: int, array: SparseArray<T>) => boolean): int

按反向迭代数组，返回满足提供的测试函数的第一个元素的索引。在查找过程中会跳过空洞位置，只对实际存在的元素进行测试。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| predicate | (elem: T, index: int, array: SparseArray\<T>) => boolean | 是 | 对数组中的每个值执行的函数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| int | 如果找到元素则返回元素的索引；否则返回 -1。|

**示例：**

```ts
const arr = new SparseArray<int>();
arr[0] = 10;
arr[2] = 30;
arr[4] = 50;
const index = arr.findLastIndex((v) => v > 20);
console.info(index); // 4
```

## filter

filter(predicate: (value: T, index: int, array: SparseArray\<T>) => boolean): SparseArray\<T>

返回一个新的SparseArray实例，其中包含满足条件的所有元素。
 
**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| predicate | (value: T, index: int, array: SparseArray\<T>) => boolean | 是 | 用于测试稀疏数组中每个元素的函数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| SparseArray\<T> | 包含所有通过测试的元素的新SparseArray实例。|

**示例：**

```ts
const arr = new SparseArray<int>(1, 2, 3, 4);
const evens = arr.filter((v) => v % 2 == 0);
console.info(evens.length); // 2
```

## includes

includes(val: T, fromIndex?: int): boolean

判断稀疏数组是否包含某个指定的值，根据情况返回true或false。在查找过程中会跳过空洞位置，只对实际存在的元素进行比较。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| val | T | 是 | 需要查找的元素值。|
| fromIndex | int | 否 | 从该索引处开始查找val，默认值为0。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| boolean | 如果稀疏数组中包含指定的值则返回true，否则返回false。|

**示例：**

```ts
const arr = new SparseArray<int>();
arr[0] = 10;
arr[2] = 30;
arr[4] = 50;
console.info(arr.includes(30)); // true
console.info(arr.includes(20)); // false
```

## indexOf

indexOf(val: T, fromIndex: int = 0): int

返回稀疏数组中可以找到一个给定元素的第一个索引，如果不存在，则返回-1。在查找过程中会跳过空洞位置，只对实际存在的元素进行比较。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| val | T | 是 | 需要查找的元素值。|
| fromIndex | int | 否 | 从该索引处开始查找val，默认值为0。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| int | 给定元素的第一个索引，如果不存在则返回-1。|

**示例：**

```ts
const arr = new SparseArray<int>();
arr[0] = 10;
arr[2] = 20;
arr[4] = 20;
console.info(arr.indexOf(20)); // 2
console.info(arr.indexOf(30)); // -1
```

## isArray

static isArray(value: Any): boolean

判断指定的值是否为稀疏数组。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | Any | 是 | 需要判断的值。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| boolean | 如果是稀疏数组则返回 true，否则返回 false。|

**示例：**

```ts
const arr = new SparseArray<int>();
console.info(SparseArray.isArray(arr)); // true
```

## join

join(sep?: string): string

将稀疏数组的所有非undefined元素按照给定连接符sep连接成一个字符串并返回这个字符串。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| sep | string | 否 | 指定一个字符串来分隔稀疏数组的每个元素。如果省略，默认值为逗号（,）。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| string | 所有稀疏数组元素连接而成的字符串。|

**示例：**

```ts
const arr = new SparseArray<string>(2)
arr.push("a", "b", "c");
console.info(arr.join("-")); // "--a-b-c"
```

## slice

slice(start: int = 0, end: int = this.maxLength): SparseArray\<T>

返回一个新的稀疏数组对象，这一对象是一个由start和end决定的原稀疏数组的浅拷贝。原始稀疏数组不会被改变。如果start大于end的值，则会返回空数组。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| start | int | 否 | 提取起始处的索引。默认值为0。|
| end | int | 否 | 提取终止处的索引。默认值为稀疏数组长度。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| SparseArray\<T> | 一个含有被提取元素的新稀疏数组。|

**示例：**

```ts
const arr = new SparseArray<int>(1, 2, 3, 4);
const sliced = arr.slice(1, 3);
console.info(sliced.toString()); // "2,3"
const empty = arr.slice(3, 1);
console.info(empty.toString()); // "" (返回空数组)
```

## sort

sort(compareFn?: (a: T, b: T) => int): this

使用指定的compareFn函数对稀疏数组的元素进行排序，并返回稀疏数组本身，而不是返回一个新数组。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| compareFn | (a: T, b: T) => int | 否 | 用来指定按某种顺序进行排列的函数。如果省略，元素按照转换为的字符串的各个字符的Unicode码进行排序。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| this | 经过排序的稀疏数组实例本身。|

**示例：**

```ts
const arr = new SparseArray<int>(3, 1, 4, 1, 5);
arr.sort((a, b) => a - b);
console.info(arr[0]); // 1
```

## copyWithin

copyWithin(target: int, start: int = 0, end: int = this.maxLength): this

复制数组的一部分到同一数组中的另一个位置，并返回稀疏数组本身，并且不会改变原数组的长度。如果start大于end的值，则直接返回原数组。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| target | int | 是 | 指定要复制到的索引。|
| start | int | 否 | 指定要复制的的起始处索引。默认值为0。|
| end | int | 否 | 指定要复制的的终止处索引。默认值为稀疏数组长度。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| this | 复制后的稀疏数组实例本身。|

**示例：**

```ts
const arr = new SparseArray<int>(1, 2, 3, 4, 5);
arr.copyWithin(0, 3, 4);
console.info(arr.toString()); // "4,2,3,4,5"
```

## concat

concat(...items: FixedArray\<ConcatArray\<T>>): SparseArray\<T>

将当前稀疏数组和提供的其他数组连接起来，创建一个新的SparseArray实例并返回。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| ...items | FixedArray\<ConcatArray\<T>> | 否 | 要连接到原稀疏数组末尾的数组或元素列表。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| SparseArray\<T> | 包含当前稀疏数组和连接元素的新SparseArray实例。|

**示例：**

```ts
const arr1 = new SparseArray<int>(1, 2);
const arr2 = new Array<int>(3, 4); 
const newArr: SparseArray<int> = arr1.concat(arr2); 
console.info(newArr.toString()); // "1,2,3,4"
```

## flat

flat\<U = T>(): SparseArray\<U>

创建一个新的SparseArray实例，并将所有子稀疏数组元素连接到其中，默认深度为1。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| SparseArray\<U> | 扁平化后的新SparseArray实例。|

**示例：**

```ts
let inner = new SparseArray<int>(44, 55, 66)
let x = new SparseArray<int | SparseArray<int>>(1)
x.push(1, 3, 5)
x.push(inner)
let res = x.flat()
console.info(res.toString()); // "1,3,5,44,55,66"
```

## flat

flat\<U>(depth: int): SparseArray\<U>

创建一个新的SparseArray实例，并将所有子稀疏数组元素递归地连接到其中，直到指定的深度。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| depth | int | 否 | 指定要提取嵌套数组的结构深度。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| SparseArray\<U> | 扁平化后的新SparseArray实例。|

**示例：**

```ts
let inner = new SparseArray<int>(44, 55, 66)
let x = new SparseArray<int | SparseArray<int>>(1)
x.push(1, 3, 5)
x.push(inner)
let res = x.flat(2)
console.info(res.toString()); // "1,3,5,44,55,66"
```

## flatMap

flatMap\<U>(fn: (v: T, k: int, arr: SparseArray\<T>) => U): SparseArray\<U>

先对稀疏数组中的每个非undefined元素应用一个映射函数，然后将结果扁平化一层。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| fn | (v: T, k: int, arr: SparseArray\<T>) => U | 是 | 应用于每个元素的函数，返回一个新元素。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| SparseArray\<U> | 经过映射和扁平化后的新SparseArray实例。|

**示例：**

```ts
let inner = new SparseArray<int>(44, 55, 66)
let x = new SparseArray<int | SparseArray<int>>(1)
x.push(1, 3, 5)
x.push(inner)
let res = x.flatMap((v) => v)
console.info(res.toString()); // "1,3,5,44,55,66"
```

## some

some(predicate: (value: T, index: int, array: SparseArray\<T>) => boolean): boolean

测试稀疏数组中是不是至少有1个元素通过了被提供的函数测试。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| predicate | (value: T, index: int, array: SparseArray\<T>) => boolean | 是 | 用来测试每个元素的函数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| boolean | 如果回调函数对任何稀疏数组元素进行执行返回了true，则some函数返回 true，否则为 false。|

**示例：**

```ts
const arr = new SparseArray<int>(1, 2, 3);
console.info(arr.some((v) => v > 2)); // true
```

## map

map\<U>(callbackfn: (value: T, index: int, array: SparseArray\<T>) => U): SparseArray\<U>

创建一个新稀疏数组，其结果是该稀疏数组中的每个元素是调用一次提供的函数后的返回值。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| callbackfn | (value: T, index: int, array: SparseArray\<T>) => U | 是 | 为数据中每个元素执行的函数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| SparseArray\<U> | 包含回调函数结果的新SparseArray实例。|

**示例：**

```ts
const arr = new SparseArray<int>(1, 2);
const doubled = arr.map((v) => v * 2);
console.info(doubled.toString()); // "2,4"
```

## values

values(): IterableIterator\<T>

返回一个包含稀疏数组中每个索引的值的迭代器对象。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| IterableIterator\<T> | 包含稀疏数组中所有值的迭代器。|

**示例：**

```ts
const arr = new SparseArray<string>("x", "y");
const iterator = arr.values();
console.info(iterator.next().value); // "x"
```

## pop

pop(): T | undefined

从稀疏数组中删除最后一个元素，并返回该元素的值。此方法会更改稀疏数组的长度。如果最后一个元素的值为开发者设置的undefined，返回undefined，若数组最后一个数组为空洞，则也返回undefined（代表不存在）。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| T \| undefined | 从稀疏数组中删除的元素；如果稀疏数组为空则返回undefined。|

**示例：**

```ts
const arr = new SparseArray<int | undefined>(1, 2, undefined);
arr.length = 4
const last = arr.pop();
console.info(last); // undefined(空洞值)
const newlast = arr.pop()
console.info(newlast); // undefined
```

## shift

shift(): T | undefined

从稀疏数组中删除第一个元素，并返回该元素的值。此方法会更改稀疏数组的长度。如果第一个元素的值为开发者设置的undefined，返回undefined，若数组第一个数组为空洞，则也返回undefined（代表不存在）。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| T \| undefined | 从稀疏数组中删除的元素；如果稀疏数组为空则返回undefined。|

**示例：**

```ts
const arr = new SparseArray<int | undefined>(1)
arr.push(undefined, 2, 3);
const first = arr.shift();
console.info(first); // undefined(空洞值)
const newfirst = arr.shift();
console.info(arr.length); // 2
```

## keys

keys(): IterableIterator\<int>

返回一个包含稀疏数组中每个索引键的迭代器。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| IterableIterator\<int> | 包含稀疏数组索引键的迭代器。|

**示例：**

```ts
const arr = new SparseArray<string>("a", "b");
const iterator = arr.keys();
console.info(iterator.next().value); // 0
```

## fill

fill(value: T, start: int = 0, end: int = this.maxLength): this

用一个固定值填充一个稀疏数组中从起始索引到终止索引内的全部元素。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | T | 是 | 用来填充稀疏数组元素的值。|
| start | int | 否 | 起始索引，默认值为0。|
| end | int | 否 | 终止索引，默认值为稀疏数组的最大长度值。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| this | 修改后的稀疏数组。|

**示例：**

```ts
const arr = new SparseArray<int>(1, 2, 3);
arr.fill(4);
console.info(arr.toString()); // "4,4,4"
```

## unshift

unshift(...values: T[]): int

在数组头部添加指定元素，并返回该稀疏数组的新长度。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| ...values | T[] | 否 | 要添加到稀疏数组开头的元素。默认值为[]。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| int | 稀疏数组的新长度。|

**示例：**

```ts
const arr = new SparseArray<int>(3, 4);
arr.unshift(1, 2);
console.info(arr.toString()); // "1,2,3,4"
```

## reverse

reverse(): this

将稀疏数组中元素的位置颠倒，并返回该稀疏数组。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| this | 颠倒后的稀疏数组实例本身。|

**示例：**

```ts
const arr = new SparseArray<int>(1, 2, 3);
arr.reverse();
console.info(arr.toString()); // "3,2,1"
```

## entries

entries(): IterableIterator\<[int, T]>

返回一个新的迭代器对象，该对象包含稀疏数组中每个索引的键/值对。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| IterableIterator\<[int, T]> | 包含键值对的迭代器。|

**示例：**

```ts
const arr = new SparseArray<string>("a", "b");
const iterator = arr.entries();
console.info(iterator.next().value); // "0,a"
```

## lastIndexof

lastIndexOf(searchElement: T): int

返回指定元素在稀疏数组中的最后一个的索引，如果不存在则返回-1。从数组的后面向前查找。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| searchElement | T | 是 | 被查找的元素。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| int | 稀疏数组中该元素的最后一次出现的索引，如未找到返回-1。|

**示例：**

```ts
const arr = new SparseArray<int>(1, 2, 3, 2, 4);
const index = arr.lastIndexOf(2);
console.info(index); // 3
```

## lastIndexOf

lastIndexOf(searchElement: T, fromIndex: int = 0): int

返回指定元素在稀疏数组中的最后一个的索引，如果不存在则返回-1。从数组的后面向前查找。fromIndex为开始查找的位置，若fromIndex为0则只会比较第一个元素，如果元素大于数组长度，则从数组的最后一个元素开始查找。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| searchElement | T | 是 | 被查找的元素。|
| fromIndex | int | 否 | 从此位置开始逆向查找。默认值为数组长度减1。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| int | 稀疏数组中该元素的最后一次出现的索引，如未找到返回-1。|

**示例：**

```ts
const arr = new SparseArray<int>(2, 5, 9, 2);
console.info(arr.lastIndexOf(2)); // 3
```

## reduce

reduce(callbackfn: (previousValue: T, currentValue: T, index: int, array: SparseArray\<T>) => T): T

对稀疏数组中的每个元素执行一个由您提供的reducer函数（升序执行），将其结果汇总为单个返回值。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| callbackfn | (previousValue: T, currentValue: T, index: int, array: SparseArray\<T>) => T | 是 | 执行稀疏数组中每个值的函数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| T \| int | 函数累计处理的结果。|

**示例：**

```ts
const arr = new SparseArray<int>(1, 2, 3, 4);
const sum = arr.reduce((acc, curr) => acc + curr);
console.info(sum); // 10
```

## reduceRight

reduceRight(callbackfn: (previousValue: T, currentValue: T, index: int, array: SparseArray<T>) => T): T

按降序对稀疏数组中的所有元素调用指定的回调函数。回调函数的返回值是累加结果，并在下一次调用回调函数时作为参数提供。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| callbackfn | (previousValue: T, currentValue: T, index: int, array: SparseArray\<T>) => T | 是 | reduceRight方法对数组中的每个元素调用一次callbackfn函数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| T | 累加结果。|

**示例：**

```ts
const arr = new SparseArray<int>(1, 2, 3, 4);
const sum = arr.reduceRight((acc, curr) => acc + curr);
console.info(sum); // 10
```



## every

every(predicate: (value: T, index: int, array: SparseArray\<T>) => boolean): boolean

测试一个稀疏数组内的所有元素是否都能通过某个指定函数的测试。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| predicate | (value: T, index: int, array: SparseArray\<T>) => boolean | 是 | 用来测试每个元素的函数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| boolean | 如果回调函数对每个元素都返回truthy值，则返回true；否则返回false。|

**示例：**

```ts
const arr = new SparseArray<int>(1, 2, 3);
console.info(arr.every((v) => v > 0)); // true
```

## of

static of\<T>(...values: T[]): SparseArray\<T>

创建一个具有可变数量参数的新SparseArray实例。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| ...values | T[] | 否 | 任意个参数，将按顺序成为稀疏数组中的元素。默认值为[]。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| SparseArray\<T> | 新创建的SparseArray实例。|

**示例：**

```ts
const arr = SparseArray.of<string>("a", "b", "c");
console.info(arr.length); // 3
```

## at

at(index: int): T | undefined

接收一个整数值并返回该索引对应的元素。若输入index值大于数组的最大长度或者该位置为空洞则会返回undefined（代表不存在），若index位置是开发者设置的undefined，则会返回当前值。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| index | int | 是 | 匹配给定索引的元素。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| T \| undefined | 匹配给定索引的元素，找不到则返回 undefined。|

**示例：**

```ts
const arr = new SparseArray<int>(1)
arr.push(10, 20, 30);
console.info(arr.at(-1)); // 30
console.info(arr.at(0)); // undefined(空洞值)
```

## toReversed

toReversed(): SparseArray\<T>

返回一个新的稀疏数组，其中元素的顺序与原数组相反。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| SparseArray\<T> | 元素顺序反转的新稀疏数组。|

**示例：**

```ts
const arr = new SparseArray<int>(2)
arr.push(1, 3, 4);
const reversed = arr.toReversed();
console.info(reversed.toString()); // "4,3,1,,"
```

## toSorted

toSorted(): SparseArray\<T>

返回一个新的稀疏数组，其中的元素按升序排列。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| SparseArray\<T> | 新的排序后的稀疏数组。|

**示例：**

```ts
const arr = new SparseArray<int>(2)
arr.push(3, 1, 4, 1, 5);
arr.length = 8
const sorted = arr.toSorted();
console.info(sorted.toString()); // ",,1,1,3,4,5,"
```

## toSorted

toSorted(comparator: (a: T, b: T) => int): SparseArray\<T>

使用提供的比较器函数返回一个新的稀疏数组，其中的元素按指定顺序排列。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| comparator | (a: T, b: T) => int | 是 | 定义排序顺序的函数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| SparseArray\<T> | 新的排序后的稀疏数组。|

**示例：**

```ts
const arr = new SparseArray<int>(3, 1, 4, 1, 5);
const sorted = arr.toSorted((a, b) => b - a);
console.info(sorted.toString()); // "5,4,3,1,1"
```

## toSpliced

toSpliced(start: int, delete: int, ...items: FixedArray\<T>): SparseArray\<T>

返回一个新的稀疏数组，在给定索引处删除或替换某些元素。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| start | int | 是 | 开始更改数组的从零开始的索引。如果为负数，则从数组末尾开始计算。如果超过数组长度，则从数组末尾开始处理。|
| delete | int | 是 | 要删除的元素数量。如果小于0，则不删除任何元素；如果超过数组长度或导致删除范围超出数组边界，则自动调整为有效值。|
| ...items | FixedArray\<T> | 否 | 要添加到数组中的元素。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| SparseArray\<T> | 应用更改后的新数组。|

**示例：**

```ts
const arr = new SparseArray<int>(1, 2, 3, 4, 5);
const spliced = arr.toSpliced(1, 2, 20, 30);
console.info(spliced.toString()); // "1,20,30,4,5"

// delete为负数时不删除元素
const noDelete = arr.toSpliced(1, -1, 20);
console.info(noDelete.toString()); // "1,20,2,3,4,5"

// delete超出范围时自动调整
const adjustDelete = arr.toSpliced(3, 10, 20);
console.info(adjustDelete.toString()); // "1,2,3,20"

// start为负数时从末尾计算
const negativeStart = arr.toSpliced(-2, 1, 20);
console.info(negativeStart.toString()); // "1,2,3,20,5"

// start超出数组长度时
const outOfRange = arr.toSpliced(10, 1, 20);
console.info(outOfRange.toString()); // "1,2,3,4,5,20"
```