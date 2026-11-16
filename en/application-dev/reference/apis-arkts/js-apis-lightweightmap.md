# @ohos.util.LightWeightMap (Nonlinear Container LightWeightMap)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong; @lijin1039-->
<!--Designer: @Malzahar; @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=31ba07988632b6f2ed98a078bdae886436926502 translatedAt=2026-11-16T05:36:47.009Z pushedAt=2026-11-16T06:31:14.235Z nl=1 -->

LightWeightMap can be used to store key-value pairs with an association relationship, where the key is unique and each key corresponds to one value.

LightWeightMap is defined based on generics and uses a lightweight structure. The default capacity is 8, and each capacity expansion doubles the original capacity.

The lookup of keys in the collection relies on a hash algorithm. Hash values are stored in an array and then mapped to the corresponding keys and values.

Both LightWeightMap and [HashMap](js-apis-hashmap.md) are containers used to store key-value pairs, but LightWeightMap occupies less memory.

**Recommended use cases:** When you need to store and access key-value pairs and are sensitive to memory usage (for example, when you need to maintain a large number of small key-value pair collections simultaneously or run in a memory-constrained environment), it is recommended to use LightWeightMap, which occupies less memory.

This topic uses the following to identify the use of generics:
- K: Key<br>
- V: Value

> **NOTE**
>
> - The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - Container classes, implemented in static languages, have restrictions on storage locations and properties, and do not support custom properties or methods.

## Specifications

When the key stored in LightWeightMap is of the number type and its value is greater than INT32_MAX (that is, 2147483647) or less than INT32_MIN (that is, -2147483648), the result of operations on LightWeightMap may be inconsistent with expectations.

This is because the storage structure changes in such cases.

For example, in the calculation of the key in the following example, 1758783600000 is greater than INT32_MAX, so it is stored as TaggedDouble; 1758783600 is less than INT32_MAX and greater than INT32_MIN, so it is stored as TaggedInt. Due to the difference in the storage methods above, different hash values are calculated when the hash algorithm is applied, which leads to different mapping results and produces a phenomenon inconsistent with expectations.

```ts
let lightWeightMap = new LightWeightMap<number, number>();
let key = 1758783600000 / 1000;  // 1758783600000 > INT32_MAX
lightWeightMap.set(key, 1001);
console.info('result:', lightWeightMap.hasKey(1758783600));  // result: false 
console.info('result:', lightWeightMap.hasKey(key));  // result: true
```

## Modules to Import

```ts
import { LightWeightMap } from '@kit.ArkTS';
```

## LightWeightMap

### Properties

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| length | number | Yes| No| Number of elements in a LightWeightMap.|


### constructor

constructor()

The constructor of LightWeightMap creates an empty LightWeightMap instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang


**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200012 | The LightWeightMap's constructor cannot be directly invoked. |

**Example**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
```


### isEmpty

isEmpty(): boolean

Checks whether this LightWeightMap is empty (contains no element).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Check result. The value **true** is returned if the LightWeightMap is empty; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The isEmpty method cannot be bound. |

**Example**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
let result = lightWeightMap.isEmpty();
console.info("result:", result);  // result: true
```


### hasAll

hasAll(map: LightWeightMap<K, V>): boolean

