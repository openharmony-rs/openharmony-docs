# @ohos.util.HashMap (Nonlinear Container HashMap)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong; @lijin1039-->
<!--Designer: @Malzahar; @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=fa87684a3d68d73092de76cbd3803fc3d90b97e4 translatedAt=2026-11-16T05:31:45.791Z pushedAt=2026-11-16T06:31:14.192Z nl=1 -->

HashMap is implemented based on arrays, linked lists, and red-black trees, supporting efficient query, insertion, and deletion. HashMap stores content based on key-value pair mapping. Duplicate keys are not allowed, and one key can correspond to only one value.

Compared with [TreeMap](js-apis-treemap.md), HashMap accesses data based on the hashCode of keys, which is faster but does not guarantee the ordering of keys. TreeMap, in contrast, stores and accesses data in an ordered manner, with lower query efficiency.

[HashSet](js-apis-hashset.md) is implemented based on HashMap. The input parameters of HashMap consist of two values: key and value. In HashSet, only the value object is stored and managed.

**Recommended use cases:** When fast access, deletion, and insertion of key-value pair data are required, HashMap is recommended. Typical application scenarios include data caching, key-value lookup tables, and configuration parameter management.

The document uses generics, including the following generic parameters:<br>
- K: Key<br>
- V: Value

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> Container classes, implemented in static languages, have restrictions on storage locations and properties, and do not support custom properties or methods.


## Modules to Import

```ts
import { HashMap } from '@kit.ArkTS';
```

## HashMap

### Properties

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| length | number | Yes| No| Number of elements in a HashMap.|


### constructor

constructor()

Creates a HashMap instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200012 | The HashMap's constructor cannot be directly invoked. |

**Example**

```ts
let hashMap = new HashMap<string, number>();
```


### isEmpty

isEmpty(): boolean

Checks whether this HashMap is empty (contains no element).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Check result. The value **true** is returned if the HashMap is empty; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The isEmpty method cannot be bound. |

**Example**

```ts
let hashMap = new HashMap<string, number>();
let result = hashMap.isEmpty();
console.info("result:", result);  // result: true
```


### hasKey

hasKey(key: K): boolean

Checks whether this HashMap has the specified key.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| key | K | Yes | Specifies the key to query, used to determine whether the HashMap contains the key. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns true if the specified key is contained; returns false if the specified key is not contained. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The hasKey method cannot be bound. |

**Example**

```ts
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
let result = hashMap.hasKey("squirrel");
console.info("result:", result);  // result: true
```


### hasValue

hasValue(value: V): boolean

Checks whether this HashMap has the specified value.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | V | Yes | Specifies the value to query, used to determine whether the HashMap contains this value. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns true if the specified value is contained; returns false otherwise. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The hasValue method cannot be bound. |

**Example**

```ts
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
let result = hashMap.hasValue(123);
console.info("result:", result);  // result: true
```


### get

get(key: K): V

Obtains the value of the specified key in this HashMap. If nothing is obtained, **undefined** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| key | K | Yes | Specifies the key whose corresponding value is to be obtained. |

**Return value**

| Type| Description|
| -------- | -------- |
| V | Returns the value mapped by key; returns undefined when the key does not exist. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The get method cannot be bound. |

**Example**

```ts
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
hashMap.set("sparrow", 356);
let result = hashMap.get("sparrow");
console.info("result:", result);  // result: 356
```


### setAll

setAll(map: HashMap<K, V>): void

Sets all elements in the specified HashMap to the current HashMap. If the current HashMap already contains the same key, the corresponding value will be overwritten.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| map | HashMap<K, V> | Yes | Source HashMap object whose all elements need to be added to the current HashMap. If map and the current HashMap have duplicate keys, the value in map will replace the value of the corresponding key in the current HashMap. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The setAll method cannot be bound. |

**Example**

```ts
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
hashMap.set("sparrow", 356);
let newHashMap = new HashMap<string, number>();
newHashMap.set("newMap", 99);
hashMap.setAll(newHashMap);
let result = hashMap.hasKey("newMap");
console.info("result:", result);  // result: true
```


### set

set(key: K, value: V): Object

Adds or updates a key-value pair in the HashMap. If the key does not exist, a new key-value pair is added; if the key already exists, its corresponding value is updated.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| key | K | Yes | Key name to add or update. If the key already exists, the corresponding value will be replaced. |
| value | V | Yes | Value to add or update. |

**Return value**

| Type| Description|
| -------- | -------- |
| Object | Returns the current HashMap instance containing the elements after addition or update. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The set method cannot be bound. |

**Example**

```ts
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
console.info("result:", hashMap.get("squirrel"));  // result: 123
```


### remove

remove(key: K): V

Deletes the element corresponding to the specified key and returns the value of that element. If the key does not exist, undefined is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| key | K | Yes | Specifies the key of the element to be removed, used to locate and remove the key-value pair corresponding to this key in the HashMap. |

**Return value**

| Type| Description|
| -------- | -------- |
| V | Returns the value of the deleted element; returns undefined when key does not exist. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The remove method cannot be bound. |

**Example**

```ts
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
hashMap.set("sparrow", 356);
let result = hashMap.remove("sparrow");
console.info("result:", result);  // result: 356
```


### clear

clear(): void

Clears this HashMap and sets its length to **0**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The clear method cannot be bound. |

**Example**

```ts
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
hashMap.set("sparrow", 356);
hashMap.clear();
let result = hashMap.isEmpty();
console.info("result:", result);  // result: true
```


### keys

keys(): IterableIterator&lt;K&gt;

Returns a new iterator object that contains all the keys in this HashMap.

