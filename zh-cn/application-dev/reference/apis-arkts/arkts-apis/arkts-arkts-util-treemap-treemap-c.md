# TreeMap

TreeMap可用于存储具有关联关系的key-value键值对集合，存储元素中key值唯一，每个key对应一个value。TreeMap底层使用红黑树实现，可以利用二叉树特性快速查找键值对。key值有序存储，可以实现快速的插入和删除。

**起始版本：** 8

<!--Device-unnamed-declare class TreeMap<K, V>--><!--Device-unnamed-declare class TreeMap<K, V>-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { TreeMap } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<[K, V]>
```

返回一个迭代器，迭代器的每一项都是一个JavaScript对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeMap-[Symbol.iterator](): IterableIterator<[K, V]>--><!--Device-TreeMap-[Symbol.iterator](): IterableIterator<[K, V]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator<[K, V]> | @throws { BusinessError } 10200011 - The Symbol.iterator method cannot be bound. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The Symbol.iterator method cannot be bound. |

**示例：**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
treeMap.set('sparrow', 356);

// 使用方法一：
for (let item of treeMap) {
  console.info('TreeMap:', item[0], item[1]);
}
// 输出结果：
// TreeMap: sparrow,356
// TreeMap: squirrel,123

// 使用方法二：
let iter = treeMap[Symbol.iterator]();
let nextResult: IteratorResult<Object[]> = iter.next();
while (!nextResult.done) {
  console.info('key:', nextResult.value[0]);
  console.info('value:', nextResult.value[1]);
  nextResult = iter.next();
}
// 输出结果：
// key: sparrow
// value: 356
// key: squirrel
// value: 123

```

```TypeScript
 // 不建议在Symbol.iterator中使用set、remove方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
 let treeMap = new TreeMap<string, number>();
 for (let i = 0; i < 10; i++) {
   treeMap.set('sparrow' + i, 123);
 }
 for (let i = 0;i < 10; i++) {
   treeMap.remove('sparrow' + i);
 }

```

## clear

```TypeScript
clear(): void
```

清除容器中的所有元素，并将length置为0。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeMap-clear(): void--><!--Device-TreeMap-clear(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The clear method cannot be bound. |

**示例：**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
treeMap.set('sparrow', 356);
// 清除容器中的所有元素
treeMap.clear();
let result = treeMap.isEmpty();
console.info('result:', result); // result: true

```

## constructor

```TypeScript
constructor(comparator?: (firstValue: K, secondValue: K) => boolean)
```

TreeMap的构造函数，支持通过比较函数使元素按照自定义规则排序。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeMap-constructor(comparator?: (firstValue: K, secondValue: K) => boolean)--><!--Device-TreeMap-constructor(comparator?: (firstValue: K, secondValue: K) => boolean)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| comparator | (firstValue: K, secondValue: K) => boolean | 否 | 比较函数。comparator（可选）用户自定义的比较函数。firstValue（必填）前一项元素。secondValue（必填）后一项元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The TreeMap's constructor cannot be directly invoked. |

**示例：**

```TypeScript
// 默认构造
let treeMap = new TreeMap<number, number>();

```

```TypeScript
//使用comparator firstValue < secondValue，表示期望结果为升序排序。反之firstValue > secondValue，表示为降序排序。
let treeMap: TreeMap<string, string> = new TreeMap<string, string>((firstValue: string, secondValue: string): boolean => {
  return firstValue > secondValue;
});
treeMap.set('aa', '3');
treeMap.set('dd', '1');
treeMap.set('cc', '2');
treeMap.set('bb', '4');
for (let item of treeMap) {
  console.info('key: ' + item[0], 'value: ' + item[1]);
};
// 输出结果：
// key: dd value: 1
// key: cc value: 2
// key: bb value: 4
// key: aa value: 3

```

```TypeScript
// 当插入自定义类型时，则必须要提供比较函数。
class TestEntry {
  public id: number = 0;
}

let testEntryMap: TreeMap<TestEntry, string> = new TreeMap<TestEntry, string>((t1: TestEntry, t2: TestEntry): boolean => {
  return t1.id < t2.id;
});
let entry1: TestEntry = {
  id: 0
};
let entry2: TestEntry = {
  id: 1
}
testEntryMap.set(entry1, '0');
testEntryMap.set(entry2, '1');
console.info('length:', testEntryMap.length); // length: 2

```

## entries

```TypeScript
entries(): IterableIterator<[K, V]>
```

返回包含此映射中键值对的新迭代器对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeMap-entries(): IterableIterator<[K, V]>--><!--Device-TreeMap-entries(): IterableIterator<[K, V]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator<[K, V]> | @throws { BusinessError } 10200011 - The entries method cannot be bound. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The entries method cannot be bound. |

**示例：**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
treeMap.set('sparrow', 356);
// 获取键值对迭代器
let entriesIterator = treeMap.entries();
// 通过迭代器遍历所有键值对
let nextResult: IteratorResult<Object[]> = entriesIterator.next();
while (!nextResult.done) {
  console.info('TreeMap:', nextResult.value);
  nextResult = entriesIterator.next();
}
// 输出结果：
// TreeMap: sparrow,356
// TreeMap: squirrel,123

```

```TypeScript
 // 不建议在entries中使用set、remove方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
 let treeMap = new TreeMap<string, number>();
 for (let i = 0; i < 10; i++) {
   treeMap.set('sparrow' + i, 123);
 }
 for (let i = 0;i < 10; i++) {
   treeMap.remove('sparrow' + i);
 }

```

## forEach

```TypeScript
forEach(callbackFn: (value?: V, key?: K, map?: TreeMap<K, V>) => void, thisArg?: Object): void
```

通过回调函数来遍历实例对象上的元素及其下标。不会对已删除的key执行回调。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeMap-forEach(callbackFn: (value?: V, key?: K, map?: TreeMap<K, V>) => void, thisArg?: Object): void--><!--Device-TreeMap-forEach(callbackFn: (value?: V, key?: K, map?: TreeMap<K, V>) => void, thisArg?: Object): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value?: V, key?: K, map?: TreeMap<K, V>) => void | 是 | 回调函数。callbackFn（必填）接受最多三个参数的函数。对每个元素调用的函数。 |
| thisArg | Object | 否 | this值。thisArg（可选）当callbackFn被调用时作为this值使用的对象。如果省略thisArg，则使用undefined作为this值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The forEach method cannot be bound. |

