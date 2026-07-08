# @ohos.util.HashSet (非线性容器HashSet)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong; @lijin1039-->
<!--Designer: @Malzahar; @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

HashSet基于[HashMap](js-apis-hashmap.md)实现。在HashSet中，仅操作元素的值对象，不涉及键的概念。

HashSet和[TreeSet](js-apis-treeset.md)相比，HashSet中的数据按Hash值分布存储，因此元素的插入顺序与遍历时的顺序可能不一致，而TreeSet则是按照元素的自然排序或者自定义比较器进行有序存储。这两种集合中的元素都不允许重复，HashSet允许插入null值，TreeSet不建议插入null值，会影响排序结果。

**推荐使用场景：** 当需要确保集合中元素不重复，或需要去除已有集合中的重复元素时，推荐使用HashSet；也可利用HashSet基于哈希的O(1)查找特性进行高效的元素存在性判断。

文档中使用了泛型，涉及以下泛型标记符：
- T：Type，类型

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 容器类使用静态语言实现，限制了存储位置和属性，不支持自定义属性和方法。


## 导入模块

```ts
import { HashSet } from '@kit.ArkTS';
```

## HashSet

### 属性

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| length | ArkTS-Dyn: number <br> ArkTS-Sta: int | 是 | 否 | HashSet的元素个数。 |

**示例：**

ArkTS-Dyn示例：

```ts
let hashSet = new HashSet<number>();
hashSet.add(1);
hashSet.add(2);
hashSet.add(3);
hashSet.add(4);
hashSet.add(5);
let result = hashSet.length;
console.info("length:", result);  // length: 5
```

ArkTS-Sta示例：

```ts
let hashSet: HashSet<int> = new HashSet<int>();
hashSet.add(1);
hashSet.add(2);
hashSet.add(3);
hashSet.add(4);
hashSet.add(5);
let res = hashSet.length;
console.info("length:", res);  // length: 5
```

### constructor

constructor()

HashSet的构造函数，用于创建一个空的HashSet实例。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200012 | The HashSet's constructor cannot be directly invoked. |

**示例：**

ArkTS-Dyn示例：

```ts
let hashSet = new HashSet<number>();
```

ArkTS-Sta示例：

```ts
let hashSet: HashSet<int> = new HashSet<int>();
```


### isEmpty

isEmpty(): boolean

判断HashSet是否为空。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 为空时返回true，不为空时返回false。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The isEmpty method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
// 创建HashSet实例，判断是否为空
const hashSet = new HashSet<number>();
let result = hashSet.isEmpty();
console.info("result:", result);  // result: true
```

ArkTS-Sta示例：

```ts
const hashSet: HashSet<int> = new HashSet<int>();
let result = hashSet.isEmpty();
console.info("result:", result);  // result: true
```


### has

has(value: T): boolean

判断HashSet是否包含指定元素。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | T | 是 | 指定要查找的元素。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 包含指定元素返回true，不包含指定元素返回false。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The has method cannot be bound. |

**示例：**

```ts
// 创建HashSet实例并添加元素
let hashSet = new HashSet<string>();
hashSet.add("squirrel");
let result = hashSet.has("squirrel");
console.info("result:", result);  // result: true
```


### add

add(value: T): boolean

向HashSet添加元素。成功添加后HashSet的length增加1；若待添加元素已存在则不会重复添加，返回false且length不变。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | T | 是 | 要添加的元素。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 成功添加元素返回true，添加失败返回false。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The add method cannot be bound. |

**示例：**

```ts
// 创建HashSet实例
let hashSet = new HashSet<string>();
// 向HashSet中添加元素
let result = hashSet.add("squirrel");
console.info("result:", result);  // result: true
```


### remove

remove(value: T): boolean

从HashSet中删除指定的元素。成功删除后HashSet的length减少1；若指定元素不存在则集合不变，返回false。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | T | 是 | 指定要删除的元素。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 成功删除指定元素返回true，删除失败返回false。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The remove method cannot be bound. |

**示例：**

```ts
// 创建HashSet实例并添加元素
let hashSet = new HashSet<string>();
hashSet.add("squirrel");
hashSet.add("sparrow");
let result = hashSet.remove("sparrow");
console.info("result:", result);  // result: true
```


### clear

clear(): void

清除HashSet中的所有元素，并将length置为0。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The clear method cannot be bound. |

**示例：**

```ts
// 创建HashSet实例并添加元素
let hashSet = new HashSet<string>();
hashSet.add("squirrel");
hashSet.add("sparrow");
hashSet.clear();
let result = hashSet.isEmpty();
console.info("result:", result);  // result: true
```


### values

values(): IterableIterator&lt;T&gt;

返回包含此HashSet中所有值的新迭代器对象。

> **说明：**
>
> 不建议在values迭代过程中使用add、remove方法，因其可能导致迭代过程中的状态异常，建议使用for循环来进行安全的插入与删除操作。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| IterableIterator&lt;T&gt; | 返回包含此HashSet中所有value的迭代器对象。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The values method cannot be bound. |

**示例：**

```ts
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


### forEach