Checks whether this LightWeightMap contains all elements of the specified **LightWeightMap** instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| map | [LightWeightMap<K, V>](#lightweightmap) | Yes | LightWeightMap object used for comparison, determining whether the current instance contains all elements in this map. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Check result. The value **true** is returned if all the elements in the specified LightWeightMap are contained; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The hasAll method cannot be bound. |

**Example**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let targetMap = new LightWeightMap<string, number>();
targetMap.set("sparrow", 356);
let result = lightWeightMap.hasAll(targetMap); 
console.info("result = ", result); // result = true
```


### hasKey

hasKey(key: K): boolean

Determines whether LightWeightMap contains the specified key. When the key is of the number type and its value is greater than INT32_MAX or less than INT32_MIN, the result may be inconsistent with expectations. For details, see [Specifications](#specifications).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| key | K | Yes | Specified key. When key is of the number type and its value is greater than INT32_MAX or less than INT32_MIN, the result may be inconsistent with expectations. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Check result. The value **true** is returned if the specified key is contained; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The hasKey method cannot be bound. |

**Example**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
let result = lightWeightMap.hasKey("squirrel");
console.info("result:", result);  // result: true
```


### hasValue

hasValue(value: V): boolean

Checks whether this LightWeightMap has the specified value.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | V | Yes | Value to determine whether it is contained. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Operation result. The value **true** is returned if the specified value is contained; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The hasValue method cannot be bound. |

**Example**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
let result = lightWeightMap.hasValue(123);
console.info("result:", result);  // result: true
```

### increaseCapacityTo

increaseCapacityTo(minimumCapacity: number): void

Expands the capacity of the current LightWeightMap to the specified capacity. If the passed capacity value is greater than or equal to the number of elements in the current LightWeightMap, the capacity is expanded to the new capacity; if it is less, no change is made.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| minimumCapacity | number | Yes | Number of elements to be accommodated. The value must be greater than or equal to 0. Capacity expansion takes effect when the value is greater than or equal to the current number of elements; otherwise, the capacity remains unchanged. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The increaseCapacityTo method cannot be bound. |

**Example**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.increaseCapacityTo(10);
```

### get

get(key: K): V

Obtains the value corresponding to the specified key. When the key is of the number type and its value is greater than INT32_MAX or less than INT32_MIN, the result may be inconsistent with expectations.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| key | K | Yes| Target key.|

**Return value**

| Type| Description|
| -------- | -------- |
| V | Value of the key.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The get method cannot be bound. |

**Example**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.get("sparrow");
console.info("result:", result);  // result: 356
```


### getIndexOfKey

getIndexOfKey(key: K): number

Finds the index of the first occurrence of the key element. If not found, -1 is returned. When the key is of the number type and its value is greater than INT32_MAX or less than INT32_MIN, the result may be inconsistent with expectations.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| key | K | Yes| Key of the element.|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Index of the element. If no match is found, **-1** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The getIndexOfKey method cannot be bound. |

**Example**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getIndexOfKey("sparrow");
console.info("result:", result);  // result: 0
```


### getIndexOfValue

getIndexOfValue(value: V): number

Finds the index of the first occurrence of the specified value element. If not found, -1 is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | V | Yes | Value whose first occurrence index is to be found. |

**Return value**

| Type| Description|
| -------- | -------- |
| number | Index of the element. If no match is found, **-1** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The getIndexOfValue method cannot be bound. |

**Example**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getIndexOfValue(123);
console.info("result:", result);  // result: 1
```


### getKeyAt

getKeyAt(index: number): K

Obtains the key of an element at the specified position in this LightWeightMap.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| index | number | Yes | The index to look up. Must be less than or equal to INT32_MAX, that is, 2147483647. |

**Return value**

| Type| Description|
| -------- | -------- |
| K | Returns the key in the key-value pair of the element corresponding to the index. If not found, returns undefined. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of index is out of range. |
| 10200011 | The getKeyAt method cannot be bound. |

**Example**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getKeyAt(1);
console.info("result:", result);  // result: squirrel
```


### setAll

setAll(map: LightWeightMap<K, V>): void

Adds all elements in one LightWeightMap to another LightWeightMap. If the target LightWeightMap already contains the same key, its corresponding value is updated.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| map | [LightWeightMap<K, V>](#lightweightmap) | Yes | LightWeightMap that provides elements to add. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The setAll method cannot be bound. |

**Example**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let map = new LightWeightMap<string, number>();
map.setAll(lightWeightMap);   // Add all elements in lightWeightMap to the map.
let result = map.get("sparrow");
console.info("result:", result);  // result: 356
```


### set
set(key: K, value: V): Object

Adds or updates a set of data in the LightWeightMap. After a successful call, if the key does not exist, a new key-value pair is added and length increases; if the key already exists, the corresponding value is updated.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| key | K | Yes | Key name for adding or updating member data. When key is of the number type and its value is greater than INT32_MAX or less than INT32_MIN, the result may be inconsistent with expectations. |
| value | V | Yes| Value of the target element.|

**Return value**

| Type| Description|
| -------- | -------- |
| Object | Returns the LightWeightMap instance object after addition or update.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The set method cannot be bound. |

**Example**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
let result = lightWeightMap.set("squirrel", 123);
console.info("result:", result);  // result: squirrel:123
```


### remove

remove(key: K): V

Deletes the element mapped by the specified key. When the key is of the number type and its value is greater than INT32_MAX or less than INT32_MIN, the result may be inconsistent with expectations.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| key | K | Yes| Target key.|

**Return value**

| Type| Description|
| -------- | -------- |
| V | Value of the element removed.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The remove method cannot be bound. |

**Example**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.remove("sparrow");
console.info("result:", result);  // result: 356
```


### removeAt

removeAt(index: number): boolean

Deletes the element corresponding to the specified index. After a successful call, if the index is valid, the key-value pair at that position is removed from the LightWeightMap and length decreases.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| index | number | Yes | Index position of the element to remove. Value range: [0, length-1], must be less than or equal to INT32_MAX, that is, 2147483647. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Operation result. The value **true** is returned if the element is removed; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The removeAt method cannot be bound. |

**Example**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.removeAt(1);
console.info("result:", result);  // result: true
```


### setValueAt

setValueAt(index: number, newValue: V): boolean

Replaces the value in the key-value pair corresponding to the specified index. After a successful call, the value of the key-value pair at the specified index is replaced with newValue.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| index | number | Yes | Specified index. Must be less than or equal to INT32_MAX, that is, 2147483647. |
| newValue | V | Yes| Value of the target element to set.|

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Operation result. The value **true** is returned if the value is set successfully; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of index is out of range. |
| 10200011 | The setValueAt method cannot be bound. |

**Example**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
lightWeightMap.setValueAt(1, 3546);
console.info("result:", lightWeightMap.get("squirrel"));  // result: 3546
```


### getValueAt

getValueAt(index: number): V

Obtains the value of an element at the specified position in this LightWeightMap.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| index | number | Yes | Specified index. Must be less than or equal to INT32_MAX, that is, 2147483647. |

**Return value**

| Type| Description|
| -------- | -------- |
| V | Value obtained.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of index is out of range. |
| 10200011 | The getValueAt method cannot be bound. |

**Example**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getValueAt(1);
console.info("result:", result);  // result: 123
```


### clear

clear(): void

Clears this LightWeightMap and sets its length to **0**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The clear method cannot be bound. |

**Example**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
lightWeightMap.clear();
let result = lightWeightMap.isEmpty();
console.info("result:", result);  // result: true
```


### keys

keys(): IterableIterator&lt;K&gt;

Returns an iterator that contains all the keys in this LightWeightMap.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;K&gt; | Iterator obtained.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The keys method cannot be bound. |

**Example**

```ts
// It is not recommended to use set, setValueAt, remove, or removeAt in keys, which may cause risks such as infinite loops that are unpredictable. Use a for loop for insertion and deletion.
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


### values

values(): IterableIterator&lt;V&gt;

Returns a new iterator object containing all values in this map.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;V&gt; | Iterator obtained.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The values method cannot be bound. |

**Example**

```ts
// It is not recommended to use set, setValueAt, remove, or removeAt in values, as this may cause risks such as infinite loops that are unpredictable. Use a for loop for insertion and deletion.
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


### forEach

forEach(callbackFn: (value?: V, key?: K, map?: LightWeightMap<K, V>) => void, thisArg?: Object): void

Traverses the elements and their key-value pair information on the instance object through a callback function.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callbackFn | function | Yes | Callback function used to traverse the elements and indexes in the LightWeightMap instance. |
| thisArg | Object | No | Used as the this value when callbackFn is called. Pass this parameter when the this in the callback function needs to point to an object other than the current instance; omit it when the this reference does not need to be changed. When omitted, the default value is the current instance object. |

callbackFn parameters
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | V | No | Value of the element that is currently traversed. |
| key | K | No | Key of the element that is currently traversed. |
| map | [LightWeightMap<K, V>](#lightweightmap) | No | Instance object that currently calls the forEach method. Default value is the current instance object. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The forEach method cannot be bound. |

**Example**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("sparrow", 123);
lightWeightMap.set("gull", 357);
lightWeightMap.forEach((value: number, key: string) => {
  console.info("value:" + value, "key:" + key);
});
// value:123 key:sparrow
// value:357 key:gull
```

```ts
// You are not advised to use the set, setValueAt, remove, or removeAt APIs in forEach because they may cause unpredictable risks such as infinite loops. You can use the for loop when inserting or deleting data.
let lightWeightMap = new LightWeightMap<string, number>();
for (let i = 0; i < 10; i++) {
  lightWeightMap.set("sparrow" + i, 123);
}
for (let i = 0; i < 10; i++) {
  lightWeightMap.remove("sparrow" + i);
}
```

### entries

entries(): IterableIterator<[K, V]>

Returns an iterator that contains all the elements in this LightWeightMap.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator<[K, V]> | Returns an iterator object containing all key-value pairs in this map. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The entries method cannot be bound. |

**Example**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let iteratorResult = lightWeightMap.entries();
let temp: IteratorResult<Object[]> = iteratorResult.next();
while (!temp.done) {
  console.info("key:" + temp.value[0]);
  console.info("value:" + temp.value[1]);
  temp = iteratorResult.next();
}
```
```ts
// You are not advised to use the set, setValueAt, remove, or removeAt APIs in entries because they may cause unpredictable risks such as infinite loops. You can use the for loop when inserting or deleting data.
let lightWeightMap = new LightWeightMap<string, number>();
for(let i = 0; i < 10; i++) {
  lightWeightMap.set("sparrow" + i, 123);
}
for(let i = 0; i < 10; i++) {
  lightWeightMap.remove("sparrow" + i);
}
```

### toString

toString(): String

Concatenates the elements in this LightWeightMap into a string and returns the string.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| String | Returns a string formed by concatenating the key-value pairs in this map. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The toString method cannot be bound. |

**Example**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.toString();
console.info("result:", result);  // result: sparrow:356,squirrel:123
```

### [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;[K, V]&gt;

Returns an iterator, where each item is a [K, V] array containing a key and a value.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator<[K, V]> | Iterator obtained.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**Example**

```ts
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

```ts
// You are not advised to use the set, setValueAt, remove, or removeAt APIs in Symbol.iterator because they may cause unpredictable risks such as infinite loops. You can use the for loop when inserting or deleting data.
let lightWeightMap = new LightWeightMap<string, number>();
for(let i = 0; i < 10; i++) {
  lightWeightMap.set("sparrow" + i, 123);
}
for(let i = 0; i < 10; i++) {
  lightWeightMap.remove("sparrow" + i);
}
```