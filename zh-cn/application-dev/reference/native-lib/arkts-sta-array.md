# Array
Array模块提供数组操作的基本方法。开发者可以使用本模块的功能，如创建数组、访问数组元素等。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## length

override get length(): int

获取数组的当前长度（即数组中实际包含的元素个数）。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| int | 数组的当前实际长度，对应于内部的this.actualLength。|

**示例：**

```ts
const arr = new Array<number>(10); // 初始长度为 10
console.info(arr.length); // 10
```

## length

set length(newLen: int)

设置数组的新长度。

> **说明：**
>
> 在当前实现中，仅支持缩短数组长度。如果尝试将长度设置为当前实际长度（this.actualLength）或负数，将抛出RangeError。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| newLen | int | 是 | 数组的目标新长度。新长度必须小于或等于当前长度，且必须大于或等于零。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3); // 初始长度 3
arr.length = 1; 
console.info(arr.length); // 1
```

## $_get

native $_get(idx: int): T

获取索引idx处的值。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| idx | int | 是 | 待获取元素的数组索引。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| T | 数组中指定索引处的元素值。|

**示例：**

```ts
const arr = new Array<string>(3);
arr[0] = "A";
const val = arr[0];
console.info(val); // "A"
```

## $_set
native $_set(idx: int, val: T): void

设置索引idx处的值为val。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| idx | int | 是 | 待设置元素的数组索引。|
| val | T | 是 | 要设置到该索引处的新值。|

**示例：**
```ts
const arr = new Array<number>(2);
arr[0] = 42;
console.info(arr[0]); // 42
```

## constructor

constructor(arrayLen: int)

创建一个新的Array\<T>实例，并指定数组的初始长度。
> 此接口使用后如未及时初始化，可能在后续使用中抛异常。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| arrayLen | int | 是 | 数组的初始长度。|

**示例：**

```ts
const arr = new Array<number>(5);
console.info(arr.length); // 5
```

## constructor

constructor()

创建一个新的Array\<T>实例，初始长度为0。

**示例：**

```ts
const arr = new Array<string>();
console.info(arr.length); // 0
```

## constructor

constructor(first: T, ...d: T[])

创建一个新的Array\<T>实例，并用指定的元素进行初始化。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| first | T | 是 | 数组的第一个元素。|
| ...d | T[] | 否 | 数组的剩余元素。默认值为[]。|

**示例：**

```ts
const arr = new Array<string>("apple", "banana", "cherry");
console.info(arr.length); // 3
console.info(arr[0]); // "apple"
```

## constructor

constructor(arrayLen: int, initializer: (index: int) => T)

null safe接口，创建一个新的Array\<T>实例，并用指定的构造器进行初始化。

> **说明：**
>
> null safe: 提供空安全机制，保证使用前初始化，避免出现空指针异常。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| arrayLen | int | 是 | 数组的初始长度。|
| initializer | (index: int) => T | 是 | 自定义构造器函数，数组索引为输入，自定义每个元素的初始值。|

**示例：**

```ts
const arr = new Array<int>(3, (index) => { return index + 1 });
console.info(arr[0]); // 1
console.info(arr[1]); // 2
console.info(arr[2]); // 3
```

## create

static create\<T>(arrayLength: number, initialValue: T): Array\<T>

创建一个指定长度的Array\<T>实例，并用一个初始值填充所有元素。

> **说明：**
>
> null safe: 提供空安全机制，保证使用前初始化，避免出现空指针异常，针对无法直接初始化的类型， 设置类型为T \| undefined， 并设置初始值undefined。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| arrayLength | number | 是 | 数组的长度。|
| initialValue | T | 是 | 数组元素的初始值。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T> | 新创建的Array实例对象。|

**示例：**

```ts
class ElementTest {
    ele: int;
    constructor(e: int) {
        this.ele = e;
    }
}

const arr = Array.create<string>(3, "default");
console.info(arr.length); // 3
console.info(arr[1]); // "default"
const arrU: Array<ElementTest | undefined> = Array.create<ElementTest | undefined>(3, undefined);
console.info(arrU[0]); // undefined
console.info(arrU[1]); // undefined
console.info(arrU[2]); // undefined
```

## extendTo

extendTo(arrayLength: number, initialValue: T): void

将数组扩展到指定的长度。如果新长度大于当前长度，新添加的元素将用`initialValue`填充。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| arrayLength | number | 是 | 数组的新长度。|
| initialValue | T | 是 | 扩展部分元素的初始值。|

**示例：**

```ts
const arr = new Array<number>(1, 2);
arr.extendTo(5, 0);
console.info(arr.length); // 5
console.info(arr[3]); // 0
```

## shrinkTo

shrinkTo(arrayLength: number): void

将数组减至指定的长度。若指定长度小于当前长度，超出的元素将被舍弃。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| arrayLength | number | 是 | 数组的新长度。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3, 4, 5);
arr.shrinkTo(2);
console.info(arr.length); // 2
```

## $\_invoke

static $_invoke\<T>(): Array\<T>

