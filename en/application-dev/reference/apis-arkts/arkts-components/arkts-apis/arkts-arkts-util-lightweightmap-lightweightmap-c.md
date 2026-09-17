# LightWeightMap

LightWeightMap stores key-value (KV) pairs. Each key must be unique and have only one value.

**Since:** 8

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { LightWeightMap } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<[K, V]>
```

returns an ES6 iterator.Each item of the iterator is a Javascript Object

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;[K, V]&gt; |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The Symbol.iterator method cannot be bound. |

**Examples**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);

// Method 1:
for (let item of lightWeightMap) {
  console.info("key:", item[0]);
  console.info("value:", item[1]);
}
// key: sparrow
// value: 356
// key: squirrel
// value: 123

// Method 2:
let iter = lightWeightMap[Symbol.iterator]();
let temp: IteratorResult<Object[]> = iter.next();
while(!temp.done) {
  console.info("key:", temp.value[0]);
  console.info("value:", temp.value[1]);
  temp = iter.next();
}
// key: sparrow
// value: 356
// key: squirrel
// value: 123
```

```TypeScript
// You are not advised to use the set, setValueAt, remove, or removeAt APIs in Symbol.iterator because they may cause unpredictable risks such as infinite loops. You can use the for loop when inserting or deleting data.
let lightWeightMap = new LightWeightMap<string, number>();
for(let i = 0; i < 10; i++) {
  lightWeightMap.set("sparrow" + i, 123);
}
for(let i = 0; i < 10; i++) {
  lightWeightMap.remove("sparrow" + i);
}
```

## clear

```TypeScript
clear(): void
```

Clears this LightWeightMap and sets its length to **0**.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The clear method cannot be bound. |

**Examples**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
lightWeightMap.clear();
let result = lightWeightMap.isEmpty();
console.info("result:", result);  // result: true
```

## constructor

```TypeScript
constructor()
```

A constructor used to create a **LightWeightMap** instance.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-constructor-calling-failure) | The LightWeightMap's constructor cannot be directly invoked. |

**Examples**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
```

## entries

```TypeScript
entries(): IterableIterator<[K, V]>
```

Returns an iterator that contains all the elements in this LightWeightMap.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;[K, V]&gt; | Iterator obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The entries method cannot be bound. |

**Examples**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let iter = lightWeightMap.entries();
let temp: IteratorResult<Object[]> = iter.next();
while(!temp.done) {
  console.info("key:" + temp.value[0]);
  console.info("value:" + temp.value[1]);
  temp = iter.next();
}
```

```TypeScript
// You are not advised to use the set, setValueAt, remove, or removeAt APIs in entries because they may cause unpredictable risks such as infinite loops. You can use the for loop when inserting or deleting data.
let lightWeightMap = new LightWeightMap<string, number>();
for(let i = 0; i < 10; i++) {
  lightWeightMap.set("sparrow" + i, 123);
}
for(let i = 0; i < 10; i++) {
  lightWeightMap.remove("sparrow" + i);
}
```

## forEach

```TypeScript
forEach(callbackFn: (value?: V, key?: K, map?: LightWeightMap<K, V>) => void, thisArg?: Object): void
```

Uses a callback to traverse the elements in this LightWeightMap and obtain their indexes.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | (value?: V, key?: K, map?: LightWeightMap&lt;K, V&gt;) =&gt; void | Yes | Callback invoked to traverse the elements in the LightWeightMap. |
| thisArg | Object | No | Value of **this** to use when **callbackFn** is invoked. The default value is this instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The forEach method cannot be bound. |

**Examples**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("sparrow", 123);
lightWeightMap.set("gull", 357);
lightWeightMap.forEach((value: number, key: string) => {
  console.info("value:" + value, "key:" + key);
});
// value:123 key:sparrow
// value:357 key:gull
```

