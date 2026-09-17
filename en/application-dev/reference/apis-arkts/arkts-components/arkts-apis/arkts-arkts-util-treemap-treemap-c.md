# TreeMap

TreeMap stores key-value (KV) pairs. Each key must be unique and have only one value. TreeMap is implemented using a red-black tree, which is a binary search tree where keys are stored in sorted order for efficient insertion and removal.

**Since:** 8

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { TreeMap } from '@kit.ArkTS';
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
let treeMap = new TreeMap<string, number>();
treeMap.set("squirrel", 123);
treeMap.set("sparrow", 356);

// Method 1:
for (let item of treeMap) {
  console.info("TreeMap:", item[0], item[1]);
}
// Output:
// TreeMap: sparrow,356
// TreeMap: squirrel,123

// Method 2:
let iter = treeMap[Symbol.iterator]();
let temp: IteratorResult<Object[]> = iter.next();
while(!temp.done) {
  console.info("key:", temp.value[0]);
  console.info("value:", temp.value[1]);
  temp = iter.next();
}
// Output:
// key: sparrow
// value: 356
// key: squirrel
// value: 123
```

```TypeScript
// You are not advised to use the set or remove APIs in Symbol.iterator because they may cause unpredictable risks such as infinite loops. You can use the for loop when inserting or deleting data.
 let treeMap = new TreeMap<string, number>();
 for(let i = 0; i < 10; i++) {
   treeMap.set("sparrow" + i, 123);
 }
 for(let i = 0;i < 10; i++) {
   treeMap.remove("sparrow" + i);
 }
```

## clear

```TypeScript
clear(): void
```

Clear all element groups in the map

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The clear method cannot be bound. |

**Examples**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set("squirrel", 123);
treeMap.set("sparrow", 356);
treeMap.clear();
let result = treeMap.isEmpty();
console.info("result:", result); // result: true
```

## constructor

```TypeScript
constructor(comparator?: (firstValue: K, secondValue: K) => boolean)
```

A constructor used to create a TreeMap object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| comparator | (firstValue: K, secondValue: K) =&gt; boolean | No | comparator comparator (Optional) User-defined comparison functions. firstValue (required) previous element. secondValue (required) next element. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-constructor-calling-failure) | The TreeMap's constructor cannot be directly invoked. |

**Examples**

```TypeScript
// Default constructor.
let treeMap = new TreeMap<number, number>();
```

```TypeScript
// Use the comparator firstValue < secondValue if the elements are expected to be sorted in ascending order. Use firstValue > secondValue if the elements are expected to be sorted in descending order.
let treeMap: TreeMap<string,string> = new TreeMap<string,string>((firstValue: string, secondValue: string): boolean => {
  return firstValue > secondValue;
});
treeMap.set("aa","3");
treeMap.set("dd","1");
treeMap.set("cc","2");
treeMap.set("bb","4");
for (let item of treeMap) {
  console.info("key: " + item[0], "value: " + item[1]);
}
// Output:
// key: dd value: 1
// key: cc value: 2
// key: bb value: 4
// key: aa value: 3
```

```TypeScript
// When a custom type is inserted, a comparator must be provided.
class TestEntry{
  public id: number = 0;
}

let ts1: TreeMap<TestEntry, string> = new TreeMap<TestEntry, string>((t1: TestEntry, t2: TestEntry): boolean => {
  return t1.id < t2.id;
});
let entry1: TestEntry = {
  id: 0
};
let entry2: TestEntry = {
  id: 1
}
ts1.set(entry1, "0");
ts1.set(entry2, "1");
console.info("length:", ts1.length); // length: 2
```

## entries

```TypeScript
entries(): IterableIterator<[K, V]>
```

Returns a new Iterator object that contains the [key, value] pairs for each element in the Map object in insertion order

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
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The entries method cannot be bound. |