forEach(callbackFn: (value?: T, key?: T, set?: HashSet&lt;T&gt;) => void, thisArg?: Object): void

在遍历过程中对每个元素调用一次回调函数。不建议在forEach回调中使用add、remove方法修改HashSet，因其可能导致迭代过程中的状态异常。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[forEach](#foreach23)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callbackFn | function | 是 | 回调函数，在遍历过程中对每个元素调用一次。回调参数包括value、key和set，详见callbackFn的参数说明。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值。当需要改变回调函数内this指向时传入此参数，不传入时默认值为当前实例对象。 |

callbackFn的参数说明：
| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | T | 否 | 当前遍历到的元素值。 |
| key | T | 否 | 当前遍历到的元素值（与value相同）。 |
| set | HashSet&lt;T&gt; | 否 | 当前调用forEach方法的实例对象。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The forEach method cannot be bound. |

**示例：**

```ts
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
```ts
// 不建议在forEach中使用add、remove方法，因其可能导致迭代过程中的状态异常，建议使用for循环来进行安全的插入与删除操作。
let hashSet = new HashSet<string>();
for(let i = 0; i < 10; i++) {
  hashSet.add("sparrow" + i);
}
for(let i = 0; i < 10; i++) {
  hashSet.remove("sparrow" + i);
}
```

### forEach<sup>23+</sup>

forEach(callbackFn: HashSetCbFn\<T\>): void

通过回调函数来遍历实例对象上的元素以及元素对应的下标。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[forEach](#foreach)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callbackFn | [HashSetCbFn\<T\>](#hashsetcbfnt23) | 是 | 回调函数。 |


**示例：**

```ts
import { HashSetCbFn } from '@kit.ArkTS';

let hashSet: HashSet<string> = new HashSet<string>();
hashSet.add("sparrow");
hashSet.add("squirrel");
let hashSetCb: HashSetCbFn<string> = (value: string, key: string, set: HashSet<string>): void => {
  console.info("value: " + value, " key: " + key);
};
hashSet.forEach(hashSetCb);
// value:squirrel key:squirrel 
// value:sparrow key:sparrow
```

### entries
entries(): IterableIterator&lt;[T, T]&gt;

返回包含此HashSet中所有元素的新迭代器对象，每个元素以[value, value]形式返回。

> **说明：**
>
> 不建议在entries迭代过程中使用add、remove方法，因其可能导致迭代过程中的状态异常，建议使用for循环来进行安全的插入与删除操作。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| IterableIterator&lt;[T, T]&gt; | 返回包含此HashSet中所有键值对的迭代器对象。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The entries method cannot be bound. |

**示例：**

```ts
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
```ts
// 不建议在entries中使用add、remove方法，因其可能导致迭代过程中的状态异常，建议使用for循环来进行安全的插入与删除操作。
let hashSet = new HashSet<string>();
for(let i = 0; i < 10; i++) {
  hashSet.add("sparrow" + i);
}
for(let i = 0; i < 10; i++) {
  hashSet.remove("sparrow" + i);
}
// key:squirrel
// value:squirrel
// key:sparrow
// value:sparrow
```

### [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;T&gt;

返回一个迭代器，迭代器的每一项为HashSet中的元素。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[$_iterator](#_iterator23)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| IterableIterator&lt;T&gt; | 返回包含此HashSet中所有元素的迭代器对象。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**示例：**

```ts
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

```ts
// 不建议在Symbol.iterator中使用add、remove方法，因其可能导致迭代过程中的状态异常，建议使用for循环来进行安全的插入与删除操作。
let hashSet = new HashSet<string>();
for(let i = 0; i < 10; i++) {
  hashSet.add("sparrow" + i);
}
for(let i = 0; i < 10; i++) {
  hashSet.remove("sparrow" + i);
}
```
### $_iterator<sup>23+</sup>

\$_iterator\(): IterableIterator&lt;T&gt;

返回一个迭代器，迭代器的每一项都是一个JavaScript对象，并返回该对象。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[Symbol.iterator](#symboliterator)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| IterableIterator&lt;T&gt; | 返回一个迭代器。 |

**示例：**

```ts
let hashSet: HashSet<string> = new HashSet<string>();
hashSet.add("squirrel");
hashSet.add("sparrow");

// 使用方法一：
let val: Array<string> = Array.from(hashSet.values())
for (let item of val) {
  console.info("value: " + item);
}

// 使用方法二：
let iter = hashSet.$_iterator();
let temp: IteratorResult<string> = iter.next();
while(!temp.done) {
  console.info("value: " + temp.value);
  temp = iter.next();
}
```

### HashSetCbFn\<T\><sup>23+</sup>

type HashSetCbFn\<T\> = (value: T, key: T, set: HashSet\<T\>) => void

HashSet中forEach方法的回调函数。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | T | 是 | 当前遍历到的元素键值对的值。 |
| key | T | 是 | 当前遍历到的元素键值对的键（和value相同）。 |
| set | [HashSet&lt;T&gt;](#hashset) | 是 | 当前调用[forEach](#foreach23)方法的实例对象。 |