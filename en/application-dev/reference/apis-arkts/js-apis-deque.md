# @ohos.util.Deque (Linear Container Deque)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong; @lijin1039-->
<!--Designer: @Malzahar; @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=fa87684a3d68d73092de76cbd3803fc3d90b97e4 translatedAt=2026-11-16T05:30:00.903Z pushedAt=2026-11-16T06:31:14.189Z nl=1 -->

Deque (double-ended queue) is implemented based on the circular queue data structure and supports insertion and deletion of elements at both ends. Deque has both first-in-first-out and last-in-first-out characteristics, and can be used as both a queue and a stack depending on the operation end. When the current capacity is insufficient to accommodate newly inserted elements, Deque dynamically adjusts its capacity, doubling it each time, without the need to manually preset the capacity.

Queue allows element removal at the front and insertion at the rear. Compared with [Queue](js-apis-queue.md), which only allows element deletion at the front and insertion at the back, Deque permits insertion and deletion at both ends.

Both [ArrayList](js-apis-arraylist.md) and Deque support insertion and deletion at the ends, but Deque does not support insertion in the middle. Deque is more efficient than an ArrayList for inserting and deleting elements at the front, whereas an ArrayList excels in element access efficiency.

**Recommended use case**: Use **Deque** when you need to frequently insert or remove elements at both the ends of a container.

This topic uses the following to identify the use of generics:
- T: Type


> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> Container classes, implemented in static languages, have restrictions on internal storage methods and supported properties, and do not support custom properties or methods.


## Modules to Import

```ts
import { Deque } from '@kit.ArkTS';
```

## Deque

### Properties

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| length | number | Yes| No| Number of elements in a Deque.|

### constructor

constructor()

The constructor of Deque, used to create an empty Deque instance based on the circular queue data structure.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200012 | The Deque's constructor cannot be directly invoked. |

**Example**

```ts
// Create a Deque instance.
let deque = new Deque<string | number | boolean | Object>();
```

### insertFront

insertFront(element: T): void

Inserts an element at the head of the Deque. After successful insertion, the number of elements in the Deque increases by 1. The efficiency of inserting an element at the head of a Deque is higher than that of an ArrayList.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| element | T | Yes | Element to insert at the head. The type must be consistent with the generic type T specified when the Deque is instantiated. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The insertFront method cannot be bound. |

**Example**

```ts
class PersonInfo {
  name: string = "";
  age: string = "";
}

// Create a deque that supports multiple types.
let deque = new Deque<string | number | boolean | Array<number> | PersonInfo>();
// Insert a string element at the head.
deque.insertFront("a");
// Insert a number element at the head.
deque.insertFront(1);
let numArray = [1, 2, 3];
deque.insertFront(numArray);
let person: PersonInfo = {name : "Dylan", age : "13"};
deque.insertFront(person);
deque.insertFront(false);
console.info("result:", deque[0]);  // result: false
```

### insertEnd

insertEnd(element: T): void

Inserts an element at the tail of the Deque. After the insertion succeeds, the number of elements in the Deque increases by 1.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| element | T | Yes | Element to insert at the tail. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The insertEnd method cannot be bound. |

**Example**

```ts
class PersonInfo {
  name: string = "";
  age: string = "";
}

// Create a deque that supports multiple types
let deque = new Deque<string | number | boolean | Array<number> | PersonInfo>();
// Insert a string element at the tail
deque.insertEnd("a");
// Insert a number element at the tail
deque.insertEnd(1);
let numArray = [1, 2, 3];
deque.insertEnd(numArray);
let person: PersonInfo = {name : "Dylan", age : "13"};
deque.insertEnd(person);
deque.insertEnd(false);
console.info("result:", deque[0]);  // result: a
```

### has

has(element: T): boolean

Checks whether this Deque has the specified element.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| element | T | Yes | Specified element to search for in the Deque, used to determine whether the Deque contains the element. The type must be consistent with the generic type T specified when the Deque is instantiated. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Operation result. The value **true** is returned if the specified element is contained; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The has method cannot be bound. |

**Example**

```ts
// Create a Deque instance.
let deque = new Deque<string>();
// Insert an element at the head.
deque.insertFront("squirrel");
// Determine whether the Deque contains the specified element.
let result = deque.has("squirrel");
console.info("result:", result);  // result: true
```

### popFirst

popFirst(): T

