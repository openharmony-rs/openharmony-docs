# HashSet

HashSet是一种非线性容器，用于存储不重复的元素集合，支持高效的元素增删和存在性判断。HashSet基于HashMap实现，仅操作元素的值对象，不涉及键的概念。

**起始版本：** 8

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<T>
```

返回一个迭代器，迭代器的每一项为HashSet中的元素。   
> **说明：**
> 
> 不建议在Symbol.iterator中使用add、remove方法，因其可能导致迭代过程中的状态异常，建议使用for循环来进行安全的插入与删除操作。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator & lt;T & gt; | 返回包含此HashSet中所有元素的迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The Symbol.iterator method cannot be bound. |

**示例**

```TypeScript
// 创建HashSet实例并添加元素
let hashSet = new HashSet<string>();
hashSet.add("squirrel");
hashSet.add("sparrow");

// 使用方法一：
for (let item of hashSet) {
  console.info("value: " + item);
}
// value: squirrel
// value: sparrow

// 使用方法二：
let symbolIterator = hashSet[Symbol.iterator]();
let iterResult: IteratorResult<string> = symbolIterator.next();
while(!iterResult.done) {
  console.info("value: " + iterResult.value);
  iterResult = symbolIterator.next();
}
// value: squirrel
// value: sparrow
```

```TypeScript
// 不建议在Symbol.iterator中使用add、remove方法，因其可能导致迭代过程中的状态异常，建议使用for循环来进行安全的插入与删除操作。
let hashSet = new HashSet<string>();
for(let i = 0; i < 10; i++) {
  hashSet.add("sparrow" + i);
}
for(let i = 0; i < 10; i++) {
  hashSet.remove("sparrow" + i);
}
```

## add

```TypeScript
add(value: T): boolean
```

向HashSet添加元素。成功添加后HashSet的length增加1；若待添加元素已存在则不会重复添加，返回false且length不变。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 要添加的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功添加元素返回true，若元素已存在则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The add method cannot be bound. |

**示例**

```TypeScript
// 创建HashSet实例
let hashSet = new HashSet<string>();
// 向HashSet中添加元素
let result = hashSet.add("squirrel");
console.info("result:", result);  // result: true
```

## clear

```TypeScript
clear(): void
```

清除HashSet中的所有元素，并将length置为0。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The clear method cannot be bound. |

**示例**

```TypeScript
// 创建HashSet实例并添加元素
let hashSet = new HashSet<string>();
hashSet.add("squirrel");
hashSet.add("sparrow");
hashSet.clear();
let result = hashSet.isEmpty();
console.info("result:", result);  // result: true
```

## constructor

```TypeScript
constructor()
```

HashSet的构造函数，用于创建一个空的HashSet实例。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The HashSet's constructor cannot be directly invoked. |

**示例**

```TypeScript
let hashSet = new HashSet<number>();
```

## entries

```TypeScript
entries(): IterableIterator<[T, T]>
```

返回包含此HashSet中所有元素的新迭代器对象，每个元素以[value, value]形式返回。   
> **说明：**
> 
> 不建议在entries迭代过程中使用add、remove方法，因其可能导致迭代过程中的状态异常，建议使用for循环来进行安全的插入与删除操作。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator & lt;[T, T] & gt; | 返回包含此HashSet中所有元素的迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The entries method cannot be bound. |

**示例**

```TypeScript
// 创建HashSet实例并添加元素
let hashSet = new HashSet<string>();
hashSet.add("squirrel");
hashSet.add("sparrow");
let entriesIterator = hashSet.entries();
let iterResult: IteratorResult<[string, string]> = entriesIterator.next();
while(!iterResult.done) {
  console.info("key:" + iterResult.value[0]);
  console.info("value:" + iterResult.value[1]);
  iterResult = entriesIterator.next();
}
// key:squirrel
// value:squirrel
// key:sparrow
// value:sparrow
```

```TypeScript
// 不建议在entries中使用add、remove方法，因其可能导致迭代过程中的状态异常，建议使用for循环来进行安全的插入与删除操作。
let hashSet = new HashSet<string>();
for(let i = 0; i < 10; i++) {
  hashSet.add("sparrow" + i);
}
for(let i = 0; i < 10; i++) {
  hashSet.remove("sparrow" + i);
}
```

## forEach

```TypeScript
forEach(callbackFn: (value?: T, key?: T, set?: HashSet<T>) => void, thisArg?: Object): void
```

在遍历过程中对每个元素调用一次回调函数。不建议在forEach回调中使用add、remove方法修改HashSet，因其可能导致迭代过程中的状态异常。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value?: T, key?: T, set?: HashSet & lt;T & gt;) = & gt; void | 是 | 回调函数，在遍历过程中对每个元素调用一次。回调参数包括value、key和set，详见callbackFn的参数说明。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值。当需要改变回调函数内this指向时传入此参数，不传入时默认值为当前实例对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The forEach method cannot be bound. |

**示例**

```TypeScript
// 创建HashSet实例并添加元素
let hashSet = new HashSet<string>();
hashSet.add("sparrow");
hashSet.add("squirrel");
hashSet.forEach((value: string, key: string): void => {
  console.info("value:", value, "key:", key);
});
// value:squirrel key:squirrel
// value:sparrow key:sparrow
```

```TypeScript
// 不建议在forEach中使用add、remove方法，因其可能导致迭代过程中的状态异常，建议使用for循环来进行安全的插入与删除操作。
let hashSet = new HashSet<string>();
for(let i = 0; i < 10; i++) {
  hashSet.add("sparrow" + i);
}
for(let i = 0; i < 10; i++) {
  hashSet.remove("sparrow" + i);
}
```

## has

```TypeScript
has(value: T): boolean
```

判断HashSet是否包含指定元素，基于哈希值进行查找，具有O(1)的时间复杂度。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 指定要查找的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 包含指定元素返回true，不包含指定元素返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The has method cannot be bound. |

**示例**

```TypeScript
// 创建HashSet实例并添加元素
let hashSet = new HashSet<string>();
hashSet.add("squirrel");
let result = hashSet.has("squirrel");
console.info("result:", result);  // result: true
```

## isEmpty

```TypeScript
isEmpty(): boolean
```

判断HashSet是否为空。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 为空时返回true，不为空时返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The isEmpty method cannot be bound. |

**示例**

```TypeScript
// 创建HashSet实例，判断是否为空
const hashSet = new HashSet<number>();
let result = hashSet.isEmpty();
console.info("result:", result);  // result: true
```

## remove

```TypeScript
remove(value: T): boolean
```

从HashSet中删除指定的元素。成功删除后HashSet的length减少1；若指定元素不存在则集合不变，返回false。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 指定要删除的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功删除指定元素返回true，若指定元素不存在则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The remove method cannot be bound. |

**示例**

```TypeScript
// 创建HashSet实例并添加元素
let hashSet = new HashSet<string>();
hashSet.add("squirrel");
hashSet.add("sparrow");
let result = hashSet.remove("sparrow");
console.info("result:", result);  // result: true
```

## values

```TypeScript
values(): IterableIterator<T>
```

返回包含此HashSet中所有值的新迭代器对象。   
> **说明：**
> 
> 不建议在values迭代过程中使用add、remove方法，因其可能导致迭代过程中的状态异常，建议使用for循环来进行安全的插入与删除操作。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator & lt;T & gt; | 返回包含此HashSet中所有值的迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The values method cannot be bound. |

**示例**

```TypeScript
// 创建HashSet实例并添加元素
let hashSet = new HashSet<string>();
hashSet.add("squirrel");
hashSet.add("sparrow");
let values = hashSet.values();
for (let value of values) {
  console.info("value:", value);
}
// value: squirrel
// value: sparrow
```

## length

```TypeScript
length: number
```

HashSet的元素个数。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang
