# HashSet

HashSet基于HashMap实现。在HashSet中，仅处理value对象。

**起始版本：** 8

**系统能力：** SystemCapability.Utils.Lang

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<T>
```

返回一个迭代器，迭代器的每一项都是一个JavaScript对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;T&gt; | @throws { BusinessError } 10200011 - The Symbol.iterator method cannot be bound. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../../errorcode-universal.md#10200011-The) | The Symbol.iterator method cannot be bound. |

**示例：**

```TypeScript
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
let iter = hashSet[Symbol.iterator]();
let temp: IteratorResult<string> = iter.next();
while(!temp.done) {
  console.info("value: " + temp.value);
  temp = iter.next();
}
// value: squirrel
// value: sparrow

```

```TypeScript
// 不建议在Symbol.iterator中使用set、remove方法，因其可能导致迭代过程中的状态异常，建议使用for循环来进行安全的插入与删除操作。
let hashSet = new HashSet<string>();
for(let i = 0;i < 10;i++) {
  hashSet.add("sparrow" + i);
}
for(let i = 0;i < 10;i++) {
  hashSet.remove("sparrow" + i);
}

```

## add

```TypeScript
add(value: T): boolean
```

向HashSet添加元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 添加成员数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功添加元素返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../../errorcode-universal.md#10200011-The) | The add method cannot be bound. |

**示例：**

```TypeScript
let hashSet = new HashSet<string>();
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
| [10200011](../../errorcode-universal.md#10200011-The) | The clear method cannot be bound. |

**示例：**

```TypeScript
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

HashSet的构造函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../../errorcode-universal.md#10200012-The) | The HashSet's constructor cannot be directly invoked. |

**示例：**

```TypeScript
let hashSet = new HashSet<number>();

```

## entries

```TypeScript
entries(): IterableIterator<[T, T]>
```

返回包含此映射中所有键值对的新迭代器对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[T, T]&gt; | 返回一个迭代器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../../errorcode-universal.md#10200011-The) | The entries method cannot be bound. |

**示例：**

```TypeScript
let hashSet = new HashSet<string>();
hashSet.add("squirrel");
hashSet.add("sparrow");
let iter = hashSet.entries();
let temp: IteratorResult<[string, string]> = iter.next();
while(!temp.done) {
  console.info("key:" + temp.value[0]);
  console.info("value:" + temp.value[1]);
  temp = iter.next();
}
// key:squirrel
// value:squirrel
// key:sparrow
// value:sparrow

```

```TypeScript
// 不建议在entries中使用set、remove方法，因其可能导致迭代过程中的状态异常，建议使用for循环来进行安全的插入与删除操作。
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

在遍历过程中对每个元素调用一次回调函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value?: T, key?: T, set?: HashSet&lt;T&gt;) =&gt; void | 是 | 回调函数。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值，默认值为当前实例对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../../errorcode-universal.md#10200011-The) | The forEach method cannot be bound. |

**示例：**

```TypeScript
let hashSet = new HashSet<string>();
hashSet.add("sparrow");
hashSet.add("squirrel");
hashSet.forEach((value: string, key: string): void => {
  console.info("value:" + value, "key:" + key);
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

判断HashSet是否包含指定元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 指定元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 包含指定元素返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../../errorcode-universal.md#10200011-The) | The has method cannot be bound. |

**示例：**

```TypeScript
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
| boolean | 为空返回true，不为空返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../../errorcode-universal.md#10200011-The) | The isEmpty method cannot be bound. |

**示例：**

```TypeScript
const hashSet = new HashSet<number>();
let result = hashSet.isEmpty();
console.info("result:", result);  // result: true

```

## remove

```TypeScript
remove(value: T): boolean
```

从HashSet中删除指定的元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 指定删除的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功删除指定元素返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../../errorcode-universal.md#10200011-The) | The remove method cannot be bound. |

**示例：**

```TypeScript
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

返回包含此映射中所有键值的新迭代器对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;T&gt; | 返回一个迭代器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../../errorcode-universal.md#10200011-The) | The values method cannot be bound. |

**示例：**

```TypeScript
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