创建并返回一个长度为0的新Array\<T>实例。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T> | 新创建的Array实例对象。|

**示例：**

```ts
const arr = new Array<string>();
console.info(arr.length); // 0
```

## $\_invoke

static $_invoke\<T>(arrayLength?: number): Array\<T>

创建并返回一个指定长度的新Array\<T>实例。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| arrayLength | number | 否 | 数组的长度。默认值为0。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T\> | 新创建的Array实例对象。|

**示例：**

```ts
const arr = new Array<number>(10);
console.info(arr.length); // 10
```

## $\_invoke

static $_invoke\<T>(...items: T[]): Array\<T>

创建并返回一个由指定元素初始化的新Array\<T\>实例。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| ...items | T[] | 否 | 数组的初始化元素列表。默认值为[]。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T> | 新创建的Array实例对象。|

**示例：**

```ts
const arr = new Array<string>("x", "y", "z");
console.info(arr[1]); // "y"
```

## from

static from\<T>(iterable: ArrayLike\<T> | Iterable\<T>): Array\<T>

从一个可迭代对象或类数组对象中创建并返回一个新的Array\<T>实例。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| iterable | ArrayLike\<T> \| Iterable\<T> | 是 | 要转换为数组的可迭代对象或类数组对象。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T> | 由可迭代对象中的元素构造的新Array实例。|

**示例：**

```ts
const source = new Array<number>(10, 20, 30);
const arr: Array<number> = Array.from<number>(source);

console.info(arr.length); // 3
console.info(arr[1]); // 20
```

## from

static from\<T>(arr: ArrayLike\<T>): Array\<T>

从一个类数组对象中创建并返回一个新的Array\<T>实例。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| arr | ArrayLike\<T> | 是 | 要转换为数组的类数组对象。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T> | 由类数组对象中的元素构造的新Array实例。|

**示例：**

```ts
const sourceArr = new Array<string>("foo", "bar", "baz");
const arr: Array<string> = Array.from(sourceArr); 

console.info(arr.length); // 3
console.info(arr[1]); // "bar"
```

## from

static from\<T, U>(iterable: ArrayLike\<T> | Iterable\<T>, mapfn: (v: T, k: number) => U): Array\<U>

从一个可迭代对象创建新的Array\<U>实例，并在转换过程中对每个元素应用一个映射函数。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| iterable | ArrayLike\<T> \| Iterable\<T> | 是 | 要转换为数组的可迭代对象或类数组对象。|
| mapfn | (v: T, k: number) => U | 是 | 应用于每个元素的映射函数，返回映射后的新值。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<U> | 构造自可迭代对象和映射函数的新Array实例。|

**示例：**

```ts
const source = new Array<number>(1, 2, 3);
const doubles: Array<number> = Array.from<number, number>(
    source, 
    (v: number, k: number): number => v * 2 
);

console.info(doubles.length); // 3
console.info(doubles[0]); // 2
```

## from

static from\<T, U>(values: FixedArray\<T>, mapfn: (v: T, k: number) => U): Array\<U>

从一个原生数组（`FixedArray<T>`）创建新的Array\<U>实例，并在转换过程中对每个元素应用一个映射函数。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| values | FixedArray\<T> | 是 | 要转换为Array的原生数组。|
| mapfn | (v: T, k: number) => U | 是 | 应用于每个元素的映射函数，返回映射后的新值。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<U> | 构造自原生数组和映射函数的新Array实例。|

**示例：**

```ts
const sourceArray = new int[2];
const mappedArr: Array<int> = Array.from<int, int>(
    sourceArray, 
    (v: int, i: number): int => {
        return v + i.toInt(); 
    }
);

console.info(mappedArr[0]); // 0
console.info(mappedArr[1]); // 1
```

## from

static from\<T>(arr: FixedArray\<T>): Array\<T>

从一个原生数组（`FixedArray<T>`）创建并返回一个新的Array\<T>实例。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| arr | FixedArray\<T> | 是 | 要转换为Array的原生数组。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T> | 构造自原生数组的新Array实例。|

**示例：**

```ts
const sourceArr = new int[2];
const newArr: Array<int> = Array.from<int>(sourceArr);

console.info(newArr.length); // 2
console.info(newArr[1]); // 0
```

## sort

sort(comparator?: (a: T, b: T) => number): this 

使用comparator实现的比较算法对数组的元素进行排序，并返回对数组的引用。如果没有提供比较函数，则使用默认的比较规则。

> **说明：**
>
> 这是一个修改原数组的方法。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| comparator | (a: T, b: T) => number | 否 | 用于定义排序顺序的函数。默认值：元素的默认比较规则（通常按字符串或数值）。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| this | 经过排序的数组实例本身。|

**示例：**

```ts
const arr = new Array<number>(3, 1, 4, 1, 5);
arr.sort((a, b) => a - b);
console.info(arr[0]); // 1
```

## shift

shift(): T | undefined

移除并返回数组的第一个元素。此方法会改变数组的长度。

