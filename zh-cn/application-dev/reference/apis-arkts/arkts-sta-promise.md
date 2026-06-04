# Promise (异步操作)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

本模块提供Promise异步操作相关的类型和接口说明。Promise是一种用于处理异步操作的对象，可以将异步操作转换为类似于同步操作的风格，以方便代码编写和维护。Promise表示一个异步操作的最终完成（或失败）情况及其结果值，提供了优雅的方式处理异步操作，避免传统回调函数的层层嵌套。

以下是典型的Promise使用场景：

- **I/O非阻塞操作**：网络请求、文件读写、定时器等。
- **任务轻量且无CPU阻塞**：单次任务执行时间短。
- **逻辑依赖清晰**：任务有明确的顺序或并行关系。

ArkTS-Dyn和TypeScript在Promise的概念与用法上保持一致。ArkTS-Sta基本也能保持一致，存在的差异点如下：

- 构造器函数的传参：reject函数，只能接受Error类型的参数，不支持传入任意类型的拒绝原因。在TypeScript中，reject可以接受任意类型值。
- 构造器函数的传参：resolve函数，必须传入一个参数，不支持无参数调用。对于`Promise<void>`类型，需要调用`resolve(undefined)`进行解析。在TypeScript中，resolve可以不传参数。
- allSettled方法返回的是[PromiseFulfilledResult](#promisefulfilledresult)和[PromiseRejectedResult](#promiserejectedresult)类实例，而非TypeScript中的普通对象`{status: "fulfilled", value: T}`或`{status: "rejected", reason: any}`。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 本模块首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## PromiseLike

PromiseLike是一个接口，定义了具有then方法的对象，用于表示异步操作的最终结果。任何实现了then方法的对象都可以被视为PromiseLike对象（也称为"thenable"对象）。

[Promise](#promise)类实现了PromiseLike接口。PromiseLike的主要用途是：

- 支持Promise与其他异步库之间的互操作，只要对方实现了then方法，就可以被Promise识别和处理。
- 在resolve中传入PromiseLike对象时，Promise会等待该对象完成后再继续处理。

> **说明：**
>
> - PromiseLike是TypeScript标准中定义的接口，ArkTS-Sta与其保持一致。

### then

then\<U = T, E = never>(onFulfilled: (value: T) => U|PromiseLike\<U>, onRejected?: (error: Error) => E|PromiseLike\<E>): PromiseLike\<Awaited\<U|E>>

为PromiseLike对象添加解析和拒绝处理程序，返回一个新的PromiseLike对象。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| onFulfilled | (value: T) => U\|[PromiseLike](#promiselike)\<U> | 是 | 解析处理程序，接收PromiseLike的解析值作为参数。 |
| onRejected | (error: Error) => E\|[PromiseLike](#promiselike)\<E> | 否 | 拒绝处理程序，接收拒绝原因作为参数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| [PromiseLike](#promiselike)\<Awaited\<U\|E>> | 返回一个新的PromiseLike对象。 |

**示例：**
```ts
// PromiseLike对象可以传入resolve，Promise会等待其完成
let promiseLike: PromiseLike<string> = Promise.resolve<string>("hello");
let promise = new Promise<string>((resolve) => {
  resolve(promiseLike);  // 传入PromiseLike对象
});
promise.then((value: string) => {
  console.info(value);  // hello
});
```

## Promise

Promise类用于表示异步操作的最终状态（成功或失败）及其结果值。Promise类实现了[PromiseLike](#promiselike)接口。

Promise提供了一种状态机制来管理异步操作的不同阶段，有三种状态：

- **pending**（进行中）：初始状态，Promise刚创建时的状态，表示异步操作尚未完成。
- **fulfilled**（已完成，也叫resolved）：表示异步操作成功完成，可通过[then](#then-1)方法获取结果值。
- **rejected**（已拒绝）：表示异步操作失败，可通过[catch](#catch)方法获取失败原因。

Promise创建后处于pending状态，异步操作完成后转换为fulfilled或rejected状态，状态一旦改变就不可再变更。

Promise提供了[then](#then-1)、[catch](#catch)、[finally](#finally)方法来注册回调函数以处理异步操作的成功或失败结果。当Promise状态改变时，回调函数会被异步调度执行。

### constructor

constructor(callback: (resolve: (value: T|PromiseLike\<T>) => void, reject: (error: Error) => void) => void)

Promise的构造函数，用于创建Promise对象。构造函数接收一个执行器函数，该执行器函数接收resolve和reject两个函数作为参数。在执行器函数中，可以调用resolve函数来异步解析Promise，或调用reject函数来异步拒绝Promise。

> **说明：**
>
> - resolve函数必须传入一个参数。对于`Promise<void>`类型，需要调用`resolve(undefined)`进行解析，而不能使用无参数的`resolve()`调用。
>
> - reject函数只能接受Error类型的参数，不支持传入任意类型的拒绝原因。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| callback | (resolve: (value: T\|[PromiseLike](#promiselike)\<T>) => void, reject: (error: Error) => void) => void | 是 | 执行器函数，接收resolve和reject函数作为参数。resolve函数用于解析Promise，reject函数用于拒绝Promise。 |

**示例：**
```ts
let promise = new Promise<number>((resolve, reject) => {
  setTimeout(() => {
    let randomNumber = Math.random();
    if (randomNumber > 0.5) {
      resolve(randomNumber);
    } else {
      reject(new Error("Random number is too small"));
    }
  }, 1000);
});
```

### then

then\<U = T, E = never>(onFulfilled: (value: T) => U|PromiseLike\<U>, onRejected?: (error: Error) => E|PromiseLike\<E>): Promise\<Awaited\<U|E>>

为Promise添加成功和失败的回调函数。当Promise成功完成时，onFulfilled回调会被调用并接收解析值作为参数；当Promise失败时，onRejected回调会被调用。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| onFulfilled | (value: T) => U\|[PromiseLike](#promiselike)\<U> | 是 | 成功回调，接收Promise的成功结果作为参数，可以返回一个值或另一个Promise。 |
| onRejected | (error: Error) => E\|[PromiseLike](#promiselike)\<E> | 否 | 失败回调，接收失败原因（Error对象）作为参数，可以返回一个值或另一个Promise。如果不提供此参数，返回的Promise会保持原Promise的失败原因。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| Promise\<Awaited\<U\|E>> | 返回一个新的Promise。新Promise的最终值取决于哪个回调被执行以及回调函数的返回值。如果回调返回普通值，新Promise会解析为该值；如果回调返回另一个Promise，新Promise会等待该Promise完成并获取其结果。 |

**示例：**
```ts
// 有参回调，可以访问解析值
let promise1 = Promise.resolve<string>("hello");
promise1.then((value: string) => {
  console.info("Resolved with: " + value);  // 输出 "Resolved with: hello"
  return value + " world";
});

// 同时处理解析和拒绝结果
let promise2 = new Promise<string>((resolve, reject) => {
  resolve("success");
});
promise2.then(
  (value: string) => {
    console.info("Resolved with: " + value);
    return value + " processed";
  },
  (error: Error) => {
    console.error("Rejected with: " + error.message);
    return "fallback";
  }
);
```

### then

then\<U = T>(onFulfilled: () => U|PromiseLike\<U>): Promise\<Awaited\<U>>

为已解析的Promise添加成功回调。当Promise成功完成时，onFulfilled回调会被调用。此重载的回调函数不接收参数，无法访问Promise的解析值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| onFulfilled | () => U\|[PromiseLike](#promiselike)\<U> | 是 | 成功回调，不接收参数，可以返回一个值或另一个Promise。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| Promise\<Awaited\<U>> | 返回一个新的Promise。如果当前Promise被解析且回调返回普通值，新Promise解析为该值；如果当前Promise被拒绝，新Promise也会被拒绝（错误透传）。 |

**示例：**
```ts
// 无参回调，无法访问解析值
let promise1 = Promise.resolve<string>("hello");
promise1.then(() => {
  console.info("Promise resolved");  // 无法获取"hello"
  return 42;
});
```

### then

then(_onFulfilled?: undefined): Promise\<Awaited\<T>>

透传原Promise的状态和值。当不提供回调函数或传入undefined时，返回的Promise会保持原Promise的状态和值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| _onFulfilled | undefined | 否 | 占位参数，用于接收undefined值。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| Promise\<Awaited\<T>> | 返回一个新的Promise，与原Promise具有相同的状态和值。 |

**示例：**
```ts
// 透传原Promise的值
let promise1 = Promise.resolve<string>("hello");
let promise2 = promise1.then();  // promise2解析值为"hello"
let promise3 = promise1.then(undefined);  // promise3解析值也为"hello"
```

### catch

catch\<U = never>(onRejected: () => U|PromiseLike\<U>): Promise\<Awaited\<T|U>>

为Promise添加失败回调（无参形式）。当Promise失败时，onRejected回调会被调用。此重载的回调函数不接收参数，无法访问错误原因。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| onRejected | () => U\|[PromiseLike](#promiselike)\<U> | 是 | 失败回调，不接收参数，可以返回一个值或另一个Promise。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| Promise\<Awaited\<T\|U>> | 返回一个新的Promise。如果当前Promise失败且回调返回值时，新Promise解析为该返回值；如果当前Promise解析，新Promise也解析为原值。 |

**示例：**
```ts
// 无参回调，无法访问错误原因
let promise = Promise.reject(new Error("operation failed"));
promise.catch(() => {
  console.error("出错了");  // 无法获取错误详情
  return "recovered";
});
```

### catch

catch\<U = never>(onRejected?: (error: Error) => U|PromiseLike\<U>): Promise\<Awaited\<T|U>>

为Promise添加失败回调（有参形式）。当Promise失败时，onRejected回调会被调用并接收错误原因作为参数。catch方法是then(undefined, onRejected)的简写形式。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| onRejected | (error: Error) => U\|[PromiseLike](#promiselike)\<U> | 否 | 失败回调，接收失败原因（Error对象）作为参数。可以返回一个值作为恢复结果，或返回另一个Promise。如果不提供此参数，返回的Promise会保持原Promise的失败原因。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| Promise\<Awaited\<T\|U>> | 返回一个新的Promise。如果当前Promise失败且回调返回值时，新Promise解析为该返回值（实现错误恢复）；如果当前Promise失败且回调抛出异常时，新Promise被拒绝。 |

**示例：**
```ts
// 有参回调，可以访问错误原因
let promise = Promise.reject(new Error("operation failed"));
promise.catch((error: Error) => {
  console.error("Error: " + error.message); // 输出 "Error: operation failed"
  return "recovered";  // 返回恢复值，后续then可以继续处理
}).then((result: string) => {
  console.info("Result: " + result);  // 输出 "Result: recovered"
});
```

### finally

finally\<U = T>(onFinally?: () => U|PromiseLike\<U>): Promise\<Awaited\<T>>

为Promise添加最终处理程序，无论Promise最终是解析还是拒绝，onFinally回调函数都会被调用。返回的Promise会保持原有Promise的解析或拒绝状态。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| onFinally | () => U\|[PromiseLike](#promiselike)\<U> | 否 | 最终处理程序，无论Promise解析还是拒绝都会调用。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| Promise\<Awaited\<T>> | 返回一个新的Promise，该Promise会保持与原Promise相同的解析或拒绝状态，但会先执行onFinally回调。 |

**示例：**
```ts
function fetchData(url: string): Promise<string> {
  console.info("开始获取数据...");
  return new Promise<string>((resolve, reject) => {
    setTimeout(() => {
      if (url === "valid") {
        resolve("ok");
      } else {
        reject(new Error("Failed"));
      }
    }, 1000);
  });
}

// 成功场景：finally执行后，原Promise的值继续传递
fetchData("valid").finally(() => {
  console.info("清理资源");
}).then((result: string) => {
  console.info("结果: " + result);
}).catch((error: Error) => {
  console.error("错误: " + error.message);
});

// 失败场景：finally执行后，原Promise的错误继续传递
fetchData("invalid").finally(() => {
  console.info("清理资源");
}).then((result: string) => {
  console.info("结果: " + result);
}).catch((error: Error) => {
  console.error("错误: " + error.message);
});
```

### resolve

static resolve(): Promise\<void>

创建一个已解析的空Promise对象，解析值为undefined。

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| Promise\<void> | 返回一个已解析的Promise，解析值为undefined。 |

**示例：**
```ts
let promise = Promise.resolve();
promise.then(() => {
  console.info("Promise resolved with undefined");
});
```

### resolve

static resolve\<U>(value: U|PromiseLike\<U>): Promise\<Awaited\<U>>

创建一个已解析的Promise对象。若value本身是Promise，则直接返回该Promise；否则创建一个以value为解析值的新Promise。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| value | U\|[PromiseLike](#promiselike)\<U> | 是 | Promise的解析值。如果value本身是Promise或PromiseLike对象，则直接返回该对象。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| Promise\<Awaited\<U>> | 返回一个已解析的Promise。如果value是Promise，则返回该Promise本身；否则返回一个以value为解析值的新Promise。 |

**示例：**
```ts
let promise1 = Promise.resolve<string>("hello");
let promise2 = Promise.resolve<number>(42);
let promise3 = Promise.resolve(promise1);  // 返回promise1本身
```

### reject

static reject(): Promise\<void>

创建一个已拒绝的空Promise对象，拒绝原因为一个空的Error对象。

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| Promise\<void> | 返回一个已拒绝的Promise，拒绝原因为空的Error对象。 |

**示例：**
```ts
let promise = Promise.reject();
promise.catch((error: Error) => {
  console.error("Promise rejected");
});
```

### reject

static reject\<U = never>(error: Error): Promise\<Awaited\<U>>

创建一个已拒绝的Promise对象，拒绝原因为传入的Error对象。

> **说明：**
>
> - reject方法只能接受Error类型的参数，不支持传入任意类型的拒绝原因。这与标准Promise规范中reject可以接受任意类型值的行为不同。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| error | Error | 是 | 指定Promise的拒绝原因，必须是Error类型。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| Promise\<Awaited\<U>> | 返回一个已拒绝的Promise。 |

**示例：**
```ts
let promise = Promise.reject<string>(new Error("Operation failed"));
promise.catch((error: Error) => {
  console.error("Error: " + error.message);  // Error: Operation failed
});
```

### all

static all\<U>(promises: FixedArray\<U|PromiseLike\<U>|undefined>): Promise\<Array\<Awaited\<U>>>

等待所有Promise都解析后返回一个包含所有解析值的数组。如果任何一个Promise被拒绝，则返回的Promise会立即被拒绝（以第一个拒绝原因为准，后续拒绝被忽略）。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| promises | FixedArray\<U\|[PromiseLike](#promiselike)\<U>\|undefined> | 是 | 一个Promise数组或包含PromiseLike对象的数组。数组中的undefined值会被转换为已解析的Promise。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| Promise\<Array\<Awaited\<U>>> | 返回一个Promise，当所有输入Promise都解析时，该Promise解析为一个包含所有解析值的数组（按原始顺序）；如果任一Promise被拒绝，则该Promise立即被拒绝（以第一个拒绝原因为准，后续拒绝被忽略）。空数组会立即解析为空数组。 |

**示例：**
```ts
let promise1 = Promise.resolve<string>("one");
let promise2 = Promise.resolve<string>("two");
let promise3 = Promise.resolve<string>("three");

let allPromise = Promise.all<string>([promise1, promise2, promise3]);
allPromise.then((values: Array<string>) => {
  console.info(values.toString()); // ["one", "two", "three"]
}).catch((error: Error) => {
  console.error("Rejected: " + error.message);
});
```

### all

static all\<U>(promises: Iterable\<U|PromiseLike\<U>>): Promise\<Array\<Awaited\<U>>>

等待所有Promise都解析后返回一个包含所有解析值的数组。支持可迭代对象（如Set、自定义Iterable）作为输入。若迭代器在遍历过程中抛出异常，返回的Promise会立即被拒绝（以第一个拒绝原因为准，后续拒绝被忽略）。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| promises | Iterable\<U\|[PromiseLike](#promiselike)\<U>> | 是 | 一个可迭代对象，包含Promise或PromiseLike对象。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| Promise\<Array\<Awaited\<U>>> | 返回一个Promise，当所有输入Promise都解析时，该Promise解析为一个包含所有解析值的数组；如果任一Promise被拒绝，则该Promise立即被拒绝（以第一个拒绝原因为准，后续拒绝被忽略）。 |

**示例：**
```ts
let promises = new Set<Promise<string>>();
promises.add(Promise.resolve<string>("one"));
promises.add(Promise.resolve<string>("two"));
promises.add(Promise.resolve<string>("three"));

let allPromise = Promise.all<string>(promises);
allPromise.then((values: Array<string>) => {
  console.info(values.toString()); // ["one", "two", "three"]
}).catch((error: Error) => {
  console.error("Rejected: " + error.message);
});
```

### allSettled

static allSettled\<U>(promises: FixedArray\<U|PromiseLike\<U>|undefined>): Promise\<PromiseSettledResult\<Awaited\<U>>[]>

等待所有Promise都完成（解析或拒绝）后返回一个包含每个Promise完成状态的对象数组。

> **说明：**
>
> 与TypeScript规范存在以下差异：
>
> 返回结果为[PromiseFulfilledResult](#promisefulfilledresult)和[PromiseRejectedResult](#promiserejectedresult)类实例，而非TypeScript中的普通对象`{status: "fulfilled", value: T}`或`{status: "rejected", reason: any}`。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| promises | FixedArray\<U\|[PromiseLike](#promiselike)\<U>\|undefined> | 是 | 一个Promise数组或包含PromiseLike对象的数组。数组中的undefined值会被转换为已解析的Promise。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| Promise\<[PromiseSettledResult](#promisesettledresultt)\<Awaited\<U>>[]> | 返回一个Promise，该Promise总是成功（不会因输入Promise失败而被拒绝），解析值为一个数组，包含每个Promise的结果状态。结果数组中的每个元素是[PromiseFulfilledResult](#promisefulfilledresult)或[PromiseRejectedResult](#promiserejectedresult)。 |

**示例：**
```ts
let promise1 = Promise.resolve<string>("one");
let promise2 = Promise.reject<string>(new Error("two failed"));
let promise3 = Promise.resolve<string>("three");

let allSettledPromise = Promise.allSettled<string>([promise1, promise2, promise3]);
allSettledPromise.then((results: PromiseSettledResult<string>[]) => {
  for (let result of results) {
    if (result.status === "fulfilled") {
      console.info("Fulfilled: " + (result as PromiseFulfilledResult<string>).value);
    } else {
      console.error("Rejected: " + (result as PromiseRejectedResult).reason.message);
    }
  }
});
```

### allSettled

static allSettled\<U>(promises: Iterable\<U|PromiseLike\<U>>): Promise\<PromiseSettledResult\<Awaited\<U>>[]>

等待所有Promise都完成（解析或拒绝）后返回一个包含每个Promise完成状态的对象数组。支持可迭代对象（如Set、自定义Iterable）作为输入。若迭代器在遍历过程中抛出异常，返回的Promise会立即被拒绝。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| promises | Iterable\<U\|[PromiseLike](#promiselike)\<U>> | 是 | 一个可迭代对象，包含Promise或PromiseLike对象。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| Promise\<[PromiseSettledResult](#promisesettledresultt)\<Awaited\<U>>[]> | 返回一个Promise，该Promise总是成功（不会因输入Promise失败而被拒绝），解析值为一个数组，包含每个Promise的结果状态。结果数组中的每个元素是[PromiseFulfilledResult](#promisefulfilledresult)或[PromiseRejectedResult](#promiserejectedresult)。 |

**示例：**
```ts
// 使用Set作为可迭代对象
let promises = new Set<Promise<string>>();
promises.add(Promise.resolve<string>("one"));
promises.add(Promise.reject<string>(new Error("two failed")));
promises.add(Promise.resolve<string>("three"));

let allSettledPromise = Promise.allSettled<string>(promises);
allSettledPromise.then((results: PromiseSettledResult<string>[]) => {
  for (let result of results) {
    if (result.status === "fulfilled") {
      let fulfilled = result as PromiseFulfilledResult<string>;
      console.info("Fulfilled: " + fulfilled.value);
    } else {
      let rejected = result as PromiseRejectedResult;
      console.error("Rejected: " + rejected.reason.message);
    }
  }
});
```

### any

static any\<U>(promises: FixedArray\<U|PromiseLike\<U>|undefined>): Promise\<Awaited\<U>>

等待任意一个Promise解析后返回该Promise的解析值。只有当所有Promise都被拒绝时，返回的Promise才会被拒绝，拒绝原因为一个AggregateError对象。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| promises | FixedArray\<U\|[PromiseLike](#promiselike)\<U>\|undefined> | 是 | 一个Promise数组或包含PromiseLike对象的数组。数组中的undefined值会被转换为已解析的Promise。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| Promise\<Awaited\<U>> | 返回一个Promise，当任意一个输入Promise解析时，该Promise解析为第一个解析的Promise的值；只有当所有Promise都被拒绝时，该Promise才会被拒绝，拒绝原因为一个AggregateError对象，包含所有拒绝原因。 |

**示例：**
```ts
let promise1 = Promise.reject<string>(new Error("one failed"));
let promise2 = Promise.resolve<string>("two");
let promise3 = Promise.resolve<string>("three");

let anyPromise = Promise.any<string>([promise1, promise2, promise3]);
anyPromise.then((value: string) => {
  console.info("First resolved: " + value); // First resolved:  two
}).catch((error: Error) => {
  if (error instanceof AggregateError) {
    console.error("All promises rejected");
  }
});
```

### any

static any\<U>(promises: Iterable\<U|PromiseLike\<U>>): Promise\<Awaited\<U>>

等待任意一个Promise解析后返回该Promise的解析值。支持可迭代对象（如Set、自定义Iterable）作为输入。若迭代器在遍历过程中抛出异常，返回的Promise会立即被拒绝。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| promises | Iterable\<U\|[PromiseLike](#promiselike)\<U>> | 是 | 一个可迭代对象，包含Promise或PromiseLike对象。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| Promise\<Awaited\<U>> | 返回一个Promise，当任意一个输入Promise解析时，该Promise解析为第一个解析的Promise的值；只有当所有Promise都被拒绝时，该Promise才会被拒绝。 |

**示例：**
```ts
let promises = new Set<Promise<string>>();
promises.add(Promise.reject<string>(new Error("one failed")));
promises.add(Promise.resolve<string>("two"));
promises.add(Promise.resolve<string>("three"));

let anyPromise = Promise.any<string>(promises);
anyPromise.then((value: string) => {
  console.info("First resolved: " + value); // First resolved: two
}).catch((error: Error) => {
  if (error instanceof AggregateError) {
    console.error("All promises rejected");
  }
});
```

### race

static race\<U>(promises: FixedArray\<U|PromiseLike\<U>|undefined>): Promise\<Awaited\<U>>

等待第一个完成的Promise（无论解析还是拒绝），并返回一个与该Promise状态相同的Promise。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| promises | FixedArray\<U\|[PromiseLike](#promiselike)\<U>\|undefined> | 是 | 一个Promise数组或包含PromiseLike对象的数组。数组中的undefined值会被转换为已解析的Promise。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| Promise\<Awaited\<U>> | 返回一个Promise，该Promise的状态和值与第一个完成的输入Promise相同。如果第一个完成的Promise被解析，则该Promise解析；如果第一个完成的Promise被拒绝，则该Promise拒绝。 |

**示例：**
```ts
let promise1 = new Promise<string>((resolve) => {
  setTimeout(() => resolve("one"), 500);
});
let promise2 = new Promise<string>((resolve) => {
  setTimeout(() => resolve("two"), 100);
});

let racePromise = Promise.race<string>([promise1, promise2]);
racePromise.then((value: string) => {
  console.info("First completed: " + value); // First completed: two
}).catch((error: Error) => {
  console.error("Rejected: " + error.message);
});
```

### race

static race\<U>(promises: Iterable\<U|PromiseLike\<U>>): Promise\<Awaited\<U>>

等待第一个完成的Promise（无论解析还是拒绝），并返回一个与该Promise状态相同的Promise。支持可迭代对象（如Set、自定义Iterable）作为输入。若迭代器在遍历过程中抛出异常，返回的Promise会立即被拒绝。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| promises | Iterable\<U\|[PromiseLike](#promiselike)\<U>> | 是 | 一个可迭代对象，包含Promise或PromiseLike对象。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| Promise\<Awaited\<U>> | 返回一个Promise，该Promise的状态和值与第一个完成的输入Promise相同。 |

**示例：**
```ts
let promises = new Set<Promise<string>>();
promises.add(new Promise<string>((resolve) => {
  setTimeout(() => resolve("one"), 500);
}));
promises.add(new Promise<string>((resolve) => {
  setTimeout(() => resolve("two"), 100);
}));

let racePromise = Promise.race<string>(promises);
racePromise.then((value: string) => {
  console.info("First completed: " + value); // First resolved: two
}).catch((error: Error) => {
  console.error("Rejected: " + error.message);
});
```

## PromiseStatus

PromiseStatus类表示Promise的完成状态，提供两个静态常量。

> **说明：**
>
> - 与TypeScript规范不同，ArkTS-Sta将Promise状态封装为类实例。在TypeScript中，Promise状态是内部概念，不暴露为独立的类。PromiseStatus不包含pending状态，pending是Promise的内部状态，用户无法通过PromiseStatus获取或判断pending状态。

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| fulfilled | "fulfilled" | 表示Promise已解析（成功完成）。 |
| rejected | "rejected" | 表示Promise已拒绝（失败）。 |

**示例：**
```ts
// 用于判断allSettled返回结果的状态
let promise1 = Promise.resolve<string>("success");
let promise2 = Promise.reject<string>(new Error("failed"));
let allSettledPromise = Promise.allSettled<string>([promise1, promise2]);
allSettledPromise.then((results: PromiseSettledResult<string>[]) => {
  for (let result of results) {
    if (result.status === PromiseStatus.fulfilled) {
      console.info("Promise fulfilled");
    } else if (result.status === PromiseStatus.rejected) {
      console.error("Promise rejected");
    }
  }
});
```

## PromiseFulfilledResult

PromiseFulfilledResult类表示[Promise.allSettled](#allsettled)返回结果中成功状态的元素。

> **说明：**
>
> - 与TypeScript规范不同，ArkTS-Sta将allSettled返回结果封装为类实例而非类型定义。在TypeScript中，对应的类型为`{status: "fulfilled", value: T}`。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | ---- | ---- | -------- |
| status | string | 否 | 否 | Promise的完成状态，值为"fulfilled"。 |
| value | T | 否 | 否 | Promise的解析值。 |

**示例：**
```ts
// 在allSettled结果中判断并获取成功值
let promise1 = Promise.resolve<string>("success");
let promise2 = Promise.reject<string>(new Error("failed"));
let allSettledPromise = Promise.allSettled<string>([promise1, promise2]);
allSettledPromise.then((results: PromiseSettledResult<string>[]) => {
  for (let result of results) {
    if (result.status === "fulfilled") {
      let fulfilled = result as PromiseFulfilledResult<string>;
      console.info("Value: " + fulfilled.value);
    }
  }
});
```

## PromiseRejectedResult

PromiseRejectedResult类表示[Promise.allSettled](#allsettled)返回结果中失败状态的元素。

> **说明：**
>
> - 与TypeScript规范不同，ArkTS-Sta将allSettled返回结果封装为类实例而非类型定义。在TypeScript中，对应的类型为`{status: "rejected", reason: any}`。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | ---- | ---- | -------- |
| status | string | 否 | 否 | Promise的完成状态，值为"rejected"。 |
| reason | Error | 否 | 否 | Promise的拒绝原因。 |

**示例：**
```ts
// 在allSettled结果中判断并获取失败原因
let promise1 = Promise.resolve<string>("success");
let promise2 = Promise.reject<string>(new Error("failed"));
let allSettledPromise = Promise.allSettled<string>([promise1, promise2]);
allSettledPromise.then((results: PromiseSettledResult<string>[]) => {
  for (let result of results) {
    if (result.status === "rejected") {
      let rejected = result as PromiseRejectedResult;
      console.error("Reason: " + rejected.reason.message);
    }
  }
});
```

## PromiseSettledResult\<T>

type PromiseSettledResult\<T> = PromiseFulfilledResult\<T> | PromiseRejectedResult

PromiseSettledResult是[PromiseFulfilledResult](#promisefulfilledresult)和[PromiseRejectedResult](#promiserejectedresult)的联合类型，表示[Promise.allSettled](#allsettled)方法返回数组中每个元素的类型。

| 类型 | 说明 |
| -------- | -------- |
| [PromiseFulfilledResult\<T>](#promisefulfilledresult) |  成功结果。当输入Promise成功解析时，status值为"fulfilled"，包含value属性表示解析值。 |
| [PromiseRejectedResult](#promiserejectedresult) | 失败结果。当输入Promise被拒绝时，status值为"rejected"，包含reason属性表示拒绝原因。 |