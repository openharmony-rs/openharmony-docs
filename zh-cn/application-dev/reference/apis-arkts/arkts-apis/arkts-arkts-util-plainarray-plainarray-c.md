# PlainArray

PlainArray可用于存储具有关联关系的key-value键值对集合，其中key值唯一且类型为number，每个key对应一个value。 PlainArray依据泛型定义，采用轻量级结构。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare class PlainArray<T>--><!--Device-unnamed-declare class PlainArray<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

## $_iterator

```TypeScript
$_iterator(): IterableIterator<[int, T]>
```

返回一个迭代器，每一项都是一个ArkTS对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-$_iterator(): IterableIterator<[int, T]>--><!--Device-PlainArray-$_iterator(): IterableIterator<[int, T]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[int, T]&gt; |  |

**示例：**

```TypeScript
let plainArray: PlainArray<string> = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");

let iter = plainArray.$_iterator();
let temp: IteratorResult<[int, string]> = iter.next();
while(!temp.done) {
  console.info("key:" + temp.value![0]);
  console.info("value:" + temp.value![1]);
  temp = iter.next();
}
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<[number, T]>
```

返回一个包含key-value键值对的迭代器对象，其中key是number类型。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-[Symbol.iterator](): IterableIterator<[number, T]>--><!--Device-PlainArray-[Symbol.iterator](): IterableIterator<[number, T]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[number, T]&gt; | 返回一个迭代器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The Symbol.iterator method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");

for (let item of plainArray) {
  console.info("value:" + item[1], "index:" + item[0]);
}
// value:squirrel index:1
// value:sparrow index:2
```

```TypeScript
// 不建议在Symbol.iterator中使用add、remove、removeAt方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
let plainArray = new PlainArray<string>();
for(let i = 0; i < 10; i++) {
  plainArray.add(i,"123");
}

for(let i = 0; i < 10; i++) {
  plainArray.remove(i);
}
```

## add

ArkTS-Dyn:
```TypeScript
add(key: number, value: T): void
```

ArkTS-Sta:
```TypeScript
add(key: int, value: T): void
```

向容器中添加一组数据。若指定的key不存在，则新增键值对，且length增加；若指定的key存在，则替换该key对应的value值。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-add(key: int, value: T): void--><!--Device-PlainArray-add(key: int, value: T): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 添加成员数据的键名。取值范围为[-2147483648, 2147483647]，即int32范围。 |
| value | T | 是 | 添加成员数据的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The add method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
console.info("result:", plainArray.get(1));  // result: squirrel
```

## clear

```TypeScript
clear(): void
```

