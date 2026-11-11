---
kits: ["ArkTS Kit / 方舟编程语言"]
description: "讲解ArkTS的异步与多线程并发编程，涵盖Promise、async/await、事件循环、TaskPool、Worker、Sendable及线程间通信等能力。"
keywords: [ArkTS, 并发编程, 异步并发, Promise, async, await, TaskPool, Worker, Sendable]
doctype: guide
status: active
---

# 并发编程
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

并发编程能够让程序同时推进多个任务而不阻塞UI主线程，是提升应用性能和响应能力的重要手段。ArkTS提供了异步并发（`Promise`、`async`/`await`）和多线程并发（`TaskPool`、`Worker`）两种并发能力：前者适用于单次I/O等轻量任务，后者适用于CPU密集型计算等耗时任务。

## 并发的基础概念

并发指在同一时间内多个任务同时推进。在多核设备上，多个任务可以在不同CPU上并行执行；在单核设备上，CPU会在某个任务等待I/O或休眠时切换执行其他任务，从而提高资源利用率。合理使用并发的收益包括：

- 充分利用计算资源，提升程序整体性能。
- 避免耗时任务阻塞UI主线程，保持界面响应流畅。
- 支持模块化、解耦的任务组织方式。

关于并发能力的整体介绍，可参见[并发概述](../arkts-utils/concurrency-overview.md)。

ArkTS针对不同任务特征提供两种并发处理策略：

- **异步并发**：异步代码在执行到需要等待的位置时暂停，并在未来某个时间点继续执行，同一时间只有一段代码在执行。适用于网络请求、文件读写等单次I/O任务，ArkTS通过`Promise`和`async`/`await`提供该能力。
- **多线程并发**：允许多段代码同时执行，UI主线程继续响应用户操作，后台线程执行耗时操作。适用于图片编解码、数据处理等计算密集型或长时间运行的任务，ArkTS通过`TaskPool`和`Worker`提供该能力。

## 异步并发

异步并发是一种编程语言特性，允许程序在执行某些操作时不必等待其完成，即可继续执行其他异步代码。ArkTS通过`Promise`和`async`/`await`提供异步并发能力。

### 异步函数：async 和 await

在`function`关键字前添加`async`即可声明异步函数，异步函数的返回值会被自动包装为`Promise`。`await`用于等待`Promise`完成并获取结果，只能用在异步函数内部；等待期间当前函数暂停执行、控制权交回事件循环，不会阻塞线程。`await`表达式中被拒绝的`Promise`会转为异常，可通过`try-catch`捕获处理。

<!-- @[async_await_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Concurrency.ets) -->

``` TypeScript
// async函数：返回值自动包装为Promise
async function fetchMessage(): Promise<string> {
  return 'Hello ArkTS';
}

// await只能在async函数中使用，等待Promise完成并获取结果
async function loadMessage(): Promise<void> {
  try {
    let message = await fetchMessage();
    console.info(`${message}`); // 'Hello ArkTS'
  } catch (error) {
    // await将被拒绝的Promise转为异常，可用try-catch捕获
    console.error(`加载失败: ${(error as Error).message}`);
  }
}

loadMessage();  // 顶层不能使用await，直接调用返回Promise，不等待完成
```

示例末尾的`loadMessage()`没有加`await`：`await`只能用于`async`函数内部，模块顶层不支持`await`，因此顶层直接调用异步函数，其返回的`Promise`不被等待，程序不等待其完成即继续执行；而`await fetchMessage()`位于`loadMessage`内部，会等待`Promise`完成并取得结果后再继续执行。