```TypeScript
// You are not advised to use the set, setValueAt, remove, or removeAt APIs in forEach because they may cause unpredictable risks such as infinite loops. You can use the for loop when inserting or deleting data.
let lightWeightMap = new LightWeightMap<string, number>();
for(let i = 0; i < 10; i++) {
  lightWeightMap.set("sparrow" + i, 123);
}
for(let i = 0; i < 10; i++) {
  lightWeightMap.remove("sparrow" + i);
}
```

## get

```TypeScript
get(key: K): V
```

Obtains the value of the specified key in this LightWeightMap.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | Target key. |

**Return value:**

| Type | Description |
| --- | --- |
| V | Value of the key. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The get method cannot be bound. |

**Examples**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.get("sparrow");
console.info("result:", result);  // result: 356
```

## getIndexOfKey

```TypeScript
getIndexOfKey(key: K): number
```

Obtains the index of the first occurrence of an element with the specified key in this LightWeightMap.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | Key of the element. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the element. If no match is found, **-1** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getIndexOfKey method cannot be bound. |

**Examples**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getIndexOfKey("sparrow");
console.info("result:", result);  // result: 0
```

## getIndexOfValue

```TypeScript
getIndexOfValue(value: V): number
```

Obtains the index of the first occurrence of an element with the specified value in this LightWeightMap.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | V | Yes | Key of the element. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the element. If no match is found, **-1** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getIndexOfValue method cannot be bound. |

**Examples**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getIndexOfValue(123);
console.info("result:", result);  // result: 1
```

## getKeyAt

```TypeScript
getKeyAt(index: number): K
```

Obtains the key of an element at the specified position in this LightWeightMap.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Position index of the element. The value must be less than or equal to int32_max, that is, 2147483647. |

**Return value:**

| Type | Description |
| --- | --- |
| K | Key obtained. If the key is not found, **undefined** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getKeyAt method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |

**Examples**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getKeyAt(1);
console.info("result:", result);  // result: squirrel
```

## getValueAt

```TypeScript
getValueAt(index: number): V
```

Obtains the value of an element at the specified position in this LightWeightMap.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Position index of the element. The value must be less than or equal to int32_max, that is, 2147483647. |

**Return value:**

| Type | Description |
| --- | --- |
| V | Value obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getValueAt method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |

**Examples**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getValueAt(1);
console.info("result:", result);  // result: 123
```

## hasAll

```TypeScript
hasAll(map: LightWeightMap<K, V>): boolean
```

Checks whether this LightWeightMap contains all elements of the specified **LightWeightMap** instance.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| map | [LightWeightMap](arkts-arkts-util-lightweightmap-lightweightmap-c.md)&lt;K, V&gt; | Yes | **LightWeightMap** instance to be used for comparison. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if all the elements in the specified LightWeightMap are contained; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The hasAll method cannot be bound. |

**Examples**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let map = new LightWeightMap<string, number>();
map.set("sparrow", 356);
let result = lightWeightMap.hasAll(map); 
console.info("result = ", result); // result = true
```

## hasKey

```TypeScript
hasKey(key: K): boolean
```

Checks whether this LightWeightMap has the specified key.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | Target key. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the specified key is contained; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The hasKey method cannot be bound. |

**Examples**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
let result = lightWeightMap.hasKey("squirrel");
console.info("result:", result);  // result: true
```

## hasValue

```TypeScript
hasValue(value: V): boolean
```

Checks whether this LightWeightMap has the specified value.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | V | Yes | Target value. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Operation result. The value **true** is returned if the specified value is contained; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The hasValue method cannot be bound. |

**Examples**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
let result = lightWeightMap.hasValue(123);
console.info("result:", result);  // result: true
```

## increaseCapacityTo

```TypeScript
increaseCapacityTo(minimumCapacity: number): void
```

Increases the capacity of this LightWeightMap. If the passed-in capacity is greater than or equal to the number of elements in this LightWeightMap, the capacity is changed to the new capacity. If the passed-in capacity is less than the number of elements in this LightWeightMap, the capacity is not changed.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| minimumCapacity | number | Yes | Minimum number of elements to accommodate in this LightWeightMap. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The increaseCapacityTo method cannot be bound. |

