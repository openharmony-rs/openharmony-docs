# Set

Set是一种用于存储唯一值的数据结构。本模块提供唯一值存储与集合运算能力，当需要确保数据唯一性并进行集合操作时，可使用本模块接口进行数据去重和关系判断。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## ReadonlySet\<T>

ReadonlySet是一个接口，它定义了一个只读的键值对集合所需要包含的接口，描述了如何读取一个Set结构的数据，但不包含任何会修改该数据的方法。

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明                         |
| ---- | ---- | ---- | ---- | ---------------------------- |
| size | int  | 是   | 否   | 返回Set中元素的数量。 |


### has

has(value: T): boolean

判断ReadonlySet是否包含指定元素。

**参数**

| 参数名 | 类型 | 必填 | 说明       |
| ------ | ---- | ---- | ---------- |
| value  | T  | 是   | 指定元素。 |

**返回值**

| 类型      | 说明                                |
| --------- | ----------------------------------- |
| boolean | 包含指定元素。返回true表示包含，返回false表示不包含。 |

**示例**

```ts
const set:ReadonlySet<int>= new Set<int>([1, 2, 3]);
console.info(set.has(2)); // true
console.info(set.has(5)); // false
```


### forEach

forEach(callbackfn: (value: T, value2: T, set: ReadonlySet\<T>) => void)

按插入顺序对对每个元素调用一次回调函数。

**参数**

