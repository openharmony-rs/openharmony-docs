# HashMap

HashMap is a map implemented based on the array, linked list, and red-black tree. It provides efficient data query, insertion, and removal. The elements in a HashMap instance are mappings of key-value pairs. Each key must be unique and have only one value.

**Since:** 8

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { HashMap } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<[K, V]>
```

Obtains an iterator, each item of which is a JavaScript object.

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
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
hashMap.set("sparrow", 356);

// Method 1:
for (let item of hashMap) {
  console.info("key:", item[0]);
  console.info("value:", item[1]);
}
// key: squirrel
// value: 123
// key: sparrow
// value: 356

// Method 2:
let iter = hashMap[Symbol.iterator]();
let temp: IteratorResult<Object[]> = iter.next();
while(!temp.done) {
  console.info("key:", temp.value[0]);
  console.info("value:", temp.value[1]);
  temp = iter.next();
}
// key: squirrel
// value: 123
// key: sparrow
// value: 356
```

```TypeScript
// You are not advised to use the set or remove APIs in Symbol.iterator because they may cause unpredictable risks such as infinite loops. You can use the for loop when inserting or deleting data.
let hashMap = new HashMap<string, number>();
for(let i = 0; i < 10; i++) {
  hashMap.set("sparrow" + i, 123);
}

for(let i = 0; i < 10; i++) {
  hashMap.remove("sparrow" + i);
}
```

## clear

```TypeScript
clear(): void
```

Clears this HashMap and sets its length to **0**.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The clear method cannot be bound. |

**Examples**

```TypeScript
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
hashMap.set("sparrow", 356);
hashMap.clear();
let result = hashMap.isEmpty();
console.info("result:", result);  // result: true
```

## constructor

```TypeScript
constructor()
```

A constructor used to create a **HashMap** instance.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-constructor-calling-failure) | The HashMap's constructor cannot be directly invoked. |

**Examples**

```TypeScript
let hashMap = new HashMap<string, number>();
```

## entries

```TypeScript
entries(): IterableIterator<[K, V]>
```

Returns an iterator that contains all the elements in this HashMap.

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
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
hashMap.set("sparrow", 356);
let iter = hashMap.entries();
let temp: IteratorResult<Object[]> = iter.next();
while(!temp.done) {
  console.info("key:" + temp.value[0]);
  console.info("value:" + temp.value[1]);
  temp = iter.next();
}
```

```TypeScript
// You are not advised to use the set or remove APIs in entries because they may cause unpredictable risks such as infinite loops. You can use the for loop when inserting or deleting data.
let hashMap = new HashMap<string, number>();
for(let i = 0; i < 10; i++) {
  hashMap.set("sparrow" + i, 123);
}

for(let i = 0; i < 10; i++) {
  hashMap.remove("sparrow" + i);
}
```

## forEach

```TypeScript
forEach(callbackFn: (value?: V, key?: K, map?: HashMap<K, V>) => void, thisArg?: Object): void
```

Uses a callback to traverse each element.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | (value?: V, key?: K, map?: HashMap&lt;K, V&gt;) =&gt; void | Yes | Callback invoked to traverse the elements in the HashMap. |
| thisArg | Object | No | Value of **this** to use when **callbackFn** is invoked. The default value is this instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The forEach method cannot be bound. |

**Examples**

```TypeScript
let hashMap = new HashMap<string, number>();
hashMap.set("sparrow", 123);
hashMap.set("gull", 357);
hashMap.forEach((value: number, key: string) => {
  console.info("value: " + value, "key: " + key);
});
// value: 123 key: sparrow
// value: 357 key: gull
```

```TypeScript
// You are not advised to use the set or remove APIs in forEach because they may cause unpredictable risks such as infinite loops. You can use the for loop when inserting or deleting data.
let hashMap = new HashMap<string, number>();
for(let i = 0; i < 10; i++) {
  hashMap.set("sparrow" + i, 123);
}

