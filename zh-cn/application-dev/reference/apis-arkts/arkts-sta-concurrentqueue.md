# ConcurrentQueue (并发队列)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

ConcurrentQueue是一种线程安全队列容器，支持异步等待式的插入、弹出操作，也支持立即返回的非阻塞操作。队列为空时，`pop()`会异步等待直到队列中有元素；队列满时，`push()`会异步等待直到队列有空余容量。

**推荐使用场景：** 可用于实现多线程之间的数据传递、任务队列、流量控制等场景，允许生产者与消费者之间安全传递数据。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
> - `push()`和`pop()`返回`Promise`，需要与`await`配合使用。若不使用`await`，只能得到未完成的`Promise`对象，无法保证插入或弹出操作已经完成。
> - `ArrayConcurrentQueue<T>`和`LinkedConcurrentQueue<T>`的泛型参数`T`需为非空类型，不能将`null`或`undefined`作为队列元素。

## ConcurrentQueue

ConcurrentQueue\<T>是定义并发队列及其方法的interface，有两个实现类：[LinkedConcurrentQueue](#linkedconcurrentqueue)和[ArrayConcurrentQueue](#arrayconcurrentqueue)。

### 属性

| 名称     | 类型 | 只读 | 可选 | 说明                 |
| :------- | :--- | :--- | :--- | :------------------- |
| size     | int  | 是   | 否   | 队列中元素的个数。   |
| capacity | int  | 是   | 否   | 队列的容量。         |

### push

push(element: T): Promise\<void>

将元素插入队列尾部。如果队列已满，则异步等待，直到队列有空余容量后再插入元素。使用Promise异步回调。

该方法多线程并发执行安全。

**参数：**

| 参数名  | 类型 | 必填 | 说明               |
| :------ | :--- | :--- | :----------------- |
| element | T    | 是   | 要插入队列的数据，不能为`null`或`undefined`。 |

**返回值：**

| 类型           | 说明                       |
| :------------- | :------------------------- |
| Promise\<void> | Promise对象，无返回结果。  |

**示例：**

```typescript
let queueInt: containers.stackless.ConcurrentQueue<int> =
  new containers.stackless.LinkedConcurrentQueue<int>(10); // 并发队列容量设置为10
for (let i = 0; i < 10; i++) {
  await queueInt.push(i);
}
let size = queueInt.size; // 10
```

### pop

pop(): Promise\<Awaited\<T>>

弹出并返回队列的头部元素。如果队列为空，则异步等待，直到队列中有元素后再弹出元素。使用Promise异步回调。

该方法多线程并发执行安全。

**返回值：**

| 类型                 | 说明                                     |
| :------------------- | :--------------------------------------- |
| Promise\<[Awaited](../../quick-start/arkts-dyn-to-sta-concurrency-rules.md#函数返回类型为await-promiseu泛型类型时需要使用promiseawaitedu类型作为返回类型)\<T>> | Promise对象，返回泛型T被await之后的结果类型。      |

**示例：**

```typescript
let queueInt: containers.stackless.ConcurrentQueue<int> =
  new containers.stackless.LinkedConcurrentQueue<int>();
await queueInt.push(9);
let res = await queueInt.pop(); // 9
```

### add

add(element: T): boolean

尝试将元素插入队列。如果队列已满，则插入失败返回false，否则插入成功返回true。该方法不会等待。

该方法多线程并发执行安全。

**参数：**

| 参数名  | 类型 | 必填 | 说明               |
| :------ | :--- | :--- | :----------------- |
| element | T    | 是   | 待插入队列的数据，不能为`null`或`undefined`。 |

**返回值：**

| 类型    | 说明                                                    |
| :------ | :------------------------------------------------------ |
| boolean | 如果队列已满，插入失败返回false，否则插入成功返回true。 |

**示例：**

```typescript
let queueInt: containers.stackless.ConcurrentQueue<int> =
  new containers.stackless.LinkedConcurrentQueue<int>(10);
for (let i = 0; i < 10; i++) {
  let res = queueInt.add(i); // true
}
console.info("queue.length: ", queueInt.size);
let res = queueInt.add(11); // false
```

### poll

poll(): T \| undefined

尝试移除队列的头部元素。如果队列为空，则返回undefined，否则返回被移除的元素。该方法不会等待。

该方法多线程并发执行安全。

**返回值：**

| 类型           | 说明                                                  |
| :------------- | :---------------------------------------------------- |
| T \| undefined | 返回被移除的头部元素，如果队列为空，则返回undefined。 |

**示例：**

```typescript
let queueInt: containers.stackless.ConcurrentQueue<int> =
  new containers.stackless.LinkedConcurrentQueue<int>();
for (let i = 0; i < 10; i++) {
  queueInt.add(i);
}
let res = queueInt.poll(); // 0
res = queueInt.poll(); // 1
```

### getFirst

getFirst(): T | undefined

获取队列的头部元素，如果队列为空，则返回undefined。

该方法多线程并发执行安全。

**返回值：**

| 类型           | 说明                                              |
| :------------- | :------------------------------------------------ |
| T \| undefined | 返回队列头部元素，如果队列为空，则返回undefined。 |

**示例：**

```typescript
let queueInt: containers.stackless.ConcurrentQueue<int> =
  new containers.stackless.LinkedConcurrentQueue<int>();
for (let i: int = 0; i < 10; ++i) {
  queueInt.add(i);
}
let res = queueInt.getFirst(); // 0
res = queueInt.getFirst(); // 0
```

### isEmpty

isEmpty(): boolean

检查队列是否为空。

该方法多线程并发执行安全。

**返回值：**

| 类型    | 说明                                    |
| :------ | :-------------------------------------- |
| boolean | 队列为空返回true，队列不为空返回false。 |

**示例：**

```typescript
let queueInt: containers.stackless.ConcurrentQueue<int> =
  new containers.stackless.LinkedConcurrentQueue<int>();
let res = queueInt.isEmpty(); // true
queueInt.add(1);
res = queueInt.isEmpty(); // false
```

### remainingCapacity

remainingCapacity(): int

当前队列在不等待的情况下还可以容纳的元素数量，即剩余容量，等于队列的容量减去当前的元素个数。

该方法多线程并发执行安全。

**返回值：**

| 类型 | 说明                     |
| :--- | :----------------------- |
| int  | 返回当前队列的剩余容量。 |

**示例：**

```typescript
let queueInt: containers.stackless.ConcurrentQueue<int> =
  new containers.stackless.ArrayConcurrentQueue<int>(10);
for (let i = 0; i < 5; i++) {
  queueInt.add(i);
}
let remainingcapacity = queueInt.remainingCapacity(); // 5
queueInt.poll();
remainingcapacity = queueInt.remainingCapacity(); // 6
console.info("queue.remainingcapacity: ", queueInt.capacity - queueInt.size);
```

## LinkedConcurrentQueue

LinkedConcurrentQueue\<T>实现了[ConcurrentQueue](#concurrentqueue)接口，是一个基于链表实现的并发队列，提供异步等待式插入、弹出，以及立即返回的非阻塞操作。`T`需为非空类型，不能将`null`或`undefined`作为队列元素。

### constructor

constructor()

LinkedConcurrentQueue的构造函数，创建一个容量为Int.MAX_VALUE(2147483647)的LinkedConcurrentQueue\<T>实例。

**示例：**

```typescript
let queueInt: containers.stackless.ConcurrentQueue<int> =
  new containers.stackless.LinkedConcurrentQueue<int>();
let capacity = queueInt.capacity; // 2147483647
```

### constructor

constructor(capacity: int)

LinkedConcurrentQueue的构造函数，创建一个容量为capacity的LinkedConcurrentQueue\<T>实例。

**参数：**

| 参数名   | 类型 | 必填 | 说明                                                 |
| :------- | :--- | :--- | :--------------------------------------------------- |
| capacity | int  | 是   | 初始化队列的容量。 <br/>取值范围：大于0，且不超过Int.MAX_VALUE（2147483647）。<br/>当capacity小于等于0时，接口会抛出RangeError，无法正常运行。<br/> |

**示例：**

```typescript
let queueInt: containers.stackless.ConcurrentQueue<int> =
  new containers.stackless.LinkedConcurrentQueue<int>(10);
let capacity = queueInt.capacity; // 10
```

### constructor

constructor(iterable: Iterable\<T>)

LinkedConcurrentQueue的构造函数，传入一个实现了Iterable\<T>接口的可迭代对象。该构造函数创建一个容量为Int.MAX_VALUE(2147483647)的LinkedConcurrentQueue\<T>实例，并将iterable中的元素添加到新创建的链表并发队列中。

**参数：**

| 参数名   | 类型         | 必填 | 说明                         |
| :------- | :----------- | :--- | :--------------------------- |
| iterable | Iterable\<T> | 是   | 一个迭代器，用于初始化队列。 |

**示例：**

```typescript
let arr: Array<int> = [0];
let queueInt: containers.stackless.ConcurrentQueue<int> =
  new containers.stackless.LinkedConcurrentQueue<int>(arr);
let res = queueInt.capacity; // 2147483647
let size = queueInt.size; // 1
let first = queueInt.getFirst(); // 0
```

### constructor

constructor(capacity: int, iterable: Iterable\<T>)

LinkedConcurrentQueue的构造函数，传入一个实现了Iterable\<T>接口的可迭代对象。该构造函数创建一个容量为capacity的LinkedConcurrentQueue\<T>实例，并将iterable中的元素添加到新创建的链表并发队列中。

**参数：**

| 参数名   | 类型         | 必填 | 说明                                               |
| :------- | :----------- | :--- | :------------------------------------------------- |
| capacity | int          | 是   | 初始化队列容量。 <br/>取值范围：大于0，且不超过Int.MAX_VALUE（2147483647）。<br/> |
| iterable | Iterable\<T> | 是   | 一个迭代器，用于初始化队列。                       |

> **说明：**
>
> - 当capacity小于等于0时，接口会抛出RangeError，无法正常运行。
> - 当iterable中的元素个数大于capacity时，接口会抛出RangeError，无法正常运行。

**示例：**

```typescript
let arr: Array<int> = [0];
let iter = arr.values();
let queueInt: containers.stackless.ConcurrentQueue<int> =
  new containers.stackless.LinkedConcurrentQueue<int>(10, iter);
let res = queueInt.capacity; // 10
let size = queueInt.size; // 1
let first = queueInt.getFirst(); // 0
```

### getEnd

getEnd(): T | undefined

获取队列的尾部元素，如果队列为空，则返回undefined。

该方法多线程并发执行安全。

**返回值：**

| 类型           | 说明                                                |
| :------------- | :-------------------------------------------------- |
| T \| undefined | 返回队列尾部元素，若队列没有元素，则返回undefined。 |

**示例：**

```typescript
let queueInt: containers.stackless.LinkedConcurrentQueue<int> =
  new containers.stackless.LinkedConcurrentQueue<int>(10);
for (let i: int = 0; i < 10; ++i) {
  queueInt.add(i);
}
let res = queueInt.getEnd(); // 9
```

## ArrayConcurrentQueue

ArrayConcurrentQueue\<T>实现了[ConcurrentQueue](#concurrentqueue)接口，是一个基于数组实现的有界并发队列，提供异步等待式插入、弹出，以及立即返回的非阻塞操作。`T`需为非空类型，不能将`null`或`undefined`作为队列元素。

### constructor

constructor(capacity: int)

ArrayConcurrentQueue的构造函数，创建一个容量为capacity的ArrayConcurrentQueue\<T>实例。

**参数：**

| 参数名   | 类型 | 必填 | 说明                                             |
| -------- | ---- | ---- | ------------------------------------------------ |
| capacity | int  | 是   | 初始化队列的容量。 <br/>取值范围：大于0，且不超过Int.MAX_VALUE（2147483647）。<br/> 当capacity小于等于0时，接口会抛出RangeError，无法正常运行。<br/> |

**示例：**

```typescript
let queueInt: containers.stackless.ConcurrentQueue<int> =
  new containers.stackless.ArrayConcurrentQueue<int>(10);
let res = queueInt.isEmpty(); // true
```

### constructor

constructor(capacity: int, iterable: Iterable\<T>)

ArrayConcurrentQueue的构造函数。该构造函数创建一个容量为capacity的ArrayConcurrentQueue\<T>实例，并将iterable中的元素添加到新创建的数组并发队列中。

**参数：**

| 参数名   | 类型         | 必填 | 说明                                             |
| -------- | ------------ | ---- | ------------------------------------------------ |
| capacity | int          | 是   | 初始化队列的容量。 <br/>取值范围：大于0，且不超过Int.MAX_VALUE（2147483647）。<br/> |
| iterable | Iterable\<T> | 是   | 一个迭代器，用于初始化队列。                     |

> **说明：**
>
> - 当capacity小于等于0时，接口会抛出RangeError，无法正常运行。
> - 当iterable中的元素个数大于capacity时，接口会抛出RangeError，无法正常运行。

**示例：**

```typescript
let arr: Array<number> = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
let set: Set<number> = new Set<number>(arr);
let queueInt: containers.stackless.ConcurrentQueue<number> =
  new containers.stackless.ArrayConcurrentQueue<number>(200, set);
let capacity = queueInt.capacity; // 200
let size = queueInt.size; // 10
```

### getEnd

getEnd(): T \| undefined

获取队列的尾部元素，如果队列为空，则返回undefined。

该方法多线程并发执行安全。

**返回值：**

| 类型           | 说明                                                |
| -------------- | --------------------------------------------------- |
| T \| undefined | 返回队列尾部元素，若队列没有元素，则返回undefined。 |

**示例：**

```typescript
let queueInt: containers.stackless.ArrayConcurrentQueue<int> =
  new containers.stackless.ArrayConcurrentQueue<int>(10);
for (let i: int = 0; i < 10; ++i) {
  queueInt.add(i);
}
let res = queueInt.getEnd(); // 9
```