**示例：**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set('sparrow', 123);
treeMap.set('gull', 357);
// 通过回调函数遍历TreeMap中的所有元素
treeMap.forEach((value: number, key: string): void => {
  console.info('value: ' + value, 'key: ' + key);
});
// 输出结果：
// value: 357 key: gull
// value: 123 key: sparrow

```

```TypeScript
 // 不建议在forEach中使用set、remove方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
 let treeMap = new TreeMap<string, number>();
 for (let i = 0; i < 10; i++) {
   treeMap.set('sparrow' + i, 123);
 }
 for (let i = 0; i < 10; i++) {
   treeMap.remove('sparrow' + i);
 }

```

## get

```TypeScript
get(key: K): V
```

获取指定key所对应的value，若为空则返回undefined。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeMap-get(key: K): V--><!--Device-TreeMap-get(key: K): V-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 指定key。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | 返回值或undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The get method cannot be bound. |

**示例：**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
treeMap.set('sparrow', 356);
// 获取指定key对应的value
let result = treeMap.get('sparrow');
console.info('result:', result); // result: 356

```

## getFirstKey

```TypeScript
getFirstKey(): K
```

获取容器中排序第一的key，若为空则返回undefined。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeMap-getFirstKey(): K--><!--Device-TreeMap-getFirstKey(): K-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| K | 返回值或undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getFirstKey method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+**ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

**示例：**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
treeMap.set('sparrow', 356);
// 获取容器中排序第一的key
let result = treeMap.getFirstKey();
console.info('result:', result); // result: sparrow

```

## getHigherKey

```TypeScript
getHigherKey(key: K): K
```

获取容器中大于对比key值的最小键，如果不存在大于对比key值的键值，则返回undefined。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeMap-getHigherKey(key: K): K--><!--Device-TreeMap-getHigherKey(key: K): K-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 对比的key值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| K | 返回排序中key后一位的数据，为空时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getHigherKey method cannot be bound. |

**示例：**

```TypeScript
let treeMap = new TreeMap<number, string>();
treeMap.set(1, 'one');
treeMap.set(2, 'two');
treeMap.set(3, 'three');
treeMap.set(4, 'four');
// 获取大于对比key值3的最小键
let result = treeMap.getHigherKey(3);
console.info('result:', result); // result: 4

```

## getLastKey

```TypeScript
getLastKey(): K
```

获取容器中排序最后的key，若为空则返回undefined。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeMap-getLastKey(): K--><!--Device-TreeMap-getLastKey(): K-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| K | 返回值或undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getLastKey method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+**ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

**示例：**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
treeMap.set('sparrow', 356);
// 获取容器中排序最后的key
let result = treeMap.getLastKey();
console.info('result:', result); // result: squirrel

```

## getLowerKey

```TypeScript
getLowerKey(key: K): K
```

获取容器中小于对比key值的最大键，如果不存在小于对比key值的键值，则返回undefined。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeMap-getLowerKey(key: K): K--><!--Device-TreeMap-getLowerKey(key: K): K-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 对比的key值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| K | 返回排序中key前一位的数据，为空时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getLowerKey method cannot be bound. |

**示例：**

```TypeScript
let treeMap = new TreeMap<number, string>();
treeMap.set(1, 'one');
treeMap.set(2, 'two');
treeMap.set(3, 'three');
treeMap.set(4, 'four');
// 获取小于对比key值3的最大键
let result = treeMap.getLowerKey(3);
console.info('result:', result); // result: 2

```

## hasKey

```TypeScript
hasKey(key: K): boolean
```