**Examples**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set("squirrel", 123);
treeMap.set("sparrow", 356);
let it = treeMap.entries();
let t: IteratorResult<Object[]> = it.next();
while(!t.done) {
  console.info("TreeMap:", t.value);
  t = it.next()
}
// Output:
// TreeMap: sparrow,356
// TreeMap: squirrel,123
```

```TypeScript
// You are not advised to use the set or remove APIs in entries because they may cause unpredictable risks such as infinite loops. You can use the for loop when inserting or deleting data.
 let treeMap = new TreeMap<string, number>();
 for(let i = 0; i < 10; i++) {
   treeMap.set("sparrow" + i, 123);
 }
 for(let i = 0;i < 10; i++) {
   treeMap.remove("sparrow" + i);
 }
```

## forEach

```TypeScript
forEach(callbackFn: (value?: V, key?: K, map?: TreeMap<K, V>) => void, thisArg?: Object): void
```

Executes the given callback function once for each real key in the map. It does not perform functions on deleted keys

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | (value?: V, key?: K, map?: TreeMap&lt;K, V&gt;) =&gt; void | Yes | callbackFn callbackFn (required) A function that accepts up to three arguments. The function to be called for each element. |
| thisArg | Object | No | thisArg thisArg (Optional) The value to be used as this value for when callbackFn is called. If thisArg is omitted, undefined is used as the this value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The forEach method cannot be bound. |

**Examples**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set("sparrow", 123);
treeMap.set("gull", 357);
treeMap.forEach((value: number, key: string): void => {
  console.info("value: " + value, "key: " + key);
});
// Output:
// value: 357 key: gull
// value: 123 key: sparrow
```

```TypeScript
// You are not advised to use the set or remove APIs in forEach because they may cause unpredictable risks such as infinite loops. You can use the for loop when inserting or deleting data.
 let treeMap = new TreeMap<string, number>();
 for(let i = 0; i < 10; i++) {
   treeMap.set("sparrow" + i, 123);
 }
 for(let i = 0;i < 10; i++) {
   treeMap.remove("sparrow" + i);
 }
```

## get

```TypeScript
get(key: K): V
```

Returns a specified element in a Map object, or undefined if there is no corresponding element

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | The key to look up in the map |

**Return value:**

| Type | Description |
| --- | --- |
| V | value or undefined |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The get method cannot be bound. |

**Examples**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set("squirrel", 123);
treeMap.set("sparrow", 356);
let result = treeMap.get("sparrow");
console.info("result:", result); // result: 356
```

## getFirstKey

```TypeScript
getFirstKey(): K
```

Obtains the first sorted key in the treemap. Or returns undefined if tree map is empty

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| K | value or undefined |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getFirstKey method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-empty-container) | Container is empty.<br>**Applicable version:** 23 and later  **ArkTS mode:** This error code applies only to ArkTS-Sta. |

**Examples**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set("squirrel", 123);
treeMap.set("sparrow", 356);
let result = treeMap.getFirstKey();
console.info("result:", result); // result: sparrow
```

## getHigherKey

```TypeScript
getHigherKey(key: K): K
```

Returns the least element greater than or equal to the specified key if the key does not exist, undefined is returned

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | The key to compare |

**Return value:**

| Type | Description |
| --- | --- |
| K | key or undefined |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getHigherKey method cannot be bound. |

**Examples**

```TypeScript
let treeMap = new TreeMap<number, string>();
treeMap.set(1, 'one');
treeMap.set(2, 'two');
treeMap.set(3, 'three');
treeMap.set(4, 'four');
let result = treeMap.getHigherKey(3);
console.info("result:", result); // result: 4
```

## getLastKey

```TypeScript
getLastKey(): K
```

Obtains the last sorted key in the treemap. Or returns undefined if tree map is empty

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| K | value or undefined |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getLastKey method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-empty-container) | Container is empty.<br>**Applicable version:** 23 and later  **ArkTS mode:** This error code applies only to ArkTS-Sta. |