> **Note:**
>
> It is not recommended to use the set and remove methods during keys iteration, because it may cause abnormal state during the iteration process. It is recommended to use a for loop to perform safe insertion and deletion operations.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;K&gt; | Returns an iterator containing all keys in this HashMap. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The keys method cannot be bound. |

**Example**

```ts
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


### values

values(): IterableIterator&lt;V&gt;

Returns a new iterator object that contains all the values corresponding to the keys in this HashMap.

> **Note:**
>
> It is not recommended to use the set and remove methods during values iteration, because it may cause abnormal state during the iteration process. It is recommended to use a for loop to perform safe insertion and deletion operations.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;V&gt; | Returns an iterator containing all values in this HashMap. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The values method cannot be bound. |

**Example**

```ts
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
hashMap.set("sparrow", 356);
let values = hashMap.values();
for (let value of values) {
  console.info("value:", value);
}
// value: 123
// value: 356
```


### replace

replace(key: K, newValue: V): boolean

Replaces the value corresponding to the specified key. The replacement is performed and true is returned only when the specified key already exists. If the key does not exist, the HashMap is not modified and false is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| key | K | Yes | Specifies the element to be replaced based on the key. The replacement takes effect only when the key already exists. |
| newValue | V | Yes | New value that replaces the value corresponding to the specified key. The newValue replaces the original value only when the specified key already exists; if the key does not exist, this value is not set. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Operation result. The value **true** is returned if the element is replaced; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The replace method cannot be bound. |

**Example**

```ts
let hashMap = new HashMap<string, number>();
hashMap.set("sparrow", 123);
let result = hashMap.replace("sparrow", 357);
console.info("result:", result);  // result: true
```


### forEach

forEach(callbackFn: (value?: V, key?: K, map?: HashMap<K, V>) => void, thisArg?: Object): void

Uses a callback to traverse each element.

> **Note:**
>
> It is not recommended to use the set and remove methods during forEach traversal, because it may cause abnormal state during the iteration process. If you need to insert or delete elements during traversal, it is recommended to use a for loop to perform safe insertion and deletion operations.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callbackFn | function | Yes | Callback function, invoked when traversing each element, used to perform custom operations on the element. |
| thisArg | Object | No | Used as the this value when callbackFn is invoked. When you need to access properties or methods of other objects in the callback function, you can pass a custom thisArg. If not passed, the default value is the current instance object. |

callbackFn parameters
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | V | No| Value of the element that is currently traversed.|
| key | K | No| Key of the element that is currently traversed.|
| map | HashMap<K, V> | No | The current HashMap instance object on which the forEach method is called. The default value is the current instance object. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The forEach method cannot be bound. |

**Example**

```ts
let hashMap = new HashMap<string, number>();
hashMap.set("sparrow", 123);
hashMap.set("gull", 357);
hashMap.forEach((value: number, key: string) => {
  console.info("value: " + value, "key: " + key);
});
// value: 123 key: sparrow
// value: 357 key: gull
```

```ts
// It is not recommended to use set and remove methods in forEach, because it may cause abnormal state during iteration. It is recommended to use a for loop to perform safe insertion and deletion operations.
let hashMap = new HashMap<string, number>();
for (let i = 0; i < 10; i++) {
  hashMap.set("sparrow" + i, 123);
}

for (let i = 0; i < 10; i++) {
  hashMap.remove("sparrow" + i);
}
```

### entries

entries(): IterableIterator&lt;[K, V]&gt;

Returns a new iterator object that contains the key-value pairs in this HashMap.

> **Note:**
>
> It is not recommended to use the set and remove methods during entries iteration, because it may cause abnormal state during the iteration process. If you need to insert or delete elements during traversal, it is recommended to use a for loop to perform safe insertion and deletion operations.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;[K, V]&gt; | Returns an iterator containing all key-value pairs in this HashMap. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The entries method cannot be bound. |

**Example**

```ts
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
hashMap.set("sparrow", 356);
let iter = hashMap.entries();
let temp: IteratorResult<Object[]> = iter.next();
while (!temp.done) {
  console.info("key:" + temp.value[0]);
  console.info("value:" + temp.value[1]);
  temp = iter.next();
}
```
```ts
// It is not recommended to use the set and remove methods in entries, because it may cause abnormal state during iteration. It is recommended to use a for loop to perform safe insertion and deletion operations.
let hashMap = new HashMap<string, number>();
for (let i = 0; i < 10; i++) {
  hashMap.set("sparrow" + i, 123);
}

for (let i = 0; i < 10; i++) {
  hashMap.remove("sparrow" + i);
}
```
### [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;[K, V]&gt;

Returns an iterator, each item of which is an array [K, V] containing a key and a value.

> **Note:**
>
> It is not recommended to use the set and remove methods during Symbol.iterator iteration, because it may cause abnormal state during the iteration process. If you need to insert or delete elements during traversal, it is recommended to use a for loop to perform safe insertion and deletion operations.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;[K, V]&gt; | Returns an iterator containing all key-value pairs in this HashMap. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**Example**
```ts
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
while (!temp.done) {
  console.info("key:", temp.value[0]);
  console.info("value:", temp.value[1]);
  temp = iter.next();
}
// key: squirrel
// value: 123
// key: sparrow
// value: 356
```

```ts
// It is not recommended to use the set and remove methods in Symbol.iterator, because it may cause abnormal state during iteration. It is recommended to use a for loop to perform safe insertion and deletion operations.
let hashMap = new HashMap<string, number>();
for (let i = 0; i < 10; i++) {
  hashMap.set("sparrow" + i, 123);
}

for (let i = 0; i < 10; i++) {
  hashMap.remove("sparrow" + i);
}
```