> **说明：**
>
> 这是一个修改原数组的方法。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| T \| undefined | 移除的元素；如果数组为空，则返回 `undefined`。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3);
const first = arr.shift();
console.info(first); // 1
console.info(arr.length); // 2
```

## pop

pop(): T | undefined

移除并返回数组的最后一个元素。此方法会改变数组的长度。

> **说明：**
>
> 这是一个修改原数组的方法。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| T \| undefined | 移除的元素；如果数组为空，则返回 `undefined`。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3);
const last = arr.pop();
console.info(last); // 3
console.info(arr.length); // 2
```

## push

push()

所有以`push`开头的方法都是push的别名，都将一个或多个元素添加到数组的末尾，并返回数组的新长度。推荐直接调用push方法。

**示例·：**
```ts
const arr = new Array<number>(0);
arr.push(10); // 调用 pushOne
console.info(arr.length); // 1
```

## pushArray

pushArray(...val: T[]): int

push的别名重载。将一个或多个元素（作为参数数组 ...val）按顺序添加到数组的末尾，并返回数组的新长度。

> **说明：**
>
> 这是一个修改原数组的方法。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| ...val | T[] | 否 | 使用扩展运算符(...)传入的一个或多个元素，它们将被添加到数组末尾。默认值为[]。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| int | 数组的新长度。|

**示例：**

```ts
const arr = new Array<string>(0);
arr.pushArray("A", "B"); 
console.info(arr.pushArray("C", "D", "E")); // 5
```

## pushOne

pushOne(val: T): int

push的别名重载。将指定的单个元素添加到数组的末尾，并返回数组的新长度。

> **说明：**
>
> 这是一个修改原数组的方法。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| val | T | 否 | 要添加到数组末尾的元素。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| int | 数组的新长度。|

**示例：**

```ts
const arr = new Array<number>(0);
arr.pushOne(10); 
arr.pushOne(20); 
console.info(arr.pushOne(30)); // 3
```

## splice

splice(start: int, delete: int, ...items: T[]): Array\<T>

通过删除或替换现有元素以及原地添加新元素来更改数组的内容。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| start | int | 是 | 开始修改的索引。|
| delete | int | 是 | 要删除的元素数量。|
| ...items | T[] | 否 | 要添加到数组中的元素。默认值为[]。|


**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T> | 包含被删除元素的数组。|

**示例：**

```ts
const arr = new Array<number>(10, 20, 30);
arr.splice(1, 1, 50);
console.info(arr); // [10, 50, 30]
```

## splice

splice(start: int): Array\<T>

从指定的`start`索引开始删除直到数组末尾的所有元素。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| start | int | 是 | 开始删除的索引。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T\> | 包含被删除元素的数组。|

**示例：**

```ts
const arr = new Array<string>("a", "b", "c");
arr.splice(1);
console.info(arr); // ["a"]
```

## isArray

static isArray(o: Any): boolean

检查传入的值是否是一个非空数组（`Array`实例或原生数组类型）。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| o | any | 是 | 需要检测的值。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| boolean | 如果`o`是一个非空数组，则返回`true`，否则返回`false`。|

**示例：**

```ts
const arr = new Array<number>();
console.info(Array.isArray(arr)); // true
console.info(Array.isArray(123)); // false
```

## of

static of\<T>(...values: T[]): Array\<T>

创建一个新的Array\<T>实例，元素由提供的参数构成。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| ...values | T[] | 否 | 任意数量的参数，按顺序成为新数组的元素。默认值为[]。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T\> | 新创建的Array实例。|

**示例：**

```ts
const arr = Array.of<string>("a", "b", "c");
console.info(arr.length); // 3
```

## unshift

unshift(...values: T[]): number

将一个或多个元素添加到数组的开头，并返回数组的新长度。

> **说明：**
>
> 这是一个修改原数组的方法。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| ...values | T[] | 否 | 要添加到数组开头的元素。默认值为[]。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| number | 数组的新长度。|

**示例：**

```ts
const arr = new Array<number>(3, 4);
const newLen = arr.unshift(1, 2);
console.info(newLen); // 4
console.info(arr[0]); // 1
```

## keys

keys(): IterableIterator\<number>

返回一个遍历数组中所有索引的迭代器。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| IterableIterator\<Number> | 包含数组索引的迭代器。|

**示例：**

```ts
const arr = new Array<string>("a", "b");
const iterator = arr.keys();
console.info(iterator.next().value); // 0
console.info(iterator.next().value); // 1
```

## $\_iterator

$_iterator(): IterableIterator\<T>

返回一个遍历数组中所有值的迭代器（与`values()`相同）。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| IterableIterator\<T> | 包含数组元素的迭代器。|

**示例：**

```ts
const arr = new Array<string>("x", "y");
const iterator = arr.$_iterator();
console.info(iterator.next().value); // "x"
```

## filter

filter(predicate: (value: T, index: int, array: Array\<T>) => boolean): Array\<T>