**Examples**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set("squirrel", 123);
treeMap.set("sparrow", 356);
let result = treeMap.getLastKey();
console.info("result:", result); // result: squirrel
```

## getLowerKey

```TypeScript
getLowerKey(key: K): K
```

Returns the greatest element smaller than or equal to the specified key if the key does not exist, undefined is returned

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | The key to compare |

**Return value:**

| Type | Description |
| --- | --- |
| K | key or undefined |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getLowerKey method cannot be bound. |

**Examples**

```TypeScript
let treeMap = new TreeMap<number, string>();
treeMap.set(1, 'one');
treeMap.set(2, 'two');
treeMap.set(3, 'three');
treeMap.set(4, 'four');
let result = treeMap.getLowerKey(3);
console.info("result:", result); // result: 2
```

## hasKey

```TypeScript
hasKey(key: K): boolean
```

Returns whether a key is contained in this map

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | The key to check if it exists in the map |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The hasKey method cannot be bound. |

**Examples**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set("squirrel", 123);
let result = treeMap.hasKey("squirrel");
console.info("result:", result);  // result: true
```

## hasValue

```TypeScript
hasValue(value: V): boolean
```

Returns whether a value is contained in this map

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | V | Yes | The value to check if it exists in the map |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The hasValue method cannot be bound. |

**Examples**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set("squirrel", 123);
let result = treeMap.hasValue(123);
console.info("result:", result);  // result: true
```

## isEmpty

```TypeScript
isEmpty(): boolean
```

Returns whether the Map object contains elements

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The isEmpty method cannot be bound. |

**Examples**

```TypeScript
let treeMap = new TreeMap<number, number>();
let result = treeMap.isEmpty();
console.info("result:", result);  // result: true
```

## keys

```TypeScript
keys(): IterableIterator<K>
```

Returns a new Iterator object that contains the keys contained in this map

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;K&gt; |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The keys method cannot be bound. |

**Examples**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set("squirrel", 123);
treeMap.set("sparrow", 356);
let keys = treeMap.keys();
for (let key of keys) {
  console.info("key:", key);
}
// Output:
// key: sparrow
// key: squirrel
```

## remove

```TypeScript
remove(key: K): V
```

Remove a specified element from a Map object

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | The key to remove from the map |

**Return value:**

| Type | Description |
| --- | --- |
| V | Target mapped value |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The remove method cannot be bound. |

**Examples**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set("squirrel", 123);
treeMap.set("sparrow", 356);
let result = treeMap.remove("sparrow"); // Delete data.
console.info("result = " + result); // result = 356
```

## replace

```TypeScript
replace(key: K, newValue: V): boolean
```

Replace the old value by new value corresponding to the specified key

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | The key to look up in the map |
| newValue | V | Yes | The new value to set for the key |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean type(Is there a target pointed to by the key) |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The replace method cannot be bound. |

**Examples**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set("sparrow", 123);
let result = treeMap.replace("sparrow", 357);
console.info("sparrow:", treeMap.get("sparrow")); // sparrow: 357
```

## set

```TypeScript
set(key: K, value: V): Object
```

Adds or updates a(new) key-value pair with a key and value specified for the Map object

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | The key to add or update |
| value | V | Yes | The value to add or update |

**Return value:**

| Type | Description |
| --- | --- |
| Object | the map object after set |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The set method cannot be bound. |

**Examples**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set("squirrel", 123);
console.info("squirrel:", treeMap.get("squirrel")); // squirrel: 123
```

## setAll

```TypeScript
setAll(map: TreeMap<K, V>): void
```

Adds all element groups in one map to another map

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| map | [TreeMap](arkts-arkts-util-treemap-treemap-c.md)&lt;K, V&gt; | Yes | map map the Map object to add members |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The setAll method cannot be bound. |

**Examples**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set("squirrel", 123);
treeMap.set("sparrow", 356);
let map : TreeMap<string, number> = new TreeMap();
map.set("demo", 12);
map.setAll(treeMap); // Add all elements in the treeMap to the map.
map.forEach((value ?: number, key ?: string) : void => {
  console.info("value: " + value, "key: " + key); 
})
// Output:
// value: 12 key: demo
// value: 356 key: sparrow
// value: 123 key: squirrel
```

## values

```TypeScript
values(): IterableIterator<V>
```

Returns a new Iterator object that contains the values contained in this map

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;V&gt; |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The values method cannot be bound. |

**Examples**

```TypeScript
let treeMap = new TreeMap<string, number>();
treeMap.set("squirrel", 123);
treeMap.set("sparrow", 356);
let values = treeMap.values();
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

Gets the element number of the TreeMap.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
