# PlainArray

PlainArray stores key-value (KV) pairs. Each key must be unique, be of the number type, and have only one value. PlainArray is based on generics and uses a lightweight structure.

**Since:** 8

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { PlainArray } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<[number, T]>
```

returns an iterator.Each item of the iterator is a Javascript Object

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;[number, T]&gt; |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The Symbol.iterator method cannot be bound. |

**Examples**

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
// You are not advised to use the add, remove, or removeAt APIs in Symbol.iterator because they may cause unpredictable risks such as infinite loops. You can use the for loop when inserting or deleting data.
let plainArray = new PlainArray<string>();
for(let i = 0; i < 10; i++) {
  plainArray.add(i,"123");
}

for(let i = 0; i < 10; i++) {
  plainArray.remove(i);
}
```

## add

```TypeScript
add(key: number, value: T): void
```

Adds an element to this PlainArray.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | number | Yes | Key of the target element. The value must be less than or equal to int32_max, that is, 2147483 647. |
| value | T | Yes | Value of the target element. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The add method cannot be bound. |

**Examples**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
console.info("result:", plainArray.get(1));  // result: squirrel
```

## clear

```TypeScript
clear(): void
```

Clears this PlainArray and sets its length to **0**.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The clear method cannot be bound. |

**Examples**

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

Clones this PlainArray and returns a copy. The modification to the copy does not affect the original instance.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [PlainArray](arkts-arkts-util-plainarray-plainarray-c.md)&lt;T&gt; | New **PlainArray** instance obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The clone method cannot be bound. |

**Examples**

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

A constructor used to create a **PlainArray** instance.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-constructor-calling-failure) | The PlainArray's constructor cannot be directly invoked. |

**Examples**

```TypeScript
let plainArray = new PlainArray<string>();
```

## forEach

```TypeScript
forEach(callbackFn: (value: T, index?: number, PlainArray?: PlainArray<T>) => void, thisArg?: Object): void
```

Uses a callback to traverse each element in the **PlainArray** instance.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | (value: T, index?: number, PlainArray?: PlainArray&lt;T&gt;) =&gt; void | Yes | Callback invoked to traverse the elements in the PlainArray. |
| thisArg | Object | No | Value of **this** to use when **callbackFn** is invoked. The default value is this instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The forEach method cannot be bound. |

**Examples**

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
// You are not advised to use the add, remove, or removeAt APIs in forEach because they may cause unpredictable risks such as infinite loops. You can use the for loop when inserting or deleting data.
let plainArray = new PlainArray<string>();
for(let i = 0; i < 10; i++) {
  plainArray.add(i,"123");
}

for(let i = 0; i < 10; i++) {
  plainArray.remove(i);
}
```

## get

```TypeScript
get(key: number): T
```

Obtains the value of the specified key in this PlainArray.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | number | Yes | Target key. The value must be less than or equal to int32_max, that is, 2147483647. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Value of the key. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The get method cannot be bound. |

**Examples**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.get(1);
console.info("result:", result);  // result: squirrel
```

## getIndexOfKey

```TypeScript
getIndexOfKey(key: number): number
```

Obtains the index of the element with the specified key in this PlainArray.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | number | Yes | Target key. The value must be less than or equal to int32_max, that is, 2147483647. |

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
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.getIndexOfKey(2);
console.info("result = ", result); // result = 1
```

## getIndexOfValue

```TypeScript
getIndexOfValue(value: T): number
```

Obtains the index of the first occurrence of an element with the specified value in this PlainArray.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | T | Yes | Value of the target element. |

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
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.getIndexOfValue("squirrel");
console.info("result:", result);  // result: 0
```

## getKeyAt

```TypeScript
getKeyAt(index: number): number
```

Obtains the key of the element at the specified position in this PlainArray.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Position index of the target element. The value must be less than or equal to int32_max, that is, 2147483647. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Key of the element. If no match is found, **-1** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getKeyAt method cannot be bound. |

**Examples**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.getKeyAt(1);
console.info("result = ", result); // result = 2
```

## getValueAt

```TypeScript
getValueAt(index: number): T
```

Obtains the value of an element at the specified position in this PlainArray.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Position index of the target element. The value must be less than or equal to int32_max, that is, 2147483647. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Value of the element. If no match is found, **undefined** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getValueAt method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |

**Examples**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.getValueAt(1);
console.info("result:", result);  // result: sparrow
```

## has

```TypeScript
has(key: number): boolean
```

Checks whether PlainArray has the specified key.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | number | Yes | Target key. The value must be less than or equal to int32_max, that is, 2147483647. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the specified key is contained; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The has method cannot be bound. |

**Examples**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
let result = plainArray.has(1);
console.info("result = ", result); // result = true
```

## isEmpty

```TypeScript
isEmpty(): boolean
```

Checks whether this PlainArray is empty.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the PlainArray is empty; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The isEmpty method cannot be bound. |

**Examples**

```TypeScript
const plainArray = new PlainArray<string>();
let result = plainArray.isEmpty();
console.info("result = ", result); // result =  true
```

## remove

```TypeScript
remove(key: number): T
```

Removes a key-value pair with the specified key.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | number | Yes | Target key. The value must be less than or equal to int32_max, that is, 2147483647. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Value in the key-value pair removed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The remove method cannot be bound. |

**Examples**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.remove(2);
console.info("result:", result);  // result: sparrow
```

## removeAt

```TypeScript
removeAt(index: number): T
```

Removes an element at the specified position from this PlainArray.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Position index of the target element. The value must be less than or equal to int32_max, that is, 2147483647. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Element removed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The removeAt method cannot be bound. |

**Examples**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.removeAt(1);
console.info("result:", result);  // result: sparrow
```

## removeRangeFrom

```TypeScript
removeRangeFrom(index: number, size: number): number
```

Removes elements within the specified range.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Start position of the elements to remove. The value must be less than or equal to int32_max, that is, 2147483647. |
| size | number | Yes | Number of elements to remove. The value must be less than or equal to int32_max, that is, 214 7483647. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of elements removed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The removeRangeFrom method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |

**Examples**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.removeRangeFrom(1, 3);
console.info("result:", result);  // result: 1
```

## setValueAt

```TypeScript
setValueAt(index: number, value: T): void
```

Sets a value for an element at the specified position in this PlainArray.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Position index of the target element. The value must be less than or equal to int32_max, that is, 2147483647. |
| value | T | Yes | Value of the target element. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The setValueAt method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |

**Examples**

```TypeScript
let plainArray = new PlainArray<string | number>();
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

Obtains a string that contains all elements in this PlainArray.

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

Number of elements in a PlainArray.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
