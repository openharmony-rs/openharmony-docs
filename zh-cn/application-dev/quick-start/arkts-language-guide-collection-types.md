---
kits: ["ArkTS Kit / 方舟编程语言"]
description: "介绍ArkTS的数组、元组、Set、Map等集合类型及只读集合，讲解遍历迭代、集合选型流程，帮助开发者按场景正确选用集合。"
keywords: [集合类型, 数组, Array, Map, 元组, Set, forEach, ReadonlyArray, 迭代器]
doctype: guide
status: active
---

# 集合类型
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

集合类型用于存储多个数据项。ArkTS提供多种集合类型，包括数组、元组、`Set`、`Map`等，每种类型有其特定的用途和特性。三类核心集合的差异是选型的前提：数组（`Array`）是有序、可重复的元素列表，通过索引访问，适合存储有序数据；集合（`Set`）存储不重复的元素，适合去重和成员存在性检查；映射（`Map`）存储键值对，键的类型不受限，适合通过键快速查找值。此外，集合按可变性还可区分为可变集合与只读集合（如`ReadonlyArray`）。

## 数组（Array）

数组是存储有序元素集合的最常用数据结构。数组中的元素按索引排列，索引从0开始，可以动态添加和删除元素。

数组常用于存储有序的数据列表（如用户列表、商品列表、日志记录）、表示序列数据（如时间序列、事件流）、处理批量数据（如批量操作、批量转换、批量查询）或作为栈或队列使用（如任务队列、历史记录）。其核心特性包括：元素按插入顺序存储且索引从0开始（有序性）、可动态添加、删除、修改元素（可变性）、所有元素必须为相同类型或联合类型（类型约束）、长度可随时改变（动态长度）。

### 数组的声明与初始化

数组可以通过字面量或构造函数创建，声明时指定元素类型以确保类型安全。

