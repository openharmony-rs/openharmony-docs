# 异步并发（Promise和async/await） (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

异步并发用于描述代码执行到异步等待点后被挂起，并在异步操作完成后继续执行的能力。ArkTS-Sta通过[Promise](../reference/apis-arkts/arkts-sta-promise.md)和async/await提供异步并发能力，适用于I/O非阻塞操作、轻量级任务编排，以及有明确顺序或并行关系的异步逻辑。

异步并发不会自动把计算任务切换到其他线程。同一线程内的异步代码在等待期间可以让出执行权，但回调和await之后的代码仍会按照异步调度继续执行。对于CPU密集型或需要多线程执行的任务，建议结合[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)、[EAWorker（独占线程任务执行器）(ArkTS)](../reference/apis-arkts/eaworker_managed.md)等多线程并发能力使用。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。
> - ArkTS-Dyn相关说明请参见[异步并发 (Promise和async/await)](async-concurrency-overview.md)。
> - Promise接口的完整说明请参见[Promise (异步操作)](../reference/apis-arkts/arkts-sta-promise.md)。

## Promise

Promise用于表示一个异步操作的最终完成或失败情况及其结果值。Promise创建后处于pending（进行中）状态，异步操作完成后会转换为fulfilled（已完成）或rejected（已拒绝）状态，状态一旦改变就不可再变更。