判断容器中是否包含指定key。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeMap-hasKey(key: K): boolean--><!--Device-TreeMap-hasKey(key: K): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 指定key。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | boolean类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The hasKey method cannot be bound. |

**示例：**

```TypeScript
let treeMap = new TreeMap<string, number>();
// 向容器中添加数据
treeMap.set('squirrel', 123);
// 判断容器中是否包含指定key
let result = treeMap.hasKey('squirrel');
console.info('result:', result);  // result: true

```

## hasValue

```TypeScript
hasValue(value: V): boolean
```

判断容器中是否包含该指定value。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeMap-hasValue(value: V): boolean--><!--Device-TreeMap-hasValue(value: V): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | V | 是 | 指定value。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | boolean类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The hasValue method cannot be bound. |

**示例：**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
// 判断容器中是否包含指定value
let result = treeMap.hasValue(123);
console.info('result:', result);  // result: true

```

## isEmpty

```TypeScript
isEmpty(): boolean
```

判断容器是否为空。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeMap-isEmpty(): boolean--><!--Device-TreeMap-isEmpty(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | boolean类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The isEmpty method cannot be bound. |

**示例：**

```TypeScript
let treeMap = new TreeMap<number, number>();
// 判断容器是否为空
let result = treeMap.isEmpty();
console.info('result:', result);  // result: true

```

## keys

```TypeScript
keys(): IterableIterator<K>
```

返回包含此映射中所有键的新迭代器对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeMap-keys(): IterableIterator<K>--><!--Device-TreeMap-keys(): IterableIterator<K>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator<K> | @throws { BusinessError } 10200011 - The keys method cannot be bound. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The keys method cannot be bound. |

**示例：**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
treeMap.set('sparrow', 356);
// 获取包含所有键的迭代器
let keys = treeMap.keys();
for (let key of keys) {
  console.info('key:', key);
}
// 输出结果：
// key: sparrow
// key: squirrel

```

## remove

```TypeScript
remove(key: K): V
```

删除指定key对应的元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeMap-remove(key: K): V--><!--Device-TreeMap-remove(key: K): V-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 指定key。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | 返回删除元素的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The remove method cannot be bound. |

**示例：**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
treeMap.set('sparrow', 356);
let result = treeMap.remove('sparrow'); // 删除数据
console.info('result = ' + result); // result = 356

```

## replace

```TypeScript
replace(key: K, newValue: V): boolean
```

对容器中一组数据进行更新（替换）。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeMap-replace(key: K, newValue: V): boolean--><!--Device-TreeMap-replace(key: K, newValue: V): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 指定key。 |
| newValue | V | 是 | 替换的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | boolean类型（key是否指向目标元素）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The replace method cannot be bound. |

**示例：**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set('sparrow', 123);
// 替换指定key对应的value
treeMap.replace('sparrow', 357);
console.info('sparrow:', treeMap.get('sparrow')); // sparrow: 357

```

## set

```TypeScript
set(key: K, value: V): Object
```

向容器中添加或更新一组数据。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeMap-set(key: K, value: V): Object--><!--Device-TreeMap-set(key: K, value: V): Object-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 添加成员数据的键名。 |
| value | V | 是 | 添加成员数据的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 返回添加后的TreeMap。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The set method cannot be bound. |

**示例：**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
console.info('squirrel:', treeMap.get('squirrel')); // squirrel: 123

```

## setAll

```TypeScript
setAll(map: TreeMap<K, V>): void
```

将一个TreeMap中的所有元素组添加到另一个TreeMap中。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeMap-setAll(map: TreeMap<K, V>): void--><!--Device-TreeMap-setAll(map: TreeMap<K, V>): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| map | [TreeMap](arkts-arkts-util-treemap-treemap-c.md)<K, V> | 是 | 该map会添加到其调用setAll接口的map对象中。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The setAll method cannot be bound. |

**示例：**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
treeMap.set('sparrow', 356);
let map: TreeMap<string, number> = new TreeMap();
map.set('demo', 12);
map.setAll(treeMap); // 将treeMap中的所有元素添加到map中
map.forEach((value?: number, key?: string) : void => {
  console.info('value: ' + value, 'key: ' + key); 
});
// 输出结果:
// value: 12 key: demo
// value: 356 key: sparrow
// value: 123 key: squirrel

```

## values

```TypeScript
values(): IterableIterator<V>
```

返回包含此映射中键值的新迭代器对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeMap-values(): IterableIterator<V>--><!--Device-TreeMap-values(): IterableIterator<V>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator<V> | @throws { BusinessError } 10200011 - The values method cannot be bound. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The values method cannot be bound. |

**示例：**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
treeMap.set('sparrow', 356);
// 获取包含所有值的迭代器
let values = treeMap.values();
for (let value of values) {
  console.info('value:', value);
}
// value: 356
// value: 123

```

## length

```TypeScript
length: number
```

TreeMap的元素个数。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeMap-length: number--><!--Device-TreeMap-length: number-End-->

**系统能力：** SystemCapability.Utils.Lang