**Examples**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.increaseCapacityTo(10);
```

## isEmpty

```TypeScript
isEmpty(): boolean
```

Checks whether this LightWeightMap is empty (contains no element).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the LightWeightMap is empty; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The isEmpty method cannot be bound. |

**Examples**

```TypeScript
const lightWeightMap = new LightWeightMap<string, number>();
let result = lightWeightMap.isEmpty();
console.info("result:", result);  // result: true
```

## keys

```TypeScript
keys(): IterableIterator<K>
```

Returns an iterator that contains all the keys in this LightWeightMap.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;K&gt; | Iterator obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The keys method cannot be bound. |

**Examples**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let keys = lightWeightMap.keys();
for (let key of keys) {
  console.info("key:", key);
}
// key: sparrow
// key: squirrel
```

## remove

```TypeScript
remove(key: K): V
```

Removes an element with the specified key from this LightWeightMap.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | Target key. |

**Return value:**

| Type | Description |
| --- | --- |
| V | Value of the element removed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The remove method cannot be bound. |

**Examples**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.remove("sparrow");
console.info("result:", result);  // result: 356
```

## removeAt

```TypeScript
removeAt(index: number): boolean
```

Removes an element at the specified position from this LightWeightMap.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Position index of the element. The value must be less than or equal to int32_max, that is, 2 147483647. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Operation result. The value **true** is returned if the element is removed; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The removeAt method cannot be bound. |

**Examples**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.removeAt(1);
console.info("result:", result);  // result: true
```

## set

```TypeScript
set(key: K, value: V): Object
```

Adds or updates an element in this LightWeightMap.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | Key of the target element. |
| value | V | Yes | Value of the target element. |

**Return value:**

| Type | Description |
| --- | --- |
| Object | LightWeightMap that contains the new element. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The set method cannot be bound. |

**Examples**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
let result = lightWeightMap.set("squirrel", 123);
console.info("result:", result);  // result: squirrel:123
```

## setAll

```TypeScript
setAll(map: LightWeightMap<K, V>): void
```

Adds all elements in a LightWeightMap to this LightWeightMap.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| map | [LightWeightMap](arkts-arkts-util-lightweightmap-lightweightmap-c.md)&lt;K, V&gt; | Yes | LightWeightMap whose elements are to be added to the current LightWeightMap. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The setAll method cannot be bound. |

**Examples**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let map = new LightWeightMap<string, number>();
map.setAll(lightWeightMap);   // Add all elements in lightWeightMap to the map.
let result = map.get("sparrow");
console.info("result:", result);  // result: 356
```

## setValueAt

```TypeScript
setValueAt(index: number, newValue: V): boolean
```

Sets a value for an element at the specified position in this LightWeightMap.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Position index of the element. The value must be less than or equal to int32_max, that is, 2 147483647. |
| newValue | V | Yes | Value of the target element to set. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Operation result. The value **true** is returned if the value is set successfully; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The setValueAt method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |

**Examples**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
lightWeightMap.setValueAt(1, 3546);
console.info("result:", lightWeightMap.get("squirrel"));  // result: 3546
```

## toString

```TypeScript
toString(): String
```

Concatenates the elements in this LightWeightMap into a string and returns the string.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| String | String obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The toString method cannot be bound. |

**Examples**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.toString();
console.info("result:", result);  // result: sparrow:356,squirrel:123
```

## values

```TypeScript
values(): IterableIterator<V>
```

Returns an iterator that contains all the values in this LightWeightMap.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;V&gt; | Iterator obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The values method cannot be bound. |

**Examples**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let values = lightWeightMap.values();
for (let value of values) {
  console.info("value:", value);
}
// value: 356
// value: 123
```

## length

```TypeScript
length: number
```

Number of elements in a LightWeightMap.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