| 参数名     | 类型                                                 | 必填 | 说明               |
| ---------- | ---------------------------------------------------- | ---- | ------------------ |
| callbackfn | (value: T, value2: T, [set: ReadonlySet\<T>](#readonlysett)) => void | 是   | 遍历时执行的回调函数，遍历顺序为元素插入顺序。 |


**示例**

```ts
const set:ReadonlySet<int> = new Set<int>([1, 2, 3]);
set.forEach((v1, v2) => {
  console.info(v1, v2); // 分别输出 1 1, 2 2, 3 3
});
```

### keys

keys(): IterableIterator\<T>

返回新迭代器对象，包含此映射中所有的键。

**返回值**

| 类型                  | 说明             |
| --------------------- | ---------------- |
| IterableIterator\<T> | 该方法返回一个迭代器对象，通过这个迭代器可以按插入顺序逐个检索映射中的所有键。 |

**示例**

```ts
const set:ReadonlySet<int> = new Set<int>([1, 2, 3]);
for (const k of set.keys()) {
  console.info(k); // 输出 1,2,3
}
```

### values

values(): IterableIterator\<T>

返回新迭代器对象，包含此映射中所有键对应的值。

**返回值**

| 类型                  | 说明             |
| --------------------- | ---------------- |
| IterableIterator\<T> | 该方法返回一个迭代器对象，通过这个迭代器可以按插入顺序逐个检索映射中的所有值。 |

**示例**

```ts
const set:ReadonlySet<int> = new Set<int>([1, 2, 3]);
for (const v of set.values()) {
  console.info(v); // 输出 1,2,3
}
```

### entries

entries(): IterableIterator\<[T, T]>

返回包含此映射中包含的键值对的新迭代器对象。

**返回值**

| 类型                       | 说明                    |
| -------------------------- | ----------------------- |
| IterableIterator\<[T, T]> | 该方法返回一个迭代器对象，通过这个迭代器可以按插入顺序逐个检索映射中的所有键值对。 |

**示例**

```ts
const set:ReadonlySet<int> = new Set<int>([1,2]);
const iter = set.entries();
console.info(iter.next().value); // 1,1
console.info(iter.next().value); // 2,2
```


## SetIterator\<T>

Set的迭代器实现，用于遍历集合元素。

### constructor

constructor(it: IterableIterator\<T>)

SetIterator的构造函数。

**参数**

| 参数名 | 类型                  | 必填 | 说明         |
| ------ | --------------------- | ---- | ------------ |
| it     | IterableIterator\<T\> | 是   | 输入的迭代器。 |


### next

next(): IteratorResult\<T>

返回下一个迭代器对象。

**返回值**

| 类型                | 说明           |
| ------------------- | -------------- |
| IteratorResult\<T\> | 下一个迭代结果。 |


### $_iterator

$_iterator(): IterableIterator\<T>

返回一个迭代器，迭代器的每一项都是一个对象，并返回该对象。

**返回值**

| 类型                  | 说明           |
| --------------------- | -------------- |
| IterableIterator\<T> | 返回自身迭代器。 |


## Set\<K>

可读可写的Set实现，继承ReadonlySet接口，支持插入、删除和清空。

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明                         |
| ---- | ---- | ---- | ---- | ---------------------------- |
| size | int  | 是   | 否   | 返回Set中元素的数量。 |

### constructor

constructor(elements?: Iterable\<K> | FixedArray\<K> | null)

使用可迭代对象或固定数组初始化Set。

**参数**

| 参数名  | 类型                                                         | 必填 | 说明                                                |
| ------- | ------------------------------------------------- | ---- | --------------------------------------------------- |
| entries | Iterable<[K, V]> \| readonly ((readonly [K, V]) \| null \| undefined)[] \| null | 否   | 可迭代的键值对集合以及只读数组（包含可能的空值）。|

**返回值**

| 类型     | 说明            |
| -------- | --------------- |
| Set\<K\> | 新建的Set实例 |

**示例**

```ts
const set = new Set<string>(["a", "b"]);
console.info(set.size); // 2
```

### constructor

constructor(set: Set\<K>)

从另一个 `Set` 拷贝内容，构造一个新的 `Set`。

**参数**

| 参数名 | 类型     | 必填 | 说明     |
| ------ | -------- | ---- | -------- |
| set    | Set\<K> | 是   | 要拷贝的Set 。|

**返回值**

| 类型     | 说明            |
| -------- | --------------- |
| Set\<K\> | 新建的Set实例 。|

**示例**

```ts
const set1 = new Set<string>(["a", "b"]);
const set2= new Set<string>(set1)
console.info(set2.size); // 2
console.info(set2.has("a")); // true
```

### constructor

constructor(values: K[])

通过数组初始化Set。

**参数**

| 参数名 | 类型  | 必填 | 说明     |
| ------ | ----- | ---- | -------- |
| values | K[] | 是   | 初始数组。 |

**返回值**

| 类型     | 说明            |
| -------- | --------------- |
| Set\<K\> | 新建的Set实例。 |

**示例**

```ts
const set = new Set<string>(["x", "y"]);
console.info(set.has("y")); // true
```

### constructor

constructor(bucketsCount: int)

通过指定桶数量构造空 `Set`， 注意：这个API未来可能被移除。

**参数**

| 参数名       | 类型  | 必填 | 说明     |
| ------------ | ----- | ---- | -------- |
| bucketsCount | int | 是   | 初始桶数。 |

**返回值**

| 类型     | 说明            |
| -------- | --------------- |
| Set\<K> | 新建的Set实例。 |

**示例**

```ts
const set = new Set<string>(32);
set.add("a");
console.info(set.has("a")); // true
```

### add

add(val: K): this

向Set添加元素。

**参数**

| 参数名 | 类型 | 必填 | 说明       |
| ------ | ---- | ---- | ---------- |
| val    | K  | 是   | 添加成员数据。|

**返回值**

| 类型   | 说明              |
| ------ | ----------------- |
| this | 返回当前Set对象（支持链式调用）。 |

**示例**

```ts
const set = new Set<int>();
set.add(10).add(20);
console.info(set.size); // 2
```

### has

has(val: K): boolean

判断Set是否包含指定元素。

**参数**

| 参数名 | 类型 | 必填 | 说明       |
| ------ | ---- | ---- | ---------- |
| val    | K  | 是   | 要查找的值。 |

**返回值**

| 类型      | 说明                              |
| --------- | --------------------------------- |
| boolean | 包含指定元素。返回true表示包含，返回false表示不包含。 |

**示例**

```ts
const set = new Set<int>([1, 2]);
console.info(set.has(2)); // true
```

### delete

delete(val: K): boolean

删除集合中的指定元素。

**参数**

| 参数名 | 类型 | 必填 | 说明       |
| ------ | ---- | ---- | ---------- |
| val    | K  | 是   | 要删除的元素。 |

**返回值**

| 类型      | 说明                                    |
| --------- | --------------------------------------- |
| boolean | 若删除成功返回true，否则返回false。 |

**示例**

```ts
const set = new Set<int>([1, 2, 3]);
console.info(set.delete(2)); // true
console.info(set.delete(4)); // false
console.info(set.has(2)); // false
```

### clear

clear()

清除Set中的所有元素，并将size置为0。

**示例**

```ts
const set = new Set<int>([1, 2, 3]);
set.clear()
console.info(set.size); // 0
```

### keys

keys(): IterableIterator\<K>

返回新迭代器对象，包含此映射中所有的键。

**返回值**

| 类型                  | 说明       |
| --------------------- | ---------- |
| IterableIterator\<K> | 该方法返回一个迭代器对象，通过这个迭代器可以按插入顺序逐个检索映射中的所有键。 |

**示例**

```ts
const set = new Set<string>(["a", "b"]);
for (const k of set.keys()) {
  console.info(k); // "a", "b"
}
```


### values

values(): IterableIterator\<K>

返回新迭代器对象，包含此映射中所有键对应的值。

**返回值**

| 类型                  | 说明       |
| --------------------- | ---------- |
| IterableIterator\<K\> | 该方法返回一个迭代器对象，通过这个迭代器可以按插入顺序逐个检索映射中的所有值。 |

**示例**

```ts
const set = new Set<string>(["a", "b"]);
for (const k of set.values()) {
  console.info(k); // "a", "b"
}
```


### $_iterator

$_iterator(): IterableIterator\<K>

返回自身值的迭代器。

**返回值**

| 类型                  | 说明       |
| --------------------- | ---------- |
| IterableIterator\<K> | 返回自身值的迭代器。 |

**示例**

```ts
const set = new Set<string>(["x", "y"]);
for (const v of set) {
  console.info(v); // "x", "y"
}
```

### entries

entries(): IterableIterator\<[K, K]>

返回包含此映射中包含的键值对的新迭代器对象。

**返回值**

| 类型                       | 说明                    |
| -------------------------- | ----------------------- |
| IterableIterator\<[K, K]> | 该方法返回一个迭代器对象，通过这个迭代器可以按插入顺序逐个检索映射中的所有键值对。 |

**示例**

```ts
const set = new Set<int>([1,2]);
const iter = set.entries();
console.info(iter.next().value); // 1,1
console.info(iter.next().value); // 2,2
```

### forEach

forEach(callbackfn: (k: K, v: K, set: Set\<K>) => void)

按插入顺序对每个元素调用一次回调函数。

**参数**

| 参数名     | 类型                                | 必填 | 说明     |
| ---------- | ----------------------------------- | ---- | -------- |
| callbackfn | (k: K, v: K, set: Set\<K\>) => void | 是   | 按插入顺序对集合的每个值执行一次回调函数。 |


**示例**

```ts
const set = new Set<int>([1, 2]);
set.forEach((k, v) => {
  console.info(k, v); // 输出 1 1, 2 2
});
```