# @ohos.util.Stack (Linear Container Stack)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong; @lijin1039-->
<!--Designer: @Malzahar; @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=e5b97192dbd8772da0547377cfcea671178fb9e9 translatedAt=2026-11-06T09:38:23.183Z pushedAt=2026-11-13T06:50:22.827Z nl=1 -->

Stack is implemented based on the array data structure. It follows the principle Last Out First In (LOFI) and supports data insertion and removal at one end.

Compared with [Queue](js-apis-queue.md), Stack is implemented based on the array data structure, while Queue is implemented based on the circular queue, which adds elements at the tail and removes elements at the head. Stack, however, performs insertion and removal operations only at one end.

**Recommended use cases:** Stack is generally suitable for scenarios that follow the Last In First Out (LIFO) principle, such as history management for undo/redo operations and function call stack simulation.

Generics are used in this document. The following generic type parameters are involved:
- T: Type, a generic type parameter, which can be of any type

> **NOTE**
>
> - The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - Container classes, implemented in static languages, have restrictions on storage locations and properties, and do not support custom properties or methods.


## Modules to Import

```ts
import { Stack } from '@kit.ArkTS';
```

## Stack

### Properties

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| length | number | Yes| No| Number of elements in a Stack.|


### constructor

constructor()

Constructor of Stack. After being called, an empty Stack instance object is created, with an initial length of 0.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200012 | The Stack's constructor cannot be directly invoked. |

**Example**

```ts
// Create a Stack instance.
let stack = new Stack<number | string | Object>();
console.info("length:", stack.length);  // length: 0
```


### push

push(item: T): T

Adds an element at the top of this Stack.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| item | T | Yes | Element to insert at the top of the stack. |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Returns the element inserted at the top of the stack. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The push method cannot be bound. |

**Example**

```ts
class PersonInfo {
  name: string = "";
  age: string = "";
  constructor(name: string, age: string) {
    this.name = name;
    this.age = age;
  }
}
// Create a Stack instance that supports multiple types.
let stack = new Stack<number | string | PersonInfo>();
// Push a string element onto the stack.
console.info("push:", stack.push("a"));  // push: a
// Push a number element onto the stack.
console.info("push:", stack.push(1));  //  push: 1
// Create a class instance and push it onto the stack.
let person1: PersonInfo = new PersonInfo("Dylan", "13");
let result = stack.push(person1);
console.info("result instanceof PersonInfo:", result instanceof PersonInfo);  // result instanceof PersonInfo: true
console.info("length:", stack.length);  // length: 3
```

### pop

pop(): T

Removes the top element from this Stack.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| T | Element removed. If the Stack is empty, **undefined** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The pop method cannot be bound. |

**Example**

```ts
let stack = new Stack<number>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(2);
stack.push(4);
// Remove the top element and return it.
let result = stack.pop(); 
console.info("result = " + result); // result = 4
```

### peek

peek(): T

Returns the top element of the stack. When the stack is empty, undefined is returned. The content of the stack remains unchanged after the call.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| T | Element removed. If the Stack is empty, **undefined** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The peek method cannot be bound. |

**Example**

```ts
let stack = new Stack<number>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(2);
// View the top element of the stack without removing it.
let result = stack.peek();
console.info("result:", result);  // result: 2
```

### locate

locate(element: T): number

Obtains the index of the first occurrence of the specified element in this Stack.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| element | T | Yes | Element to find. |

**Return value**

| Type| Description|
| -------- | -------- |
| number | Index of the element. If no match is found, **-1** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The locate method cannot be bound. |

**Example**

```ts
let stack = new Stack<number>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(2);
// Find the index of the first occurrence of element 5.
let result = stack.locate(5);
console.info("result:", result);  // result: 2
```

### forEach

forEach(callbackFn: (value: T, index?: number, stack?: Stack&lt;T&gt;) => void, thisArg?: Object): void

Traverses each element in the Stack instance object in the order from the bottom to the top of the stack, and executes the callback function on each element.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callbackFn | function | Yes | Callback function executed when traversing each element. |
| thisArg | Object | No | Used as the value of this when callbackFn is invoked. Default Value: the current instance object when not passed. |

callbackFn parameters

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | T | Yes| Value of the element that is currently traversed.|
| index | number | No | Subscript value of the current traversal, starting from 0 and incrementing sequentially. Default Value: 0. |
| stack | Stack&lt;T&gt; | No| Instance that calls the **forEach** API. The default value is this instance.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The forEach method cannot be bound. |

**Example**

```ts
let stack = new Stack<number>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(4);
// Traverse each element in the stack and execute the callback function.
stack.forEach((value: number, index: number): void => {
  console.info("value:" + value, "index:" + index);
});
// value:2 index:0
// value:4 index:1
// value:5 index:2
// value:4 index:3
```

### isEmpty

isEmpty(): boolean

Checks whether the stack is empty. Returns true if it is empty, and false otherwise.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns **true** if the Stack is empty; returns **false** otherwise.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The isEmpty method cannot be bound. |

**Example**

```ts
let stack = new Stack<number>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(4);
// Check whether the stack is empty.
let result = stack.isEmpty();
console.info("result:", result);  // result: false
```

### [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;T&gt;

Returns an iterator, each item of which is an element of type T.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;T&gt; | Returns an iterator used to traverse all elements in the Stack in the storage order. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**Example**
```ts
let stack = new Stack<number>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(4);

// Method 1:
for (let value of stack) {
  console.info("value:", value);
}
// value: 2
// value: 4
// value: 5
// value: 4

// Method 2:
// Create an iterator.
let iter = stack[Symbol.iterator]();
// Obtain the first iteration result.
let currentValue: IteratorResult<number> = iter.next().value;
// Traverse the elements in the iterator.
while (currentValue != undefined) {
  console.info("value: " + currentValue);
  currentValue = iter.next().value;
}
// value: 2
// value: 4
// value: 5
// value: 4
```