返回一个新的Array\<T>实例，其中包含满足条件的所有元素。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| predicate | (value: T, index: int, array: Array\<T>) => boolean | 是 | 用于测试数组中每个元素的函数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T> | 包含所有通过测试的元素的新Array实例。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3, 4);
const evens = arr.filter((v) => v % 2 == 0);
console.info(evens.length); // 2
```

## flat

flat\<U>(depth: number): Array\<U>

在处理多层嵌套的数据结构时，创建一个新的Array\<U>实例，并将所有子数组元素递归地连接到其中，直到指定的深度。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| depth | number | 否 | 指定要提取嵌套数组的结构深度。默认值为1。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<U> | 扁平化后的新Array实例。|

**示例：**

```ts
const nested = new Array<Any>(1, new Array<Any>(2, new Array<Any>(3)));
const flatArr = nested.flat(2);
console.info(flatArr.length); // 3
```

## flat

flat\<U>(depth: int): Array\<U>

创建一个新的Array\<U>实例，并将所有子数组元素递归地连接到其中，直到指定的深度。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| depth | int | 否 | 指定要提取嵌套数组的结构深度。默认值为1。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<U> | 扁平化后的新Array实例。|

**示例：**

```ts
const nested = new Array<Any>(1, new Array<Any>(2, 3));
const flatArr = nested.flat(1);
console.info(flatArr.length); // 3
console.info(flatArr); // [1, 2, 3]
```

## concat

concat(...items: FixedArray\<ConcatArray\<T>>): Array\<T>

将当前数组实例和提供的其他数组实例连接起来，创建一个新的Array\<T>实例并返回。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| ...items | FixedArray\<ConcatArray\<T>> | 否 | 要连接到原数组末尾的数组或元素列表。传入的是数组内元素会被展平并追加到新数组中。默认值为[]。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T> | 由当前数组和所有`items`构造的新Array实例。|

**示例：**

```ts
const arr1 = new Array<number>(1, 2);
const arr2 = new Array<number>(3, 4); 
const newArr: Array<number> = arr1.concat(arr2); 
console.info(newArr); // [1, 2, 3, 4]
```

## flat

flat\<U\>(): Array\<U\>

创建一个新的Array\<U>实例，并将所有子数组元素连接到其中，默认深度为1。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<U> | 扁平化后的新Array实例。|

**示例：**

```ts
const nested = new Array<Any>(1, new Array<Any>(2, new Array<Any>(3)));
const flatArr = nested.flat(); 
console.info(flatArr.length); // 3
```

## flatMap

flatMap\<U>(fn: (v: T, k: int, arr: Array\<T>) => U): Array\<U>

先对数组中的每个元素应用一个映射函数，然后将结果扁平化一层。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| fn | (v: T, k: int, arr: Array\<T>) => U | 是 | 应用于每个元素的函数，返回一个新元素。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<U> | 经过映射和扁平化后的新Array实例。|

**示例：**

```ts
const arr = new Array<number>(1, 2);
const doubled: Array<number> = arr.flatMap(
    (v: number, k: int, array: Array<number>): Array<number> => {
        return new Array<number>(v, v * 2);
    }
);
console.info(doubled); // [1, 2, 2, 4]
```

## at

at(index: number): T

接收一个整数值，返回该索引处的元素，允许使用正数和负数索引。负数索引从数组末尾开始倒数。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| index | number | 是 | 要返回的数组元素的索引，从零开始计数，负数表示从末尾开始计数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| T | 匹配给定索引的元素。|

**示例：**

```ts
const arr = new Array<number>(10, 20, 30);
console.info(arr.at(-1)); // 30
```

## at

at(index: int): T

接收一个整数值，返回该索引处的元素，允许使用正数和负数索引。负数索引从数组末尾开始倒数。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| index | int | 是 | 要返回的数组元素的索引，从零开始计数，负数表示从末尾开始计数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| T | 匹配给定索引的元素。|

**示例：**

```ts
const arr = new Array<number>(10, 20, 30);
console.info(arr.at(-2)); // 20
```

## copyWithin

copyWithin(target: number, start: number, end?: Number): this

将数组的一部分浅拷贝到数组中的另一个位置，并返回它，不修改其长度。

> **说明：**
>
> 这是一个修改原数组的方法。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| target | number | 是 | 复制到的索引位置。|
| start | Number | 否 | 开始复制元素的源索引。默认值为0。|
| end? | Number | 否 | 结束复制元素的源索引。默认值为数组长度。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| this | 转换后的数组实例本身。|

**示例：**

```ts
const arr = new Array<string>("a", "b", "c", "d", "e");
arr.copyWithin(0, 3, 4); 
console.info(arr); // ["d", "b", "c", "d", "e"]
```

## copyWithin

copyWithin(target: int, start: int, end: int): this

将数组的一部分浅拷贝到数组中的另一个位置，并返回它，不修改其长度。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| target | int | 是 | 复制到的索引位置。|
| start | int | 是 | 开始复制元素的源索引。|
| end | int | 是 | 结束复制元素的源索引（不包含）。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| this | 转换后的数组实例本身。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3, 4, 5);
arr.copyWithin(3, 0, 2); 
console.info(arr); // [1, 2, 3, 1, 2]
```