清除容器中的所有元素，并将length置为0。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-clear(): void--><!--Device-PlainArray-clear(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The clear method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
plainArray.clear();
let result = plainArray.isEmpty();
console.info("result:", result);  // result: true
```

## clone

```TypeScript
clone(): PlainArray<T>
```

克隆一个实例，并返回克隆后的实例。修改克隆后的实例并不会影响原实例。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-clone(): PlainArray<T>--><!--Device-PlainArray-clone(): PlainArray<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 返回新的对象的克隆实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The clone method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let newPlainArray = plainArray.clone();
console.info("result:", newPlainArray.get(1));  // result: squirrel
```

## constructor

```TypeScript
constructor()
```

PlainArray的构造函数。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-constructor()--><!--Device-PlainArray-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The PlainArray's constructor cannot be directly invoked. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
```

## forEach

```TypeScript
forEach(callbackFn: (value: T, index?: number, PlainArray?: PlainArray<T>) => void, thisArg?: Object): void
```

在遍历PlainArray实例对象中每一个元素的过程中，对每个元素执行回调函数。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-forEach(callbackFn: (value: T, index?: number, PlainArray?: PlainArray<T>) => void, thisArg?: Object): void--><!--Device-PlainArray-forEach(callbackFn: (value: T, index?: number, PlainArray?: PlainArray<T>) => void, thisArg?: Object): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value: T, index?: number, PlainArray?: PlainArray&lt;T&gt;) =&gt; void | 是 | 回调函数。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值，默认值为当前实例对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The forEach method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
plainArray.forEach((value: string, index: number) => {
  console.info("value:" + value, "index:" + index);
});
// value:squirrel index:1
// value:sparrow index:2
```

```TypeScript
// 不建议在forEach中使用add、remove、removeAt方法，因其可能导致迭代过程中的状态异常，建议使用for循环来进行安全的插入与删除操作。
let plainArray = new PlainArray<string>();
for (let i = 0; i < 10; i++) {
  plainArray.add(i, "123");
}

for (let i = 0; i < 10; i++) {
  plainArray.remove(i);
}
```

## forEach

```TypeScript
forEach(callbackFn: PlainArrayForEachCb<T>): void
```

在遍历PlainArray实例对象中每一个元素的过程中，对每个元素执行回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-forEach(callbackFn: PlainArrayForEachCb<T>): void--><!--Device-PlainArray-forEach(callbackFn: PlainArrayForEachCb<T>): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 | 回调函数。 |

**示例：**

```TypeScript
import { PlainArrayForEachCb } from '@kit.ArkTS';

let plainArray: PlainArray<string> = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let plainArrayCb: PlainArrayForEachCb<string> = (value: string, key: int, PlainArray: PlainArray<string>) => {
  console.info("value: " + value, " key: " + key);
}
plainArray.forEach(plainArrayCb);
```

## get

```TypeScript
get(key: number): T
```

获取指定key所对应的value。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-get(key: number): T--><!--Device-PlainArray-get(key: number): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | number | 是 | 查找的指定key。取值范围为[-2147483648, 2147483647]，即int32范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回key映射的value值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The get method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.get(1);
console.info("result:", result);  // result: squirrel
```

## get

```TypeScript
get(key: int): T | undefined
```

查询与指定key关联的value。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-get(key: int): T | undefined--><!--Device-PlainArray-get(key: int): T | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | int | 是 | 查找的目标key。该值为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 键值对中的value。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

**示例：**

```TypeScript
let plainArray: PlainArray<string> = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.get(1);
```

## getIndexOfKey

ArkTS-Dyn:
```TypeScript
getIndexOfKey(key: number): number
```

ArkTS-Sta:
```TypeScript
getIndexOfKey(key: int): int
```

查找指定key对应的下标值，如果未找到则返回-1。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-getIndexOfKey(key: int): int--><!--Device-PlainArray-getIndexOfKey(key: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 指定key。需要小于等于int32\_\_\_ESCAPED\_UNDERSCORE\_\_\_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 返回指定key对应的下标值，查找失败返回-1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getIndexOfKey method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.getIndexOfKey(2);
console.info("result:", result); // result: 1
```

## getIndexOfValue

ArkTS-Dyn:
```TypeScript
getIndexOfValue(value: T): number
```

ArkTS-Sta:
```TypeScript
getIndexOfValue(value: T): int
```

查找指定value元素第一次出现的下标值，如果未找到则返回-1。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-getIndexOfValue(value: T): int--><!--Device-PlainArray-getIndexOfValue(value: T): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 指定value元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 返回指定value元素第一次出现时的下标值，查找失败返回-1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getIndexOfValue method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.getIndexOfValue("squirrel");
console.info("result:", result);  // result: 0
```

## getKeyAt

ArkTS-Dyn:
```TypeScript
getKeyAt(index: number): number
```

ArkTS-Sta:
```TypeScript
getKeyAt(index: int): int
```

查找指定下标元素键值对中的key值。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-getKeyAt(index: int): int--><!--Device-PlainArray-getKeyAt(index: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 指定下标。需要小于等于int32\_\_\_ESCAPED\_UNDERSCORE\_\_\_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 返回该下标元素键值对中的key值，失败返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getKeyAt method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.getKeyAt(1);
console.info("result:", result); // result: 2
```

## getValueAt

ArkTS-Dyn:
```TypeScript
getValueAt(index: number): T
```

ArkTS-Sta:
```TypeScript
getValueAt(index: int): T
```

查找指定下标元素键值对中的Value值，失败则返回undefined。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-getValueAt(index: int): T--><!--Device-PlainArray-getValueAt(index: int): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 指定下标。需要小于等于int32\_\_\_ESCAPED\_UNDERSCORE\_\_\_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回该下标元素键值对中的value值，失败返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getValueAt method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.getValueAt(1);
console.info("result:", result);  // result: sparrow
```

## has

ArkTS-Dyn:
```TypeScript
has(key: number): boolean
```

ArkTS-Sta:
```TypeScript
has(key: int): boolean
```

判断容器中是否包含指定key。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-has(key: int): boolean--><!--Device-PlainArray-has(key: int): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 指定key。取值范围为[-2147483648, 2147483647]，即int32范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 包含指定key返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The has method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
let result = plainArray.has(1);
console.info("result:", result); // result: true
```

## isEmpty

```TypeScript
isEmpty(): boolean
```

判断容器是否为空。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-isEmpty(): boolean--><!--Device-PlainArray-isEmpty(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 为空返回true，不为空返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The isEmpty method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
let result = plainArray.isEmpty();
console.info("result:", result); // result: true
```

## remove

```TypeScript
remove(key: number): T
```

删除指定key对应的键值对。指定key不存在时，返回undefined。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-remove(key: number): T--><!--Device-PlainArray-remove(key: number): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | number | 是 | 指定key。需要小于等于int32\_\_\_ESCAPED\_UNDERSCORE\_\_\_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回所删除的键值对中的value值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The remove method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.remove(2);
console.info("result:", result);  // result: sparrow
```

## remove

```TypeScript
remove(key: int): T | undefined
```

如果存在指定key对应的键值对，则删除并返回该值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-remove(key: int): T | undefined--><!--Device-PlainArray-remove(key: int): T | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | int | 是 | 待删除的目标key。该值为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 如果key存在则返回映射的值，否则返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

**示例：**

```TypeScript
let plainArray: PlainArray<string> = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.remove(2);
```

## removeAt

```TypeScript
removeAt(index: number): T
```

删除指定下标对应的元素。指定[0, PlainArray.length-1]以外的值时会返回undefined。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-removeAt(index: number): T--><!--Device-PlainArray-removeAt(index: number): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 指定元素下标。需要小于等于int32\_\_\_ESCAPED\_UNDERSCORE\_\_\_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回删除的元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The removeAt method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.removeAt(1);
console.info("result:", result);  // result: sparrow
```

## removeAt

```TypeScript
removeAt(index: int): T | undefined
```

如果存在指定下标的键值对，则删除并返回该值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-removeAt(index: int): T | undefined--><!--Device-PlainArray-removeAt(index: int): T | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 查找的目标下标。该值为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | T类型的值，容器为空时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

**示例：**

```TypeScript
let plainArray: PlainArray<string> = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.removeAt(1);
```

## removeRangeFrom

ArkTS-Dyn:
```TypeScript
removeRangeFrom(index: number, size: number): number
```

ArkTS-Sta:
```TypeScript
removeRangeFrom(index: int, size: int): int
```

删除指定范围内的元素。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-removeRangeFrom(index: int, size: int): int--><!--Device-PlainArray-removeRangeFrom(index: int, size: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 删除元素的起始下标。取值范围为[0, PlainArray.length-1]，且需要小于等于int32\_\_\_ESCAPED\_UNDERSCORE\_\_\_max即2147483647。 |
| size | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 期望删除元素个数。需要大于0，小于等于int32\_\_\_ESCAPED\_UNDERSCORE\_\_\_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 实际删除元素个数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The removeRangeFrom method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
// 从下标1开始删除元素
let result = plainArray.removeRangeFrom(1, 3);
console.info("result:", result);  // result: 1
```

## setValueAt

ArkTS-Dyn:
```TypeScript
setValueAt(index: number, value: T): void
```

ArkTS-Sta:
```TypeScript
setValueAt(index: int, value: T): void
```

替换容器中指定下标对应键值对中的value值。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-setValueAt(index: int, value: T): void--><!--Device-PlainArray-setValueAt(index: int, value: T): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 指定替换数据下标。取值范围为[0, PlainArray.length-1]，且需要小于等于int32\_\_\_ESCAPED\_UNDERSCORE\_\_\_max即2147483647。 |
| value | T | 是 | 替换键值对中的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The setValueAt method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
let plainArray = new PlainArray<string | number>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
// 替换plainArray中下标为1的键值对中的value值为3546
plainArray.setValueAt(1, 3546);
// 获取并打印plainArray中下标为1的键值对中的value值
let result = plainArray.getValueAt(1);
console.info("result:", result);  // result: 3546
```

ArkTS-Sta示例：

```TypeScript
let plainArray: PlainArray<string | int> = new PlainArray<string | int>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
plainArray.setValueAt(1, 3546);
let result = plainArray.getValueAt(1); 
console.info("result:", result);  // result: 3546
```

## toString

```TypeScript
toString(): String
```

获取包含容器中所有键和值的字符串。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-toString(): String--><!--Device-PlainArray-toString(): String-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| String | 返回将容器中所有键和值拼接而成的字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The toString method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.toString();
console.info("result:", result);  // result: 1:squirrel,2:sparrow
```

## length

```TypeScript
length: number
```

PlainArray的元素个数。

**类型：** number

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-length: number--><!--Device-PlainArray-length: number-End-->

**系统能力：** SystemCapability.Utils.Lang