Promise提供[then](../reference/apis-arkts/arkts-sta-promise.md#then-1)、[catch](../reference/apis-arkts/arkts-sta-promise.md#catch)和[finally](../reference/apis-arkts/arkts-sta-promise.md#finally)等方法注册回调函数，用于处理异步操作的成功结果、失败原因和最终清理逻辑。当Promise状态改变后，对应回调会被异步调度执行。

以下示例创建一个Promise对象，模拟延迟返回数据的异步操作。

```ts
// ArkTS-Sta示例
function queryScore(id: int): Promise<int> {
  return new Promise<int>((resolve, reject) => {
    setTimeout(() => {
      if (id > 0) {
        resolve(90);
      } else {
        reject(new Error("invalid id"));
      }
    }, 1000);
  });
}
```

Promise对象创建后，可以通过then方法处理成功结果，通过catch方法处理失败原因。

```ts
// ArkTS-Sta示例
let promise: Promise<int> = queryScore(100);

promise.then((score: int) => {
  console.info("score: " + score); // score: 90
  return score + 5;
}).then((newScore: int) => {
  console.info("new score: " + newScore); // new score: 95
}).catch((error: Error) => {
  console.error("query failed: " + error.message); // query failed: invalid id（查询失败时）
});
```

多个Promise之间存在并行关系时，可以使用Promise提供的静态方法进行编排。

```ts
// ArkTS-Sta示例
let promise1: Promise<int> = queryScore(1);
let promise2: Promise<int> = queryScore(2);
let promise3: Promise<int> = queryScore(3);

Promise.all<int>([promise1, promise2, promise3]).then((scores: Array<int>) => {
  console.info("score count: " + scores.length); // score count: 3
}).catch((error: Error) => {
  console.error("query failed: " + error.message); // query failed: invalid id（任一Promise失败时）
});
```

ArkTS-Sta中的Promise与ArkTS-Dyn、TypeScript中的使用方式基本一致，但存在以下差异和限制：

- Promise构造器中的resolve函数必须传入一个参数。对于Promise\<void>，需要调用resolve(undefined)完成解析。
- Promise构造器中的reject函数和Promise.reject只能接受Error类型参数，不支持使用字符串、数字等任意类型作为拒绝原因。
- then和catch中的失败回调参数类型应标注为Error或其父类类型。需要访问具体错误类型时，可在回调内部进行显式类型转换。
- 不建议声明Promise\<Promise\<T>>后直接调用then。需要嵌套Promise场景时，应让外层Promise直接解析为最终结果类型，或使用Awaited\<T>描述await后的类型。
- Promise.allSettled返回的是PromiseFulfilledResult和PromiseRejectedResult类实例。根据status判断结果后，需要通过as显式转换为对应类型再访问value或reason。
- Promise构造器的executor函数不能声明为async。需要在executor中执行异步逻辑时，应将异步逻辑放入独立的async函数或异步闭包中。

Promise\<void>的resolve需要显式传入undefined，示例如下：

```ts
// ArkTS-Sta示例
function delay(time: int): Promise<void> {
  return new Promise<void>((resolve) => {
    setTimeout(() => {
      resolve(undefined);
    }, time);
  });
}
```

reject和失败回调需要使用Error类型，示例如下：

```ts
// ArkTS-Sta示例
let promise: Promise<string> = new Promise<string>((resolve, reject) => {
  reject(new Error("operation failed"));
});

promise.catch((error: Error) => {
  console.error("error: " + error.message); // error: operation failed
});
```

使用`Promise.allSettled`处理结果时，需要显式转换结果类型，示例如下：

```ts
// ArkTS-Sta示例
let promise1: Promise<string> = Promise.resolve<string>("success");
let promise2: Promise<string> = Promise.reject<string>(new Error("failed"));

Promise.allSettled<string>([promise1, promise2]).then((results: PromiseSettledResult<string>[]) => {
  for (let result of results) {
    if (result.status === "fulfilled") {
      let fulfilled = result as PromiseFulfilledResult<string>;
      console.info("value: " + fulfilled.value); // value: success
    } else {
      let rejected = result as PromiseRejectedResult;
      console.error("reason: " + rejected.reason.message); // reason: failed
    }
  }
});
```

## async/await

async/await是基于Promise的异步语法。使用async声明的函数会返回Promise对象，函数内部可以使用await等待一个Promise完成。await会暂停当前async函数的后续执行，直到被等待的Promise转换为fulfilled或rejected状态。

以下示例展示了使用await以接近同步代码的方式处理异步结果。

```ts
// ArkTS-Sta示例
async function getScoreText(id: int): Promise<string> {
  let score: int = await queryScore(id);
  return "score: " + score;
}

async function printScore(): Promise<void> {
  let text: string = await getScoreText(100);
  console.info(text); // score: 90
}
```

await等待的Promise如果进入rejected状态，await表达式会抛出对应的Error对象。可以使用try/catch捕获异常，示例如下：

```ts
// ArkTS-Sta示例
async function printScoreWithErrorHandling(id: int): Promise<void> {
  try {
    let score: int = await queryScore(id);
    console.info("score: " + score); // score: 90（id > 0时）；query failed: invalid id（id <= 0时走catch）
  } catch (error) {
    let e = error as Error;
    console.error("query failed: " + e.message); // query failed: invalid id
  }
}
```

在ArkTS-Sta中使用async/await时，需要注意以下约束：

- await只能在async函数中使用。调用返回Promise的方法时，如果需要获取异步结果，应在async函数中使用await。
- 不支持在全局初始化阶段直接或间接调用async函数。需要在函数、方法或事件处理逻辑中触发异步流程。
- 泛型async函数返回`await Promise<U>`的结果时，返回类型应使用`Promise<Awaited<U>>`描述实际结果类型。
- 不支持泛型async箭头函数。需要泛型异步逻辑时，应使用泛型async函数声明。

泛型async函数示例如下：

```ts
// ArkTS-Sta示例
async function loadValue<T>(loader: () => Promise<T>): Promise<Awaited<T>> {
  let value = await loader();
  return value;
}

let v1: string = await loadValue<string>(() => Promise.resolve("hello"));
```

需要在Promise executor中执行异步逻辑时，不要将executor声明为async，示例如下：

```ts
// ArkTS-Sta示例
function asyncResolve(): Promise<int> {
  return new Promise<int>((resolve, reject) => {
    runAsync(resolve, reject);
  });
}

async function runAsync(resolve: (value: int) => void, reject: (error: Error) => void): Promise<void> {
  try {
    await delay(1000);
    resolve(1);
  } catch (error) {
    reject(error as Error);
  }
}
```

## 使用建议

- Promise和async/await适合描述异步等待与任务编排，不适合直接承载长时间CPU计算。CPU密集型任务建议使用[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)等多线程能力。
- 异步函数内部不应长时间执行同步阻塞逻辑，否则会影响同一线程后续异步回调的调度。
- 多个异步任务之间无顺序依赖时，可使用`Promise.all`、`Promise.any`、`Promise.race`或`Promise.allSettled`组合任务，减少不必要的串行等待。
- 在多线程共享数据场景中，应结合[AsyncLock (异步锁)](../reference/apis-arkts/arkts-sta-asynclock.md)、并发容器或原子操作保证数据访问安全。