## copyWithin

copyWithin(target: int, start: int): this

将数组的一部分浅拷贝到数组中的另一个位置，从`start`索引开始直到数组末尾，不修改其长度。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| target | int | 是 | 复制到的索引位置。|
| start | int | 是 | 开始复制元素的源索引。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| this | 转换后的数组实例本身。|

**示例：**

```ts
const arr = new Array<string>("a", "b", "c", "d");
arr.copyWithin(1, 2); 
console.info(arr); // ["a", "c", "c", "d"]
```

## copyWithin

copyWithin(target: int): this

将数组的一部分浅拷贝到数组中的另一个位置，从索引0开始直到数组末尾，不修改其长度。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| target | int | 是 | 复制到的索引位置。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| this | 转换后的数组实例本身。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3, 4);
arr.copyWithin(2); 
console.info(arr); // [1, 2, 1, 2]
```

## fill

fill(value: T, start?: Number, end?: Number): this

用一个静态值填充数组中的所有元素，可以指定填充的起始和结束索引。

> **说明：**
>
> 这是一个修改原数组的方法。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | T | 是 | 用来填充数组元素的值。|
| start | Number | 否 | 开始填充的索引。默认值为0。|
| end | Number | 否 | 结束填充的索引（不包含）。默认值为数组长度。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| this | 转换后的数组实例本身。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3, 4);
arr.fill(0, 1, 3);
console.info(arr); // [1, 0, 0, 4]
```

## fill

fill(value: T, start: int, end: int): this

输入一个值value填充数组中的所有元素，指定填充的起始和结束索引。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | T | 是 | 用来填充数组元素的值。|
| start | int | 是 | 开始填充的索引。|
| end | int | 是 | 结束填充的索引（不包含）。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| this | 转换后的数组实例本身。|

**示例：**

```ts
const arr = new Array<string>("a", "b", "c");
arr.fill("x", 1, 3);
console.info(arr); // ["a", "x", "x"]
```

## find

find(predicate: (value: T, index: int, array: Array\<T>) => boolean): T | undefined

返回数组中第一个满足提供的测试函数的元素的值；若无满足条件的的元素，则返回`undefined`。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| predicate | (value: T, index: int, array: Array\<T>) => boolean | 是 | 用于测试数组中每个元素的函数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| T \| undefined | 数组中第一个满足条件的元素值，或`undefined`。|

**示例：**

```ts
const arr = new Array<number>(10, 20, 30);
const result = arr.find((v) => v > 15);
console.info(result); // 20
```

## findIndex

findIndex(predicate: (value: T, index: int, array: Array\<T>) => boolean): int

返回数组中第一个满足参数predicate提供的目标函数的元素的索引，否则返回-1。

> **说明：**
>
> 这是一个修改原数组的方法。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| predicate | (value: T, index: int, array: Array\<T>) => boolean | 是 | 用于测试数组中每个元素的函数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| int | 找到的第一个元素的索引，或 -1。|

**示例：**

```ts
const arr = new Array<number>(10, 20, 30);
const index = arr.findIndex((v) => v === 30);
console.info(index); // 2
```

## findLast

findLast(predicate: (elem: T, index: int, array: Array\<T>) => boolean): T | undefined

倒序遍历数组，返回第一个满足参数predicate提供的测试函数的元素的值，否则返回`undefined`。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| predicate | (elem: T, index: int, array: Array\<T>) => boolean | 是 | 用于测试数组中每个元素的函数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| T \| undefined | 找到的最后一个元素的值，或`undefined`。|

**示例：**

```ts
const arr = new Array<number>(10, 20, 15, 25);
const result = arr.findLast((v) => v > 15);
console.info(result); // 25
```

## every

every(predicate: (value: T, index: int, array: Array\<T>) => boolean): boolean
    
测试数组中的所有元素是否都满足参数predicate提供的测试函数。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| predicate | (value: T, index: int, array: Array\<T>) => boolean | 是 | 用于测试数组中每个元素的函数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| boolean | 如果所有元素都满足测试，返回 `true`，否则返回 `false`。|

**示例：**

```ts
const arr = new Array<number>(2, 4, 6);
const isEven = arr.every((v) => v % 2 === 0);
console.info(isEven); // true
```

## some

some(predicate: (value: T, index: int, array: Array\<T>) => boolean): boolean