关于`async`/`await`的更多用法与示例，可参见[异步并发 (Promise和async/await)](../arkts-utils/async-concurrency-overview.md#asyncawait)。

### Promise及其常用操作

`Promise`是表示异步操作最终结果的对象。创建后处于`pending`（进行中）状态，异步操作完成后转换为`fulfilled`（已完成）或`rejected`（已拒绝）状态，且状态转换不可逆。通过`then`、`catch`方法可注册成功、失败回调，并支持链式调用串联多个异步步骤。

<!-- @[promise_basic_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Concurrency.ets) -->

``` TypeScript
// 通过构造函数创建Promise
let basicPromise = new Promise<string>((resolve, reject) => {
  let success = true;
  if (success) {
    resolve('操作成功');
  } else {
    reject(new Error('操作失败'));
  }
});

// then注册成功回调，catch注册失败回调，支持链式调用
basicPromise
  .then((value: string): string => `${value}，继续处理`)
  .then((value: string): void => console.info(`${value}`))
  .catch((error: Error): void => console.error(`${error.message}`));
```

处理多个异步任务时，可以组合使用`Promise`的常用静态方法：`Promise.all`等待全部完成、任一失败则整体失败；`Promise.race`采用最先完成的结果；`Promise.allSettled`无论成败都收集全部结果；`Promise.any`采用第一个成功的结果。

<!-- @[promise_combinators](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Concurrency.ets) -->

``` TypeScript
// Promise.all()：等待全部完成，任一失败则整体失败
let allPromise = Promise.all([Promise.resolve(1), Promise.resolve(2)]);
allPromise.then((values: number[]): void => console.info(`${values.join(', ')}`)); // 1, 2

// Promise.race()：采用最先完成的Promise结果
let fastPromise = new Promise<string>((resolve: (value: string) => void) => {
  setTimeout(() => resolve('fast'), 100);
});
let slowPromise = new Promise<string>((resolve: (value: string) => void) => {
  setTimeout(() => resolve('slow'), 200);
});
Promise.race([fastPromise, slowPromise])
  .then((value: string): void => console.info(`${value}`)); // 'fast'

// Promise.allSettled()：等待全部完成，无论成败都收集结果
Promise.allSettled([Promise.resolve('ok'), Promise.reject(new Error('bad'))])
  .then((results): void => {
    results.forEach((result): void => {
      console.info(`${result.status}`);
    });
  });
// 输出两行日志：
// 'fulfilled'
// 'rejected'

// Promise.any()：采用第一个成功的结果
Promise.any([Promise.reject(new Error('A失败')), Promise.resolve('B成功')])
  .then((value: string): void => console.info(`${value}`)); // 'B成功'
```

`Promise`回调的执行时机由事件循环决定：同步代码先执行，微任务（`Promise.then`）在当前任务后执行，宏任务（`setTimeout`）在下一轮执行。

<!-- @[event_loop_mechanism](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Async.ets) -->

``` TypeScript
// 事件循环机制
console.info('1. 开始');

// 宏任务（Macro Task）：setTimeout、setInterval、I/O等
setTimeout(() => {
  console.info('2. setTimeout（宏任务）');
}, 0);

// 微任务（Micro Task）：Promise、queueMicrotask等
Promise.resolve().then(() => {
  console.info('3. Promise（微任务）');
});

console.info('4. 同步代码结束');

// 输出顺序：
// '1. 开始'
// '4. 同步代码结束'
// '3. Promise（微任务）'
// '2. setTimeout（宏任务）'
```

关于`Promise`状态、`then`/`catch`/`finally`回调与链式调用的详细介绍，可参见[异步并发 (Promise和async/await)](../arkts-utils/async-concurrency-overview.md#promise)。

## 多线程并发

多线程并发允许同时执行多段代码：UI主线程继续响应用户操作和更新界面，后台线程执行耗时操作，避免应用卡顿。ArkTS通过`TaskPool`和`Worker`提供多线程并发能力，两者均基于Actor并发模型实现，线程间内存隔离、通过消息传递通信。

多线程并发中`TaskPool`与`Worker`的特点差异和选型建议，可参见[TaskPool和Worker的对比](../arkts-utils/taskpool-vs-worker.md)。

### Worker简介

`Worker`为应用程序提供多线程运行环境，实现应用程序执行过程与宿主线程分离，适合与宿主线程长期交互、任务逻辑复杂、需要自行管理线程生命周期的场景。

使用`Worker`的基本流程：宿主线程创建`Worker`实例后，通过`postMessage`向Worker线程发送消息，通过`onmessage`接收Worker线程返回的处理结果；任务完成后调用`terminate`销毁Worker线程，避免资源泄漏。

<!-- @[worker_basic_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/WorkerUsage.ts) -->

``` TypeScript
// WorkerUsage.ets
import { worker, MessageEvents } from '@kit.ArkTS';

// 使用Worker在后台线程执行耗时任务
function useWorker(): void {
  // 创建Worker线程实例（Worker线程文件需位于模块的ets目录下）
  const wk: worker.ThreadWorker = new worker.ThreadWorker('entry/ets/workers/MyWorker.ets');

  // 接收Worker线程返回的消息
  wk.onmessage = (e: MessageEvents): void => {
    console.info(`收到Worker消息: ${e.data}`);
    // 任务完成后销毁Worker线程，避免资源泄漏
    wk.terminate();
  };

  // 向Worker线程发送消息，触发后台任务
  wk.postMessage('hello world');
}

// useWorker(); // 一般在按钮单击等UI事件回调中调用
```

宿主线程引用的Worker线程文件（`entry/ets/workers/MyWorker.ets`）内容如下，Worker线程通过`workerPort`接收宿主线程消息，处理完成后将结果发回宿主线程：

<!-- @[worker_thread_impl](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/workers/MyWorker.ets) -->

``` TypeScript
// entry/src/main/ets/workers/MyWorker.ets
import { worker, MessageEvents, ErrorEvent, ThreadWorkerGlobalScope } from '@kit.ArkTS';

// Worker线程与宿主线程通信的端口
const workerPort: ThreadWorkerGlobalScope = worker.workerPort;

// 接收宿主线程通过postMessage发送的消息
workerPort.onmessage = (e: MessageEvents): void => {
  // 收到消息后在此执行耗时任务（如图片解码、数据压缩），示例省略具体任务实现；注意不能直接操作UI
  if (e.data === 'hello world') {
    // 处理结果通过postMessage发回宿主线程，由宿主线程处理并更新UI
    workerPort.postMessage('success');
  }
}

// Worker线程发生错误时的回调
workerPort.onerror = (err: ErrorEvent): void => {
  console.error(`MyWorker error: ${err.message}`);
}
```

Worker线程使用时需注意以下约束：

- **不能操作UI**：UI操作必须在主线程中执行，在Worker线程中操作UI可能导致界面异常或崩溃；需要更新界面时，应通过`postMessage`将结果发回宿主线程处理。
- **线程间内存隔离**：Worker线程与宿主线程拥有独立的运行环境和内存，不能直接访问宿主线程的对象；跨线程传递的数据需可序列化（基本类型、普通对象等）或为可共享的Sendable对象，不可传递函数、循环引用，以及`Promise`、`Error`等特殊对象（已完成状态的`Promise`除外）。
- **启动开销与数量限制**：每个`Worker`的启动存在一定内存开销，应避免频繁创建和销毁、优先复用；在内存允许的情况下，同一进程下最多支持同时开启64个Worker线程，且与`napi_create_ark_runtime`创建的runtime总数不超过80，实际可运行数量会根据内存使用情况动态调整。

`Worker`的运作机制、创建方式等详情，可参见[Worker简介](../arkts-utils/worker-introduction.md)。

### TaskPool简介

`TaskPool`为应用程序提供由系统统一管理的多线程环境，无需开发者管理线程生命周期。工作线程数量由系统根据任务负载动态扩缩容，调度和资源利用率更优。

使用`TaskPool`的基本流程：任务函数需要使用`@Concurrent`装饰器标注，通过`taskpool.execute`传入任务函数和参数后，任务被调度到后台线程执行，结果以`Promise`形式返回。相比`Worker`，`TaskPool`接口更易用、资源开销更低，是大多数耗时任务（如[耗时任务并发场景](../arkts-utils/time-consuming-task-overview.md)）的推荐选择。

<!-- @[taskpool_basic_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TaskPoolUsage.ets) -->

``` TypeScript
import { taskpool } from '@kit.ArkTS';

// 任务函数需要使用@Concurrent装饰器标注
@Concurrent
function add(a: number, b: number): number {
  return a + b; // 在TaskPool后台线程中执行
}

async function useTaskPool(): Promise<void> {
  try {
    // 传入任务函数和参数，任务被调度到后台线程执行
    let result = await taskpool.execute(add, 2, 3);
    console.info(`计算结果: ${result}`); // 5
  } catch (error) {
    console.error(`任务执行失败: ${(error as Error).message}`);
  }
}

useTaskPool();
```

`TaskPool`的运作机制、使用规范等详情，可参见[TaskPool简介](../arkts-utils/taskpool-introduction.md)。

### 线程间通信及Sendable对象共享

ArkTS的线程间通信基于Actor并发模型，线程间内存隔离，需要通过消息传递完成数据和命令的交互。

普通对象（包括普通类实例、数组等）采用标准的序列化（Structured Clone）方式传递：发送时将对象序列化为与引擎无关的数据，接收方反序列化后得到一个内容一致的新对象。因此传递过程相当于一次深拷贝——接收方拿到的是副本，对其修改不会影响原对象；序列化、反序列化和深拷贝的开销随对象大小和嵌套复杂度增长，传递大对象时需注意通信耗时。同时，函数、循环引用等无法序列化的内容不能以该方式传递。

对于需要跨线程传递的大对象，可以使用Sendable对象：通过`@Sendable`装饰器标注的类可在线程间以引用方式传递，跨线程前后指向同一个对象，无需拷贝，能显著降低通信开销。使用`@Sendable`类需满足以下主要约束：

- 类的父类和实现的接口必须也是Sendable的，成员属性的类型必须是Sendable支持的数据类型（基础类型、其他Sendable对象等）；
- 不能使用对象字面量或数组字面量初始化Sendable对象，须通过`new`创建；
- 类内部不能访问当前模块上下文环境中定义的变量；
- 成员不支持类型别名、计算属性名和`!`断言。

完整规则见[Sendable使用规则](../arkts-utils/sendable-constraints.md)。

<!-- @[sendable_basic_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/SendableUsage.ets) -->

``` TypeScript
import { taskpool } from '@kit.ArkTS';

// @Sendable装饰器标注的类可在线程间以引用方式共享
@Sendable
class SharedCounter {
  public count: number = 0;

  increase(): void {
    this.count++;
  }
}

// 任务函数使用@Concurrent装饰器标注，可接收Sendable对象参数
@Concurrent
function consumeSharedCounter(counter: SharedCounter): number {
  counter.increase();
  return counter.count;
}

async function useSendable(): Promise<void> {
  let counter = new SharedCounter();
  // Sendable对象引用传递，跨线程前后是同一个对象
  let result = await taskpool.execute(consumeSharedCounter, counter);
  console.info(`子线程返回的count: ${result}`); // 1
  console.info(`宿主线程读取的count: ${counter.count}`); // 1，与子线程共享同一对象
}

useSendable();
```

关于线程间通信方式可参见[ArkTS线程间通信概述](../arkts-utils/interthread-communication-overview.md)；Sendable对象的使用约束和更多示例，可参见[Sendable对象简介](../arkts-utils/arkts-sendable.md)。