for(let i = 0; i < 10; i++) {
  hashMap.remove("sparrow" + i);
}
```

## get

```TypeScript
get(key: K): V
```

Obtains the value of the specified key in this HashMap. If nothing is obtained, **undefined** is returned.

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
| V | Value obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The get method cannot be bound. |

**Examples**

```TypeScript
const hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
hashMap.set("sparrow", 356);
let result = hashMap.get("sparrow");
console.info("result:", result);  // result: 356
```

## hasKey

```TypeScript
hasKey(key: K): boolean
```

Checks whether this HashMap has the specified key.

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
const hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
let result = hashMap.hasKey("squirrel");
console.info("result:", result);  // result: true
```

## hasValue

```TypeScript
hasValue(value: V): boolean
```

Checks whether this HashMap has the specified value.

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
| boolean | Check result. The value **true** is returned if the specified value is contained; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The hasValue method cannot be bound. |

**Examples**

```TypeScript
const hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
let result = hashMap.hasValue(123);
console.info("result:", result);  // result: true
```

## isEmpty

```TypeScript
isEmpty(): boolean
```

Checks whether this HashMap is empty (contains no element).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the HashMap is empty; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The isEmpty method cannot be bound. |

**Examples**

```TypeScript
const hashMap = new HashMap<string, number>();
let result = hashMap.isEmpty();
console.info("result = ", result) // result = true
```

## keys

```TypeScript
keys(): IterableIterator<K>
```

Returns an iterator that contains all the keys in this HashMap.

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
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
hashMap.set("sparrow", 356);
let keys = hashMap.keys();
for (let key of keys) {
  console.info("key:" + key);
}
// key:squirrel
// key:sparrow
```

## remove

```TypeScript
remove(key: K): V
```

Removes an element with the specified key from this HashMap.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | Key of the target element. |

**Return value:**

| Type | Description |
| --- | --- |
| V | Value of the element. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The remove method cannot be bound. |

**Examples**

```TypeScript
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
hashMap.set("sparrow", 356);
let result = hashMap.remove("sparrow");
console.info("result:", result);  // result: 356
```

## replace

```TypeScript
replace(key: K, newValue: V): boolean
```

Replaces the value of a specified key.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | Key of the target element. |
| newValue | V | Yes | New value of the element. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Operation result. The value **true** is returned if the element is replaced; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The replace method cannot be bound. |

**Examples**

```TypeScript
let hashMap = new HashMap<string, number>();
hashMap.set("sparrow", 123);
let result = hashMap.replace("sparrow", 357);
console.info("result:", result);  // result: true
```

## set

```TypeScript
set(key: K, value: V): Object
```

Adds or updates an element in this HashMap.

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
| Object | HashMap that contains the new element. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The set method cannot be bound. |

**Examples**

```TypeScript
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123)
console.info("result:", hashMap.get("squirrel"));  // result: 123
```

## setAll

```TypeScript
setAll(map: HashMap<K, V>): void
```

Adds all elements in a **HashMap** instance to this HashMap.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| map | [HashMap](arkts-arkts-util-hashmap-hashmap-c.md)&lt;K, V&gt; | Yes | **HashMap** instance whose elements are to be added to the current HashMap. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The setAll method cannot be bound. |

**Examples**

```TypeScript
const hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
hashMap.set("sparrow", 356);
let newHashMap = new HashMap<string, number>();
newHashMap.set("newMap", 99);
hashMap.setAll(newHashMap);
let result = hashMap.hasKey("newMap");
console.info("result:", result);  // result: true
```

## values

```TypeScript
values(): IterableIterator<V>
```

Returns an iterator that contains all the values in this HashMap.

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
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
hashMap.set("sparrow", 356);
let values = hashMap.values();
for (let value of values) {
  console.info("value:", value)
}
// value: 123
// value: 356
```

## length

```TypeScript
length: number
```

Number of elements in a HashMap.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