测试数组中是否至少有一个元素满足参数predicate提供的测试函数。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| predicate | (value: T, index: int, array: Array\<T>) => boolean | 是 | 用于测试数组中每个元素的函数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| boolean | 如果有任何一个元素满足测试，返回`true`，否则返回`false`。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3);
const hasOdd = arr.some((v) => v % 2 !== 0);
console.info(hasOdd); // true
```

## findLastIndex

findLastIndex(predicate: (element: T, index: int, array: Array\<T>) => boolean): int

倒序遍历数组，返回第一个满足参数predicate提供的测试函数的元素的索引，否则返回-1。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| predicate | (element: T, index: int, array: Array\<T>) => boolean | 是 | 用于测试数组中每个元素的函数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| int | 找到的最后一个元素的索引，或 -1。|

**示例：**

```ts
const arr = new Array<number>(10, 20, 10, 30);
const index = arr.findLastIndex((v) => v === 10);
console.info(index); // 2
```

## reduce

reduce(callbackfn: (previousValue: T, currentValue: T, index: int, array: Array\<T>) => T): T

对数组中的所有元素按索引顺序执行一个回调函数，通过接收上一次迭代的累积结果作为previousValue，最终返回累计结果（不提供初始值）。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| callbackfn | (previousValue: T, currentValue: T, index: int, array: Array\<T>) => T | 是 | 用于累积值的回调函数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| T | 累积的结果。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3);
const sum = arr.reduce((acc, current) => acc + current);
console.info(sum); // 6
```

## reduce

reduce\<U = T>(callbackfn: (previousValue: U, currentValue: T, index: int, array: Array\<T>) => U, initialValue: U): U

对数组中的所有元素按索引顺序执行一个回调函数，通过接收上一次迭代的累积结果作为previousValue，最终返回累计结果（提供初始值）。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| callbackfn | (previousValue: U, currentValue: T, index: int, array: Array\<T>) => U | 是 | 用于累积值的回调函数。|
| initialValue | U | 是 | 累积的初始值。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| U | 累积的结果。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3);
const sum: number = arr.reduce(
    (acc: number, current: number, index: int, array: Array<number>): number => {
        return acc + current;
    }, 
    10 
);
console.info(sum); // 16
```

## reduceRight

reduceRight\<U = T>(callbackfn: (previousValue: U, currentValue: T, index: int, array: Array\<T>) => U, initialValue: U): U

与`reduce`类似，但以降序（从右到左）对数组中的元素应用回调函数。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| callbackfn | (previousValue: U, currentValue: T, index: int, array: Array\<T>) => U | 是 | 用于累积值的回调函数。|
| initialValue | U | 是 | 累积的初始值。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| U | 累积的结果。|

**示例：**

```ts
const arr = new Array<string>("a", "b", "c");
const reversed = arr.reduceRight((acc, current) => acc + current, "");
console.info(reversed); // "cba"
```

## forEach

forEach(callbackfn: (value: T, index: int, array: Array\<T>) => void): void

对数组中的每个元素执行一次提供的回调函数。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| callbackfn | (value: T, index: int, array: Array\<T>) => void | 是 | 对每个元素执行的函数。|

**示例：**

```ts
const arr = new Array<number>(1, 2);
arr.forEach((v) => console.info(v * 2)); // 2,4
```

## slice

slice(start?: Number, end?: Number): Array\<T>

返回一个浅拷贝的新Array\<T\>实例，包含从`start`到`end`（不包含`end`）选择的元素。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| start | Number | 否 | 开始提取的零基索引。默认值为0。|
| end | Number | 否 | 结束提取的零基索引（不包含）。默认值为数组长度。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T\> | 包含提取元素的新Array实例。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3, 4, 5);
const newArr = arr.slice(1, 4);
console.info(newArr); // [2, 3, 4]
```

## slice

slice(start: int, end: int): Array\<T>

返回一个浅拷贝的新Array\<T\>实例，包含从`start`到`end`（不包含`end`）选择的元素。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| start | int | 是 | 开始提取的零基索引。|
| end | int | 是 | 结束提取的零基索引（不包含）。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T\> | 包含提取元素的新Array实例。|

**示例：**

```ts
const arr = new Array<number>(10, 20, 30);
const newArr = arr.slice(0, 1);
console.info(newArr); // [20]
```

## slice

slice(start: int): Array\<T>

返回一个浅拷贝的新Array\<T\>实例，包含从`start`索引开始直到数组末尾的所有元素。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| start | int | 是 | 开始提取的零基索引。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T\> | 包含提取元素的新Array实例。|

**示例：**

```ts
const arr = new Array<string>("a", "b", "c");
const newArr = arr.slice(1);
console.info(newArr); // ["b", "c"]
```

## lastIndexOf

lastIndexOf(searchElement: T, fromIndex?: int): int

返回给定元素在数组中最后一次出现的索引，如果不存在则返回-1。从`fromIndex`开始向后搜索。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| searchElement | T | 是 | 要定位的元素。|
| fromIndex | int | 否 | 开始向后搜索的零基索引。默认值为0。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| int | 元素在数组中最后一次出现的索引，-1 如果未找到。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3, 2, 1);
const index = arr.lastIndexOf(2, 3);
console.info(index); // 3
```

## lastIndexOf

lastIndexOf(searchElement: T): int

返回给定元素在数组中最后一次出现的索引，如果不存在则返回-1。从数组末尾开始向后搜索。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| searchElement | T | 是 | 要定位的元素。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| int | 元素在数组中最后一次出现的索引，-1如果未找到。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3, 2, 1);
const index = arr.lastIndexOf(2);
console.info(index); // 3
```

## join

join(sep?: String): string

