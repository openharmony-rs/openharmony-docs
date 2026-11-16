# @ohos.util.Queue (Linear Container Queue)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong; @lijin1039-->
<!--Designer: @Malzahar; @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-11-16T05:50:36.334Z pushedAt=2026-11-16T06:31:14.251Z nl=1 -->

Queue follows the first-in-first-out (FIFO) principle: elements are added at the tail and removed at the head. Queue is implemented based on a circular queue data structure.

Compared with [Deque](js-apis-deque.md), Queue adds elements at the tail and removes elements at the head, whereas Deque supports adding and removing elements at both ends.

**Recommended use case**: Use Queue in FIFO scenarios.

The document uses generics, involving the following generic type parameters:<br>
- T: Type, a generic type parameter, which can be of any type

> **NOTE**
>
> - The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - Container classes, implemented in static languages, have restrictions on storage locations and properties, and do not support custom properties or methods.


## Modules to Import

```ts
import { Queue } from '@kit.ArkTS';
```


## Queue

### Properties

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| length | number | Yes| No| Number of elements in a Queue.|


### constructor

constructor()

The constructor of Queue, which creates a new Queue instance with an initial length of 0. The Queue container class is implemented using a static language, which restricts the storage location and properties, and does not support custom properties and methods.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200012 | The Queue's constructor cannot be directly invoked. |

**Example**

```ts
// Create a Queue instance.
let queue = new Queue<number | string | Object>();
console.info("queue length:", queue.length);  // queue length: 0
```

### add

add(element: T): boolean

Inserts an element at the tail of the queue. If the insertion is successful, true is returned and the queue length increases; otherwise, false is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| element | T | Yes| Target element.|

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Operation result. The value **true** is returned if the element is added; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The add method cannot be bound. |

**Example**

```ts
class PersonInfo {
  name: string = "";
  age: string = "";
}
// Create a Queue instance that supports multiple types.
let queue = new Queue<number | string | PersonInfo | number[]>();
// Add an element to the tail of the queue.
queue.add("a");
queue.add(1);
let b = [1, 2, 3];
queue.add(b);
let c : PersonInfo = {name : "Dylan", age : "13"};
queue.add(c);
console.info("result:", queue.length);  // result: 4
```

### pop

pop(): T

Removes the element at the head of the queue and returns the removed element. When Queue is empty, undefined is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| T | Returns the removed element. Returns undefined when Queue is empty. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The pop method cannot be bound. |

**Example**

```ts
let queue = new Queue<number>();
queue.add(2);
queue.add(4);
queue.add(5);
queue.add(2);
queue.add(4);
// Delete the head element of the queue, and return the deleted element.
let result = queue.pop();
console.info("result:", result);  // result: 2
```

### getFirst

getFirst(): T

Obtains the head element of the queue (without removing the head element of the queue).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| T | Returns the head element of the queue. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The getFirst method cannot be bound. |

**Example**

```ts
let queue = new Queue<number>();
queue.add(2);
queue.add(4);
queue.add(5);
queue.add(2);
// Obtain the head element of the queue.
let result = queue.getFirst();
console.info("result:", result);  // result: 2
```

### forEach

forEach(callbackFn: (value: T, index?: number, Queue?: Queue&lt;T&gt;) => void, thisArg?: Object): void

Traverses each element in the Queue instance and executes the callback function on each element.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callbackFn | function | Yes | Callback function executed for each element. |
| thisArg | Object | No | Value used as this when callbackFn is called. Default value is the current instance object. |

callbackFn parameters

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | T | Yes| Value of the element that is currently traversed.|
| index | number | No | Index value of the current traversal. If not specified, the traversal starts from 0 by default. |
| Queue | Queue&lt;T&gt; | No | Instance object that currently calls the forEach method. If not specified, the current instance object is used. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The forEach method cannot be bound. |

**Example**

```ts
let queue = new Queue<number>();
queue.add(2);
queue.add(4);
queue.add(5);
queue.add(4);
// Traverse each element in the Queue and execute the callback function for each element.
queue.forEach((value: number, index: number): void => {
  console.info("value:" + value, "index:" + index);
});
// value:2 index:0
// value:4 index:1
// value:5 index:2
// value:4 index:3
```

### [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;T&gt;

Returns an iterator, where each item is an element of type T.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;T&gt; | Returns an iterator used to traverse all elements in the Queue. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**Example**
```ts
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
// Obtain the iterator of Queue.
let iter = queue[Symbol.iterator]();
// Traverse elements through the next method of the iterator.
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