<!-- @[array_creation_methods](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
// 使用类型后缀 []
let numbers: number[] = [1, 2, 3, 4, 5];
let strings: string[] = ['a', 'b', 'c'];
let booleans: boolean[] = [true, false, true];

// 使用泛型Array
let numbers2: Array<number> = [1, 2, 3];
let strings2: Array<string> = ['hello', 'world'];

// 空数组
let empty: number[] = [];
let empty2: string[] = [];

// 联合类型数组
let mixed: (number | string)[] = [1, 'two', 3, 'four'];
let nullable: (number | null)[] = [1, null, 3];

// 使用扩展运算符创建
let original: number[] = [1, 2, 3];
let copy: number[] = [...original];
let extended: number[] = [...original, 4, 5];
```

`number[]`和`Array<number>`功能等价，推荐使用`number[]`形式（更简洁），`Array<T>`语法则适合需要强调泛型的场景。扩展运算符`...original`创建新数组，修改副本不影响原数组。

### 访问与修改数组元素

数组元素通过索引访问和修改，常用于读取值、更新数据、数据处理和运行时状态更新等场景。

<!-- @[array_element_access](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let arr: number[] = [10, 20, 30, 40, 50];

// 读取元素
let first: number = arr[0];   // 10
let second: number = arr[1];  // 20
let last: number = arr[arr.length - 1];  // 50

// 修改元素
arr[0] = 100;
arr[1] = 200;
console.info(`${arr.join(', ')}`);  // 100, 200, 30, 40, 50

// 越界访问
let outOfBounds: number | undefined = arr[10];
console.info(`${outOfBounds}`);  // undefined

// 安全访问
let index: number = 5;
if (index >= 0 && index < arr.length) {
  let safe: number = arr[index];
}
```

数组越界访问返回`undefined`而非抛出异常，因此访问不确定索引前应进行边界检查。

### 数组的遍历

数组遍历常用于数据处理、查找、统计和转换。选择方式时：只需值用`for...of`，需要索引用`for`循环，函数式处理用`forEach`，遍历中不要修改数组长度。

<!-- @[array_for_loop_iteration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let iterArr: number[] = [1, 2, 3, 4, 5];

for (let value of iterArr) {
  console.info(`${value}`);
}

// 获取索引和值
for (let i = 0; i < iterArr.length; i++) {
  console.info(`Index ${i}: ${iterArr[i]}`);
}
```

`forEach`方法以函数式风格遍历数组，对每个元素执行回调：

<!-- @[array_forEach_method](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let forEachArr: number[] = [1, 2, 3];

forEachArr.forEach((value: number, index: number): void => {
  console.info(`Index ${index}: ${value}`);
});
```

`forEach`不支持`break`，需要提前退出遍历时使用`for...of`或`for`循环。

<!-- @[array_indexed_iteration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let iterArr2: number[] = [1, 2, 3];

for (let i = 0; i < iterArr2.length; i++) {
  console.info(`${iterArr2[i]}`);
}
```

需要手动控制遍历节奏时，可通过`values()`获取迭代器，用`next()`逐个取值：

<!-- @[array_iterator_manual](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let manualArr: number[] = [1, 2, 3];
let arrIter: IterableIterator<number> = manualArr.values();

let iterResult: IteratorResult<number> = arrIter.next();
while (!iterResult.done) {
  console.info(`${iterResult.value}`);  // 依次输出 1, 2, 3
  iterResult = arrIter.next();
}
```

### 数组的常用操作

数组提供`push`、`pop`、`shift`、`splice`等常用操作，用于增删改查元素。

<!-- @[array_add_elements](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let elemArr: number[] = [1, 2];

// push：末尾添加
elemArr.push(3);
elemArr.push(4, 5);  // 可添加多个
let newLength: number = elemArr.push(6);  // 返回新长度

// unshift：开头添加
elemArr.unshift(0);
elemArr.unshift(-1, -2);  // 可添加多个

console.info(`${elemArr.join(', ')}`);  // -1, -2, 0, 1, 2, 3, 4, 5, 6
```

删除元素使用`pop`、`shift`、`splice`等方法：

<!-- @[array_remove_elements](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let elemArr2: number[] = [1, 2, 3, 4, 5];

// pop：删除末尾
let elemLast: number | undefined = elemArr2.pop();  // 5
console.info(`${elemArr2.join(', ')}`);  // 1, 2, 3, 4

// shift：删除开头
let elemFirst: number | undefined = elemArr2.shift();  // 1
console.info(`${elemArr2.join(', ')}`);  // 2, 3, 4

// splice：删除指定位置
let removed: number[] = elemArr2.splice(1, 2);  // 删除索引1开始的2个元素
console.info(`${elemArr2.join(', ')}`);  // 2
console.info(`${removed.join(', ')}`);  // 3, 4
```

`concat`和`slice`方法用于拼接和截取数组，均返回新数组而不修改原数组：

<!-- @[array_concat_and_slice](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let arr1: number[] = [1, 2];
let arr2: number[] = [3, 4];

// concat：拼接数组
let combined: number[] = arr1.concat(arr2);
console.info(`${combined.join(', ')}`);  // 1, 2, 3, 4
let concatExtended: number[] = arr1.concat(3, 4, [5, 6]);
console.info(`${concatExtended.join(', ')}`);  // 1, 2, 3, 4, 5, 6

// slice：拆分/截取
let sliceArr: number[] = [1, 2, 3, 4, 5];
let sub: number[] = sliceArr.slice(1, 4);
console.info(`${sub.join(', ')}`);  // 2, 3, 4
let tail: number[] = sliceArr.slice(2);
console.info(`${tail.join(', ')}`);  // 3, 4, 5
let sliceCopy: number[] = sliceArr.slice();
console.info(`${sliceCopy.join(', ')}`);  // 1, 2, 3, 4, 5（拷贝）
```

数组的查找与过滤方法包括`indexOf`、`includes`、`find`和`filter`等：

<!-- @[array_search_and_filter](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let filterArr: number[] = [1, 2, 3, 2, 1];

// indexOf：查找索引
let filterIndex: number = filterArr.indexOf(2);  // 1（第一个匹配）
let lastIndex: number = filterArr.lastIndexOf(2);  // 3（最后一个匹配）
let notFound: number = filterArr.indexOf(10);  // -1

// includes：是否包含
let has2: boolean = filterArr.includes(2);  // true
let has10: boolean = filterArr.includes(10);  // false

// find：条件查找
let filterNumbers: number[] = [1, 5, 10, 15, 20];
let found: number | undefined = filterNumbers.find((value: number): boolean => {
  return value > 10;
});  // 15

let foundIndex: number = filterNumbers.findIndex((value: number): boolean => {
  return value > 10;
});  // 3

// filter：过滤
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

### 数组的高阶用法

数组还提供`map`（映射）、`filter`（过滤）、`reduce`（归约）、`sort`/`reverse`（排序）、`flat`/`flatMap`（展平）等函数式方法，支持链式组合实现"筛选→变换→汇总"的数据处理管道。这些方法返回新数组（`sort`/`reverse`除外），不修改原数组。

`map`：映射每个元素

`map`对数组每个元素执行变换，返回新数组。

<!-- @[array_map](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let amNumbers: number[] = [1, 2, 3, 4, 5];

let amDoubled: number[] = amNumbers.map((n: number): number => n * 2);
console.info(`${amDoubled.join(', ')}`);  // 2, 4, 6, 8, 10

let amStrings: string[] = amNumbers.map((n: number): string => `Item ${n}`);
console.info(`${amStrings.join(', ')}`);  // 'Item 1, Item 2, Item 3, Item 4, Item 5'
```

`filter`：过滤元素

`filter`方法对数组每个元素执行判断函数，返回所有满足条件的元素组成的新数组，原数组不变。常用于数据筛选，如从用户列表中筛选活跃用户、从商品列表中筛选在售商品。

<!-- @[array_filter](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let afNumbers: number[] = [1, 2, 3, 4, 5, 6];

let afEvens: number[] = afNumbers.filter((n: number): boolean => n % 2 === 0);
console.info(`${afEvens.join(', ')}`);  // 2, 4, 6
```

`reduce`：归约数组

`reduce`将数组归约为单个值，需提供初始值。

<!-- @[array_reduce](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let arNumbers: number[] = [1, 2, 3, 4, 5];

let arSum: number = arNumbers.reduce((acc: number, n: number): number => acc + n, 0);
console.info(`${arSum.toString()}`);  // 15

let arProduct: number = arNumbers.reduce((acc: number, n: number): number => acc * n, 1);
console.info(`${arProduct.toString()}`);  // 120
```

`sort`与`reverse`：排序

`sort`方法对数组元素原地排序，可传入比较函数自定义排序规则；`reverse`方法将数组元素顺序反转。两者都修改原数组，若需保留原数组，先创建副本（如调用`slice()`或使用展开运算符）再排序。

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

组合使用`map`、`filter`、`reduce`

`map`、`filter`、`reduce`可通过链式调用组合使用，实现"筛选→变换→汇总"的数据处理管道。例如：先`filter`筛选有效数据，再`map`提取关键字段，最后`reduce`计算汇总值。链式调用时每一步返回新数组，不影响原始数据。

<!-- @[array_chain](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let acPrices: number[] = [999, 25, 15, 75];

// 筛选大于50的价格，打八折后求和
let acTotal: number = acPrices
  .filter((price: number): boolean => price > 50)
  .map((price: number): number => Math.round(price * 0.8))
  .reduce((acc: number, price: number): number => acc + price, 0);

console.info(`${acTotal}`);  // 859
```

`flat`与`flatMap`：扁平化与转换扁平化

`flat()`将嵌套数组展平为一维数组，可指定展平深度。`flatMap()`先对每个元素执行转换函数，再将结果展平一级，等价于`map()`后再`flat()`，常用于将嵌套结构转换并展平。两者也可使用`reduce`和展开运算符手动实现相同效果。

<!-- @[flat_flatmap_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let ffnNested: number[][] = [[1, 2], [3, 4], [5, 6]];

// flat：将二维数组展平为一维
let ffnFlat: number[] = ffnNested.flat();
console.info(`${ffnFlat.join(', ')}`); // 1, 2, 3, 4, 5, 6

// flatMap：对每个元素映射后展平一级
let ffnWords: string[] = ['hello world', 'foo bar'];
let ffnFlatMapped: string[] = ffnWords.flatMap((s: string): string[] => s.split(' '));
console.info(`${ffnFlatMapped.join(', ')}`); // 'hello, world, foo, bar'

// reduce和展开运算符替代flat
let ffnFlatReduce: number[] = ffnNested.reduce((acc: number[], arr: number[]): number[] => {
  return [...acc, ...arr];
}, []);
console.info(`${ffnFlatReduce.join(', ')}`); // 1, 2, 3, 4, 5, 6
```

## 元组（Tuple）

元组是固定长度和类型的有序集合。元组与数组不同：元组的长度固定，每个位置的类型可以不同，而数组的长度可变，所有元素类型相同。

- 表示固定结构的数据（如坐标点`[x, y]`、RGB颜色`[r, g, b]`）。
- 返回多个值（如函数返回`[result, error]`）。
- 表示键值对（如`[key, value]`）。
- 定义特定位置有特定类型的数据（如`[id, name, age]`）。

### 元组的声明与初始化

元组通过明确指定每个位置的元素类型来声明，长度和类型序列固定。

<!-- @[tuple_basics](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let tuple: [number, string] = [1, 'hello'];
let coordinate: [number, number] = [10, 20];
let user: [number, string, boolean] = [1, 'Alice', true];
```

上述类型标注中每个位置的类型可以不同，从而表达固定结构的数据。在ArkTS中，简单的固定长度数组可以替代元组的作用。

### 访问元组元素

元组元素通过索引访问，每个位置有明确的类型，编译器会据此进行类型检查；元组也常用于让函数返回多个相关值。

<!-- @[tuple_element_access](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
// 索引访问
let accessTuple: [number, string] = [1, 'hello'];
let num: number = accessTuple[0];    // 1
let str: string = accessTuple[1];    // 'hello'

// 访问数组形式的元组
let accessPair: number[] = [10, 20];
let accessFirst: number = accessPair[0];   // 10
let accessSecond: number = accessPair[1];  // 20
```

元组通过索引访问时，编译器保留每个位置的精确类型信息（如`accessTuple[0]`为`number`，`accessTuple[1]`为`string`）；而使用数组形式（如`number[]`）模拟元组时，类型信息不如真正的元组精确，访问时需要手动进行边界检查。

### 元组与数组的区别

元组具有固定长度和类型序列，数组长度可变且元素类型统一。

<!-- @[tuple_vs_array](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
// 元组：固定长度和类型
let point: [number, number] = [10, 20];  // 只能有两个number

// 数组：可变长度，统一类型
let tupleNumbers: number[] = [1, 2, 3, 4, 5];  // 可添加更多number

// 元组表示固定结构
let userTuple: [number, string, boolean] = [1, 'Alice', true];
console.info(`${userTuple.join(', ')}`);  // '1, Alice, true'

// 数组表示动态集合
let userIds: number[] = [1, 2, 3, 4, 5];
userIds.push(6);  // 可添加
```

## 集合（Set）

`Set`用于存储不重复元素的集合，适合去重、成员存在性检查等场景，与数组不同，`Set`中的元素唯一。

### Set的声明与初始化

`Set`用于存储唯一值的集合，通过构造函数创建并指定元素类型。

<!-- @[set_creation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
// 创建空Set
let emptySet: Set<number> = new Set();

// 从数组创建
let numbersSet: Set<number> = new Set([1, 2, 3, 4, 5]);

// 添加初始元素
let stringSet: Set<string> = new Set();
stringSet.add('a');
stringSet.add('b');
```

### Set的核心特性

`Set`保证元素唯一性，自动去重，提供高效的存在性检查。

<!-- @[set_uniqueness](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let set: Set<number> = new Set([1, 2, 2, 3, 3, 3]);
console.info(`${set.size}`);  // 3（去除重复）

// 添加重复元素无效
set.add(1);
console.info(`${set.size}`);  // 3（不变）

// 去除数组重复元素
let uniqueArr: number[] = [1, 2, 2, 3, 3, 3];
let unique: number[] = Array.from(new Set(uniqueArr));
console.info(`${unique.join(', ')}`);  // 1, 2, 3
```

### Set的常用操作

`Set`提供添加、删除、查找、遍历等基本操作。

<!-- @[set_basic_operations](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let opsSet: Set<number> = new Set([1, 2, 3]);

// add：添加元素（重复添加无效）
opsSet.add(4);
let opsAddedSet: Set<number> = opsSet.add(5);  // 返回Set本身

// delete：删除元素，返回是否成功删除
let opsDeleteResult: boolean = opsSet.delete(2);  // true（成功删除）
let opsRemoveResult: boolean = opsSet.delete(10); // false（不存在）

// has：检查元素是否存在
let opsHas1: boolean = opsSet.has(1);   // true
let opsHas10: boolean = opsSet.has(10); // false

console.info(`${opsSet.size}`);  // 4（元素为1、3、4、5）
```

遍历`Set`用`for...of`或`forEach`，也可通过`values()`、`keys()`获取迭代器：

<!-- @[set_iteration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let iterSet: Set<number> = new Set([1, 2, 3]);

// for...of遍历
for (let value of iterSet) {
  console.info(`${value}`);
}

// forEach方法
iterSet.forEach((value: number): void => {
  console.info(`${value}`);
});

// 获取所有值
let values: IterableIterator<number> = iterSet.values();
for (let value of values) {
  console.info(`${value}`);
}

// 获取所有键（Set中键等于值）
let keys: IterableIterator<number> = iterSet.keys();
for (let key of keys) {
  console.info(`${key}`);
}
```

需要手动控制遍历节奏时，可通过`values()`获取迭代器，用`next()`逐个取值：

<!-- @[set_iterator_manual](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let manualSet: Set<number> = new Set([1, 2, 3]);
let setIter: IterableIterator<number> = manualSet.values();

let setResult: IteratorResult<number> = setIter.next();
while (!setResult.done) {
  console.info(`${setResult.value}`);  // 依次输出 1, 2, 3
  setResult = setIter.next();
}
```

`Set`与数组之间可以相互转换，利用`Set`的唯一性可实现数组去重：

<!-- @[set_array_conversion](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
// Set转数组
let convSet: Set<number> = new Set([1, 2, 3]);
let convArr: number[] = Array.from(convSet);
console.info(`${convArr.join(', ')}`);  // 1, 2, 3

// 数组转Set
let convNumbers: number[] = [1, 2, 2, 3];
let setFromArr: Set<number> = new Set(convNumbers);
console.info(`${Array.from(setFromArr).join(', ')}`);  // 1, 2, 3

// 去重
let duplicates: number[] = [1, 1, 2, 2, 3, 3];
let convUnique: number[] = Array.from(new Set(duplicates));
console.info(`${convUnique.join(', ')}`);  // 1, 2, 3
```

`clear`方法清空`Set`中所有元素：

<!-- @[set_clear_method](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let clearSet: Set<number> = new Set([1, 2, 3]);
clearSet.clear();
console.info(`${clearSet.size}`);  // 0
```

### Set的高阶用法

`Set`本身不提供`map`、`filter`等高阶方法，可先通过`Array.from`转换为数组，使用数组的高阶方法（详细用法见[数组的高阶用法](#数组的高阶用法)）处理后，再转回`Set`：

<!-- @[set_high_order_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let hoSet: Set<number> = new Set([1, 2, 3, 4, 5]);

// 筛选偶数：Set转数组→filter→转回Set
let hoEvens: Set<number> = new Set(
  Array.from(hoSet).filter((n: number): boolean => n % 2 === 0)
);
console.info(`${hoEvens.size}`);  // 2（元素为2、4）
```

## 映射（Map）

`Map`是存储键值对的集合，键和值可以是任意类型。

### Map的声明与初始化

`Map`用于存储键值对的集合，通过构造函数创建并指定键和值的类型。

<!-- @[map_creation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
// 创建空Map
let emptyMap: Map<string, number> = new Map();

// 从数组创建（键值对数组）
let initMap: Map<string, number> = new Map([
  ['a', 1],
  ['b', 2],
  ['c', 3]
]);

// 添加初始键值对
let map: Map<string, number> = new Map();
map.set('one', 1);
map.set('two', 2);
```

### 键值对的访问、添加与删除

`Map`通过`get`、`set`、`delete`方法访问和修改键值对，支持动态数据管理。

<!-- @[map_basic_operations](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let opsMap: Map<string, number> = new Map();

// 添加键值对
opsMap.set('a', 1);
opsMap.set('b', 2);
opsMap.set('c', 3);

// 访问值
let valueA: number | undefined = opsMap.get('a');  // 1
let valueB: number | undefined = opsMap.get('b');  // 2
let opsNotFound: number | undefined = opsMap.get('x');  // undefined

// 判断键是否存在
let hasA: boolean = opsMap.has('a');  // true
let hasX: boolean = opsMap.has('x');  // false

// 删除键值对
let opsDeleted: boolean = opsMap.delete('b');  // true
let opsNotDeleted: boolean = opsMap.delete('x');  // false

// 更新值
opsMap.set('a', 10);  // 更新 'a' 的值

// 清空Map
opsMap.clear();
console.info(`${opsMap.size}`);  // 0
```

### Map的遍历

`Map`遍历使用`forEach`或`for...of`循环，可以遍历键、值或键值对。

<!-- @[map_iteration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let iterMap: Map<string, number> = new Map([
  ['a', 1],
  ['b', 2],
  ['c', 3]
]);

// forEach遍历
iterMap.forEach((value: number, key: string): void => {
  console.info(`${key}: ${value}`);
});

// for...of遍历entries
for (let entry of iterMap.entries()) {
  let key: string = entry[0];
  let value: number = entry[1];
  console.info(`${key}: ${value}`);
}

// for...of遍历键
for (let key of iterMap.keys()) {
  console.info(`${key}`);
}

// for...of遍历值
for (let value of iterMap.values()) {
  console.info(`${value}`);
}

// 不使用解构遍历，显式读取entry元素
for (let entry of iterMap.entries()) {
  let key: string = entry[0];
  let value: number = entry[1];
  console.info(`${key}: ${value}`);
}
```

需要手动控制遍历节奏时，可通过`entries()`获取迭代器，用`next()`逐个取值：

<!-- @[map_iterator_manual](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let manualMap: Map<string, number> = new Map([['a', 1], ['b', 2]]);
let mapIter: IterableIterator<[string, number]> = manualMap.entries();

let mapResult: IteratorResult<[string, number]> = mapIter.next();
while (!mapResult.done) {
  let entry: [string, number] = mapResult.value;
  console.info(`${entry[0]}: ${entry[1]}`);  // 依次输出 a: 1, b: 2
  mapResult = mapIter.next();
}
```

### Record<K, V> 类型

`Record<K, V>`是ArkTS内置的工具类型，将键类型`K`映射到值类型`V`，适合表达"字符串键值对象"。当键固定为字符串或数值、结构相对简单时，比`Map`更轻量，常用对象字面量初始化。

<!-- @[record_type_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let ages: Record<string, number> = {
  'John': 25,
  'Mary': 21
};
ages['John']; // 25
```

键类型`K`可为`string`或`number`（不含`bigint`），值类型`V`可为任意类型；按下标读取返回`V | undefined`，使用前需判空。

当值为复合结构时，可用接口描述其形状：

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

与`Map`相比，`Record`基于对象字面量、键只能为字符串或数值、无`size`属性（需`Object.keys(obj).length`计算）、不支持任意类型键。需要任意类型键、动态增删键值对或保持插入顺序时优先使用`Map`（见[Map与普通对象的区别](#map与普通对象的区别)）。

### Map与普通对象的区别

`Map`键可以是任意类型，对象键只能是字符串，`Map`更适合动态键值存储。

<!-- @[map_vs_object](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
// Map：任意键类型
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

// Record：适合表达字符串键值对象
let obj: Record<string, number> = {};
obj['key1'] = 1;
obj['key2'] = 2;

let objValue: number | undefined = obj['key1'];
if (objValue !== undefined) {
  console.info(`${objValue}`);
}

// Map：保持顺序
let orderedMap: Map<string, number> = new Map();
orderedMap.set('a', 1);
orderedMap.set('b', 2);
orderedMap.set('c', 3);
console.info(`${Array.from(orderedMap.keys()).join(', ')}`);  // a, b, c（保持顺序）

// Map：直接获取大小
console.info(`${orderedMap.size}`);  // 3

// Object：需要计算大小
let objSize: number = Object.keys(obj).length;
```

### Map的高阶用法

`Map`本身不提供`map`、`filter`等高阶方法，可先通过`Array.from`转换为数组，使用数组的高阶方法（详细用法见[数组的高阶用法](#数组的高阶用法)）处理后，再转回`Map`：

<!-- @[map_high_order_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let hoMap: Map<string, number> = new Map([['a', 1], ['b', 2], ['c', 3]]);

// 筛选值大于1的键值对：Map转数组→filter→转回Map
let hoFiltered: Map<string, number> = new Map(
  Array.from(hoMap).filter((entry: [string, number]): boolean => entry[1] > 1)
);
console.info(`${hoFiltered.size}`);  // 2（'b'、'c'）

// 对所有值求和
let hoTotal: number = Array.from(hoMap.values()).reduce(
  (acc: number, value: number): number => acc + value, 0
);
console.info(`${hoTotal}`);  // 6
```

## 只读集合类型

只读集合类型禁止修改操作，适合传递不变数据。

### 只读数组

只读数组使用`readonly number[]`声明，与`ReadonlyArray<number>`是等价写法，禁止`push`、`pop`等修改操作，只能读取。

<!-- @[readonly_array_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
// readonly number[] 与 ReadonlyArray<number> 是等价写法
let readonlyArr: readonly number[] = [1, 2, 3];
let sameArr: ReadonlyArray<number> = readonlyArr;

// 不可修改
// readonlyArr.push(4);   // 编译错误
// readonlyArr[0] = 10;   // 编译错误

// 可以读取
let roFirst: number = readonlyArr[0];       // 1
let roLength: number = readonlyArr.length;  // 3

// 可变数组可以赋值给只读数组（单向）
let mutableNums: number[] = [1, 2, 3];
let readonlyNums: readonly number[] = mutableNums;
```

### 只读Map与只读Set

只读集合通过`ReadonlyMap`或`ReadonlySet`类型声明，防止意外修改。`ReadonlyMap`和`ReadonlySet`为ArkTS内置只读接口。

<!-- @[readonly_map_set_interfaces](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
// 使用内置的ReadonlyMap返回只读视图
function getReadOnlyMap(): ReadonlyMap<string, number> {
  let map: Map<string, number> = new Map();
  map.set('a', 1);
  return map;  // 返回只读视图
}

// 使用内置的ReadonlySet返回只读视图
function getReadOnlySet(): ReadonlySet<number> {
  let set: Set<number> = new Set([1, 2, 3]);
  return set;  // 返回只读视图
}
```

### 只读元组

只读元组确保数据不被修改，适用于配置数据、常量坐标、函数参数保护等场景，编译器会强制检查修改操作。

<!-- @[readonly_tuple](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
let readonlyTuple: readonly [number, string] = [1, 'hello'];
// readonlyTuple[0] = 2;  // 编译错误
```

### 只读集合的使用场景

只读集合适用于配置数据、常量列表等不应被修改的场景。

<!-- @[readonly_collection_scenarios](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Collections.ets) -->

``` TypeScript
// 配置数据：只读，防止意外修改
const CONFIG: ReadonlyArray<string> = ['api', 'db', 'cache'];

// 函数参数：只读，保护原始数据
function processItems(items: ReadonlyArray<number>): number {
  let sum: number = 0;
  for (let item of items) {
    sum += item;
  }
  return sum;
}

let scenariosNumbers: number[] = [1, 2, 3];
processItems(scenariosNumbers);  // 传入只读视图

// 返回只读结果：防止外部修改
function getConstants(): ReadonlyArray<string> {
  return ['CONST_A', 'CONST_B'];
}
```

## ArkTS共享容器（@arkts.collections）

除本篇介绍的原生集合类型外，ArkTS还提供基于`@arkts.collections`模块的共享容器（如`collections.Array`、`collections.Map`、`collections.Set`），用于并发场景下跨Worker线程的高性能数据传递，导入方式为`import { collections } from '@kit.ArkTS';`（API version 12起支持，仅可在.ets文件中使用）。

共享容器与原生集合类型的主要差异：

- **传递行为**：原生集合跨线程传递（如发送给`Worker`）时进行值拷贝，各线程修改互不影响；共享容器在多个并发实例间默认按引用传递，支持多个并发实例同时操作同一个容器实例，避免大数据量的重复拷贝。
- **线程安全**：共享容器不是线程安全的，内部采用fail-fast机制，检测到多个并发实例同时进行结构性修改时会触发异常，多线程读写需配合异步锁机制保证安全访问；原生集合仅在单线程内使用，无此问题。
- **属性限制**：共享容器实例无法通过`.`或`[]`添加或更新属性。
- **选型建议**：单线程场景使用原生集合；并发场景需要在`Worker`间高效共享数据时使用共享容器。

详细接口说明见[@arkts.collections (ArkTS容器集)](../reference/apis-arkts/arkts-apis-arkts-collections.md)。

## 类型化数组（TypedArray）

TypedArray是一类针对数值计算优化的数组类型，包括Int8Array、Uint8Array、Int16Array、Uint16Array、Int32Array、Uint32Array、Float32Array等，每种类型固定存储对应位宽的数值（如Int8Array存储8位有符号整数，Float32Array存储32位浮点数），元素在内存中连续排列，无需装箱。

与普通数组（`Array`）相比，普通数组是长度动态可变的数组，对象元素存储的是引用，数值元素访问存在装箱与类型检查开销，而TypedArray直接存储原始数值，访问和计算开销更小。因此涉及纯数值计算的场景（如图像像素处理、音频采样数据、科学计算）推荐使用TypedArray，普通数组则适合存储对象、字符串等通用数据。

TypedArray的使用场景与性能对比示例见[高性能编程指南](arkts-high-performance-programming.md)。

## 常用操作速查表

以下速查表按类型汇总常用操作及其行为——是原地修改（修改原集合）还是返回新的集合或值：

**数组常用操作**

| 类型 | 操作 | 行为 |
| --- | --- | --- |
| 数组 | `push`、`unshift`、`pop`、`shift`、`splice` | 原地修改 |
| 数组 | `sort`、`reverse` | 原地修改 |
| 数组 | `concat`、`slice`、`map`、`filter`、`flat`、`flatMap` | 返回新数组 |
| 数组 | `reduce` | 返回归约值，不修改原数组 |
| 数组 | `indexOf`、`includes`、`find`、`findIndex` | 返回查询结果，不修改原数组 |

**Set/Map及类型转换常用操作**

| 类型 | 操作 | 行为 |
| --- | --- | --- |
| `Set` | `add`、`delete`、`clear` | 原地修改 |
| `Set` | `has` | 返回查询结果，不修改原集合 |
| `Map` | `set`、`delete`、`clear` | 原地修改 |
| `Map` | `get`、`has` | 返回查询结果，不修改原集合 |
| 转换 | `Array.from(set)`、`Array.from(map)` | 返回新数组 |
| 转换 | `new Set(arr)`、`new Map(entries)` | 返回新集合 |

## 使用流程

1. 判断数据关系：有序列表用`Array`，唯一值集合用`Set`，键值索引用`Map`，固定长度且各位置类型固定的数据结构优先使用元组或明确的接口。
2. 明确元素类型：声明数组元素、`Set`元素、`Map`键和值的具体类型，不使用`any`或`unknown`接收集合内容。
3. 确认可变边界：函数只读取集合时使用`readonly T[]`（等价于`ReadonlyArray<T>`）；需要写入时只在创建者或专门负责更新的函数中修改。
4. 选择访问方式：数组索引、`find`、`Map.get`等可能返回`undefined`的访问结果必须先判断再使用。
5. 选择遍历方式：只读值用`for...of`，需要索引用`for`或带类型标注的`forEach`，遍历`Map`时显式读取`entry[0]`和`entry[1]`。
6. 检查ArkTS限制：不要使用解构赋值遍历集合，不要把对象键作为普通对象索引，不要把可变集合直接暴露给不该修改它的调用方。
