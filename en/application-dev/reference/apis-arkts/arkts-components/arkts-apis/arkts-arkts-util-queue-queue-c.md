# Queue

Queue follows the principle of First In First Out (FIFO). It supports insertion of elements at the end and removal from the front of the queue. Queue is implemented based on the queue data structure.

**Since:** 8

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { Queue } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<T>
```

returns an iterator.Each item of the iterator is a Javascript Object

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;T&gt; |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The Symbol.iterator method cannot be bound. |

**Examples**

```TypeScript
let queue = new Queue<number>();
queue.add(2);
queue.add(4);
queue.add(5);
queue.add(4);

// Method 1:
for (let value of queue) {
  console.info("value:", value);
}
// value: 2
// value: 4
// value: 5
// value: 4

// Method 2:
let iter = queue[Symbol.iterator]();
let temp: IteratorResult<number> = iter.next().value;
while(temp != undefined) {
  console.info("value: " + temp);
  temp = iter.next().value;
}
// value: 2
// value: 4
// value: 5
// value: 4
```

## add

```TypeScript
add(element: T): boolean
```

Adds an element at the end of this Queue.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| element | T | Yes | Target element. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Operation result. The value **true** is returned if the element is added; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The add method cannot be bound. |

**Examples**

```TypeScript
class C1 {
  name: string = ""
  age: string = ""
}
let queue = new Queue<number | string | C1 | number[]>();
let result = queue.add("a");
let result1 = queue.add(1);
let b = [1, 2, 3];
let result2 = queue.add(b);
let c : C1 = {name : "Dylan", age : "13"};
let result3 = queue.add(c);
console.info("result:", queue.length);  // result: 4
```

## constructor

```TypeScript
constructor()
```

A constructor used to create a **Queue** instance.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-constructor-calling-failure) | The Queue's constructor cannot be directly invoked. |

**Examples**

```TypeScript
let queue = new Queue<number | string | Object>();
```

## forEach

```TypeScript
forEach(callbackFn: (value: T, index?: number, Queue?: Queue<T>) => void, thisArg?: Object): void
```

Uses a callback to traverse each element in the **Queue** instance.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | (value: T, index?: number, Queue?: Queue&lt;T&gt;) =&gt; void | Yes | Callback invoked to traverse the elements in the Queue. |
| thisArg | Object | No | Value of **this** to use when **callbackFn** is invoked. The default value is this instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The forEach method cannot be bound. |

**Examples**

```TypeScript
let queue = new Queue<number>();
queue.add(2);
queue.add(4);
queue.add(5);
queue.add(4);
queue.forEach((value: number, index: number): void => {
  console.info("value:" + value, "index:" + index);
});
// value:2 index:0
// value:4 index:1
// value:5 index:2
// value:4 index:3
```

## getFirst

```TypeScript
getFirst(): T
```

Obtains the first element of this Queue.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| T | The first element obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getFirst method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-empty-container) | Container is empty.<br>**Applicable version:** 23 and later  **ArkTS mode:** This error code applies only to ArkTS-Sta. |

**Examples**

```TypeScript
let queue = new Queue<number>();
queue.add(2);
queue.add(4);
queue.add(5);
queue.add(2);
let result = queue.getFirst();
console.info("result:", result);  // result: 2
```

## pop

```TypeScript
pop(): T
```

Removes the first element from this Queue.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| T | Element removed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The pop method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-empty-container) | Container is empty.<br>**Applicable version:** 23 and later  **ArkTS mode:** This error code applies only to ArkTS-Sta. |

**Examples**

```TypeScript
let queue = new Queue<number>();
queue.add(2);
queue.add(4);
queue.add(5);
queue.add(2);
queue.add(4);
let result = queue.pop();
console.info("result:", result);  // result: 2
```

## length

```TypeScript
length: number
```

Number of elements in a Queue.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