Removes and returns the first element of the Deque. After the removal succeeds, the number of elements in the Deque decreases by 1. The Deque is more efficient than ArrayList at removing elements from the head.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| T | First element removed.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The popFirst method cannot be bound. |

**Example**

```ts
// Create a Deque instance and insert elements.
let deque = new Deque<number>();
deque.insertFront(2);
deque.insertFront(4);
deque.insertEnd(5);
deque.insertFront(2);
deque.insertFront(4);
// Delete and return the deque's first element.
let result = deque.popFirst();
console.info("result:", result);  // result: 4
```

### popLast

popLast(): T

Removes and returns the last element of the Deque. After the removal succeeds, the number of elements in the Deque decreases by 1.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| T | Last element removed.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The popLast method cannot be bound. |

**Example**

```ts
// Create a Deque instance and insert elements.
let deque = new Deque<number>();
deque.insertFront(2);
deque.insertEnd(6);
deque.insertFront(5);
deque.insertFront(2);
deque.insertFront(4);
// Delete and return the deque's tail element.
let result = deque.popLast();
console.info("result:", result);  // result: 6
```

### forEach

forEach(callbackFn: (value: T, index?: number, deque?: Deque&lt;T&gt;) => void, thisArg?: Object): void

Traverses each element in the Deque instance through a callback function.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callbackFn | function | Yes | Callback function executed when traversing each element. The value of `this` during execution can be specified through the `thisArg` parameter. During the execution of the callback function, it is not recommended to modify the Deque (such as inserting or deleting elements), otherwise it may cause abnormal traversal behavior. |
| thisArg | Object | No | Used as the value of `this` when `callbackFn` is invoked. Pass this parameter when you need to change the `this` reference in the callback function; if not passed, the default value is the current instance object. |

callbackFn parameters

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | T | Yes| Value of the element that is currently traversed.|
| index | number | No | The index value of the current iteration, incrementing from 0. |
| deque | [Deque](#deque)&lt;T&gt; | No | The instance object that calls the forEach method, that is, the Deque instance being traversed. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The forEach method cannot be bound. |

**Example**

```ts
// Create a Deque instance and insert elements.
let deque = new Deque<number>();
deque.insertFront(2);
deque.insertEnd(3);
deque.insertFront(1);
deque.insertEnd(4);
// Use forEach to traverse each element in the Deque and execute the callback function.
deque.forEach((value: number, index: number): void => {
  console.info("value:" + value, "index:" + index);
});
/*
Output: value:1 index:0
         value:2 index:1
         value:3 index:2
         value:4 index:3
 */
```

### getFirst

getFirst(): T

Obtains the head element of the Deque instance without removing it. After the call, the content and length of the Deque remain unchanged. To remove and return the first element, use popFirst.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| T | Returns the head element of the Deque instance. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The getFirst method cannot be bound. |

**Example**

```ts
// Create a Deque instance and insert elements.
let deque = new Deque<number>();
deque.insertEnd(2);
deque.insertEnd(4);
deque.insertFront(5);
deque.insertFront(4);
// Get the head element of the Deque.
let result = deque.getFirst();
console.info("result:", result);  // result: 4
```

### getLast

getLast(): T

Obtains the tail element of the Deque instance without removing it. After the call, the content and length of the Deque remain unchanged. To remove and return the tail element, use popLast.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| T | Returns the tail element of the Deque instance. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The getLast method cannot be bound. |

**Example**

```ts
// Create a Deque instance and insert elements.
let deque = new Deque<number>();
deque.insertFront(2);
deque.insertFront(4);
deque.insertFront(5);
deque.insertFront(4);
// Get the tail element of the Deque.
let result = deque.getLast();
console.info("result:", result);  // result: 2
```

### [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;T&gt;

Returns an iterator that traverses the elements in the Deque in insertion order. Each item of the iterator is an element of type T.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;T&gt; | Returns an iterator used to traverse all elements in the Deque instance. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**Example**
```ts
let deque = new Deque<number>();
deque.insertFront(2);
deque.insertFront(4);
deque.insertFront(5);
deque.insertFront(4);

// Method 1:
for (let item of deque) {
  console.info("value:" + item);
}
/*
Output result:
value:4
value:5
value:4
value:2
 */

// Method 2:
let iter = deque[Symbol.iterator]();
let iterResult: IteratorResult<number> = iter.next();
while (!iterResult.done) {
  console.info("value:" + iterResult.value);
  iterResult = iter.next();
}
/*
Output result:
value:4
value:5
value:4
value:2
 */
```