将数组中的所有元素连接成一个字符串并返回，元素之间用指定的分隔符分隔。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| sep | String | 否 | 指定的分隔符字符串。默认值为","。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| string | 包含所有数组元素连接而成的新字符串。|

**示例：**

```ts
const arr = new Array<string>("a", "b", "c");
const str = arr.join("-");
console.info(str); // "a-b-c"
```

## toString

toString(): string

返回表示指定数组及其元素的字符串。相当于调用`join(",")`。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| string | 数组的字符串表示。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3);
const str = arr.toString();
console.info(str); // "1,2,3"
```

## toLocaleString

toLocaleString(locales: Object, options: Object): string

以自定义国际化格式接收locales和options参数，将指定数组包含的元素连接成字符串。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | Object | 是 | 一个对象，代表用于格式化数字或日期的语言环境或区域设置。|
| options | Object | 是 | 一个对象，包含用于格式化的配置选项，例如数字样式、日期组件等。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| string | 方法实际返回一个表示数组及其元素的本地化字符串，但目前实现为抛出Error。|


**示例：**

```ts
const arr = new Array<number>(1000, 2000);
arr.toLocaleString(
        { lang: "en-US" },  // locales 参数
        { style: "decimal", useGrouping: false } // options 参数
    ); // "1000,2000"
```

## toLocaleString

toLocaleString(locales: Object): string

以自定义国际化格式接收locales参数，将指定数组包含的元素连接成字符串。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | Object | 是 | 一个对象，代表用于格式化数字或日期的语言环境或区域设置。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| string | 当前实现中，它会调用上一个重载版本，并最终抛出错误。理论上，它返回一个表示数组及其元素的本地化字符串。|

**示例：**

```ts
const arr = new Array<number>(2);
arr.toLocaleString({ lang: "zh-CN" }); // "2000,1000"
```

## toLocaleString

toLocaleString(): string

以默认国际化格式将指定数组包含的元素连接成字符串。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| string | 表示数组中所有元素连接而成的字符串，元素之间以逗号分隔。|

**示例：**

```ts
const arr = new Array<number>(3);
arr[0] = 10;
arr[1] = 20;
arr[2] = 30;
console.info(arr.toLocaleString()); // "10,20,30"
```

## toSpliced

toSpliced(start?: Number, delete?: Number): Array\<T>

`splice()` 的复制版本（功能增强）。返回一个新数组，其中一些元素在给定索引处被移除和/或替换。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| start | Number | 否 | 开始修改的索引。默认值为数组长度。|
| delete | Number | 否 | 要删除的元素数量。默认值为数组长度。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T\> | 经过修改后的新Array实例。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3, 4);
const newArr = arr.toSpliced(1, 2); 
console.info(newArr); // [1,4]
console.info(arr); // [1,2,3,4]
```

## toSpliced

toSpliced(start: number, delete: number, ...items: FixedArray\<T>): Array\<T>

`splice()`的复制版本（功能增强）。返回一个新数组，其中一些元素在给定索引处被移除和/或替换。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| start | number | 是 | 开始修改的索引。|
| delete | number | 是 | 要删除的元素数量。|
| ...items | FixedArray\<T> | 否 | 要添加到数组中的元素。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T\> | 经过修改后的新Array实例。|

**示例：**

```ts
const arr = new Array<string>("a", "b", "c");
const newArr = arr.toSpliced(1, 1, "x", "y"); 
console.info(newArr); // ["a","x","y","c"]
```

## toSpliced

toSpliced(start: int, delete: int, ...items: FixedArray\<T>): Array\<T>

`splice()`的复制版本（功能增强）。返回一个新数组，其中一些元素在给定索引处被移除和/或替换。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| start | int | 是 | 开始修改的索引。|
| delete | int | 是 | 要删除的元素数量。|
| ...items | FixedArray\<T> | 否 | 要添加到数组中的元素。默认值为空数组[]。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T\> | 经过修改后的新Array实例。|

**示例：**

```ts
const arr = new Array<number>(10, 20, 30);
const newArr = arr.toSpliced(0, 0, 5); 
console.info(newArr); // [10,20,30,5]
```

## toSpliced

toSpliced(start: int): Array\<T>

`splice()`的复制版本（功能增强）。返回一个新数组，其中从`start`索引开始直到数组末尾的所有元素都被删除。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| start | int | 是 | 开始删除的索引。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T\> | 经过修改后的新Array实例。|

**示例：**

```ts
const arr = new Array<string>("x", "y", "z");
const newArr = arr.toSpliced(1); 
console.info(newArr); // ["x"]
```

## includes

includes(val: T, fromIndex?: Number): boolean

检查数组是否包含某个值，返回`true`或`false`。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| val | T | 是 | 要搜索的值。|
| fromIndex | Number | 否 | 开始搜索的索引。默认值为0。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| boolean | 如果数组包含该值，返回`true`，否则返回`false`。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3);
console.info(arr.includes(2)); // true
console.info(arr.includes(5)); // false
```

## indexOf

indexOf(val: T, fromIndex?: int): int

返回给定元素在数组中第一次出现的索引，如果不存在则返回-1。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| val | T | 是 | 要搜索的值。 |
| fromIndex | int | 否 | 开始搜索的索引。默认值为0。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| int | 元素的索引，如果未找到返回-1。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3, 2);
const index = arr.indexOf(2, 2);
console.info(index); // 3
```

## indexOf

indexOf(val: T): int

返回给定元素在数组中第一次出现的索引，如果不存在则返回-1。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| val | T | 是 | 要搜索的值。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| int | 元素的索引，如果未找到返回-1。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3, 2);
const index = arr.indexOf(2);
console.info(index); // 1
```

## toSorted

toSorted(): Array\<T>

`sort()`的复制版本（功能增强）。返回一个元素已排序的新数组。使用默认比较器sort（使用原地算法对数组的元素进行排序，并返回对数组的引用）。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T> | 经过排序的数组副本。|

**示例：**

```ts
const arr = new Array<number>(3, 1, 2);
const sortedArr = arr.toSorted();
console.info(sortedArr); // [1,2,3]
console.info(arr); // [3,1,2]
```

## toSorted

toSorted(comparator: (a: T, b: T) => number): Array\<T>

`sort()`的复制版本（功能增强）。使用提供的比较器返回一个元素已排序的新数组。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| comparator | (a: T, b: T) => number | 是 | 用于比较两个元素的函数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T\> | 经过排序的数组副本。|

**示例：**

```ts
const arr = new Array<string>("c", "a", "b");
const sortedArr = arr.toSorted((a, b) => a.localeCompare(b));
console.info(sortedArr); // ["a","b","c"]
```

## reverse

reverse(): this

原地反转数组中元素的顺序，并返回数组本身。

> **说明：**
>
> 这是一个修改原数组的方法。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| this | 经过反转的数组实例本身。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3);
arr.reverse();
console.info(arr); // [3,2,1]
```

## toReversed

toReversed(): Array\<T>

`reverse()`的复制版本（功能增强）。返回一个元素顺序被反转的新数组。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T\> | 经过反转的数组副本。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3);
const reversedArr = arr.toReversed();
console.info(reversedArr); // [3,2,1]
console.info(arr); // [1,2,3]
```

## with

with(index: number, value: T): Array\<T>

返回一个新数组，其中给定索引处的元素已被新值替换（不修改原数组）。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| index | number | 是 | 要替换的元素的索引。|
| value | T | 是 | 新的值。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T\> | 替换了指定元素的新 Array 实例。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3);
const newArr = arr.with(1, 99);
console.info(newArr); // [1,99,3]
console.info(arr); // [1,2,3]
```

## with

with(index: int, value: T): Array\<T>

返回一个新数组，其中给定索引处的元素已被新值替换（不修改原数组）。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| index | int | 是 | 要替换的元素的索引。|
| value | T | 是 | 新的值。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<T\> | 替换了指定元素的新Array实例。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3);
const newArr = arr.with(-1, 0); 
console.info(newArr); // [1,2,0]
```

## values

values(): IterableIterator\<T>

返回一个遍历数组中所有值的迭代器。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| IterableIterator\<T\> | 包含数组值的迭代器。|

**示例：**

```ts
const arr = new Array<string>("a", "b");
const iterator = arr.values();
console.info(iterator.next().value); // "a"
console.info(iterator.next().value); // "b"
```

## entries

entries(): IterableIterator\<[number, T]>

返回一个遍历数组中所有[索引, 值]对的迭代器。

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| IterableIterator\<[number, T]\> | 包含[索引, 值]对的迭代器。|

**示例：**

```ts
const arr = new Array<string>("x", "y");
const iterator = arr.entries();
console.info(iterator.next().value); // [0,"x"]
console.info(iterator.next().value); // [1,"y"]
```

## map

map\<U>(callbackfn: (value: T, index: int, array: Array\<T>) => U): Array\<U>

对数组中的每个元素调用一个定义的回调函数，并返回一个包含结果的新数组。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| callbackfn | (value: T, index: int, array: Array\<T>) => U | 是 | 对每个元素执行的函数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| Array\<U\> | 包含回调函数结果的新Array实例。|

**示例：**

```ts
const arr = new Array<number>(1, 2, 3);
const squared: Array<number> = arr.map((v: number, index: int, array: Array<number>) => {
    return v * v;
});
console.info(squared); // [1,4,9]
```

## reduceRight

reduceRight(callbackfn: (previousValue: T, currentValue: T, index: int, array: Array\<T>) => T): T

与`reduce`类似，但以索引降序的方式（从右到左）对数组中的元素应用回调函数（不提供初始值）。

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| callbackfn | (previousValue: T, currentValue: T, index: int, array: Array\<T>) => T | 是 | 用于累积值的回调函数。|

**返回值：**
| 类型 | 说明 |
| :--- | :--- |
| T | 累积的结果。|

**示例：**

```ts
const arr = new Array<string>("a", "b", "c");
const reversed = arr.reduceRight((acc, current) => acc + current);
console.info(reversed); // "cba"
```