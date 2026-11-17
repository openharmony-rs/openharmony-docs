---
kits: ["ArkTS Kit"]
description: "Explains asynchronous and multithreaded concurrent programming in ArkTS, including Promise, async/await, the event loop, TaskPool, Worker, Sendable, and inter-thread communication."
keywords: ["ArkTS", "concurrent programming", "asynchronous concurrency", "Promise", "async", "await", "TaskPool", "Worker", "Sendable"]
doctype: guide
status: active
---

# Concurrent Programming
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=8923bda514baa1452b967ea964ea779c7417bd8e translatedAt=2026-11-12T12:34:02.235Z pushedAt=2026-10-30T06:21:33.935Z nl=1 -->

Concurrent programming allows multiple tasks to make progress without blocking the UI main thread, improving app performance and responsiveness. ArkTS provides asynchronous concurrency (`Promise`, `async`/`await`) for lightweight tasks such as single I/O operations, and multithreaded concurrency (`TaskPool`, `Worker`) for time-consuming tasks such as CPU-intensive computation.

## Basic Concepts of Concurrency

Concurrency means that multiple tasks make progress during the same period. On multicore devices, tasks can run in parallel on different CPUs. On single-core devices, the CPU switches to other tasks when a task waits for I/O or sleeps, improving resource utilization. Appropriate use of concurrency provides the following benefits:

- Fully utilizes computing resources and improves overall program performance.
- Prevents time-consuming tasks from blocking the UI main thread, keeping the UI responsive.
- Supports modular, loosely coupled task organization.

For an overview of concurrency capabilities, see [Concurrency Overview](../arkts-utils/concurrency-overview.md).

ArkTS provides two concurrency strategies for different task characteristics:

- **Asynchronous concurrency**: Asynchronous code pauses when it needs to wait and resumes later. Only one piece of code executes at a time. This suits single I/O tasks such as network requests and file reads and writes. ArkTS provides this capability through `Promise` and `async`/`await`.
- **Multithreaded concurrency**: Multiple pieces of code can execute simultaneously. The UI main thread continues responding to user actions while background threads perform time-consuming operations. This suits compute-intensive or long-running tasks such as image encoding and decoding and data processing. ArkTS provides this capability through `TaskPool` and `Worker`.

## Asynchronous Concurrency

Asynchronous concurrency is a language feature that allows a program to continue executing other asynchronous code without waiting for certain operations to finish. ArkTS provides asynchronous concurrency through `Promise` and `async`/`await`.

### Asynchronous Functions: async and await

Declare an asynchronous function by adding `async` before `function`. Its return value is automatically wrapped in a `Promise`. `await` waits for a `Promise` to settle and obtains its result, and can be used only inside asynchronous functions. While waiting, the current function pauses and returns control to the event loop without blocking the thread. A rejected `Promise` in an `await` expression becomes an exception that can be caught with `try-catch`.

<!-- @[async_await_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Concurrency.ets) -->

``` TypeScript
// An async function automatically wraps its return value in a Promise.
async function fetchMessage(): Promise<string> {
  return 'Hello ArkTS';
}

// await can be used only in an async function to wait for a Promise and obtain its result.
async function loadMessage(): Promise<void> {
  try {
    let message = await fetchMessage();
    console.info(`${message}`); // 'Hello ArkTS'
  } catch (error) {
    // await turns a rejected Promise into an exception that try-catch can catch.
    console.error(`Loading failed: ${(error as Error).message}`);
  }
}

loadMessage();  // Top-level await is not supported. This call returns a Promise without waiting for completion.
```

The final `loadMessage()` call has no `await`: `await` is supported only inside `async` functions, not at module top level. Calling an asynchronous function at top level therefore does not await the returned `Promise`, and execution continues without waiting for completion. By contrast, `await fetchMessage()` inside `loadMessage` waits for the `Promise` and obtains its result before continuing.

For more `async`/`await` usage and examples, see [Asynchronous Concurrency (Promise and async/await)](../arkts-utils/async-concurrency-overview.md#asyncawait).

### Promise and Common Operations

A `Promise` represents the eventual result of an asynchronous operation. It starts in the `pending` state and transitions to `fulfilled` or `rejected` when the operation finishes. This transition is irreversible. Use `then` and `catch` to register success and failure callbacks and chain multiple asynchronous steps.

<!-- @[promise_basic_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Concurrency.ets) -->

``` TypeScript
// Create a Promise using the constructor.
let basicPromise = new Promise<string>((resolve, reject) => {
  let success = true;
  if (success) {
    resolve('Operation succeeded');
  } else {
    reject(new Error('Operation failed'));
  }
});

// Register success and failure callbacks with then and catch, and chain calls.
basicPromise
  .then((value: string): string => `${value}, continue processing`)
  .then((value: string): void => console.info(`${value}`))
  .catch((error: Error): void => console.error(`${error.message}`));
```

Use common `Promise` static methods to combine asynchronous tasks: `Promise.all` waits for all tasks to finish and fails if any task fails; `Promise.race` uses the first settled result; `Promise.allSettled` collects all results regardless of success or failure; `Promise.any` uses the first successful result.

<!-- @[promise_combinators](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Concurrency.ets) -->

``` TypeScript
// Promise.all(): wait for all tasks; fail if any task fails.
let allPromise = Promise.all([Promise.resolve(1), Promise.resolve(2)]);
allPromise.then((values: number[]): void => console.info(`${values.join(', ')}`)); // 1, 2

// Promise.race(): use the result of the first settled Promise.
let fastPromise = new Promise<string>((resolve: (value: string) => void) => {
  setTimeout(() => resolve('fast'), 100);
});
let slowPromise = new Promise<string>((resolve: (value: string) => void) => {
  setTimeout(() => resolve('slow'), 200);
});
Promise.race([fastPromise, slowPromise])
  .then((value: string): void => console.info(`${value}`)); // 'fast'

// Promise.allSettled(): wait for all tasks and collect results regardless of success or failure.
Promise.allSettled([Promise.resolve('ok'), Promise.reject(new Error('bad'))])
  .then((results): void => {
    results.forEach((result): void => {
      console.info(`${result.status}`);
    });
  });
// Output two log lines:
// 'fulfilled'
// 'rejected'

// Promise.any(): use the first successful result.
Promise.any([Promise.reject(new Error('A failed')), Promise.resolve('B succeeded')])
  .then((value: string): void => console.info(`${value}`)); // 'B succeeded'
```

The event loop determines when `Promise` callbacks run: synchronous code runs first, microtasks (`Promise.then`) run after the current task, and macrotasks (`setTimeout`) run in the next iteration.

<!-- @[event_loop_mechanism](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Async.ets) -->

``` TypeScript
// Event loop mechanism
console.info('1. Start');

// Macro task: setTimeout, setInterval, I/O, etc.
setTimeout(() => {
  console.info('2. setTimeout (macro task)');
}, 0);

// Micro task: Promise, queueMicrotask, etc.
Promise.resolve().then(() => {
  console.info('3. Promise (micro task)');
});

console.info('4. Synchronous code ends');

// Output order:
// '1. Start'
// '4. Synchronous code ends'
// '3. Promise (micro task)'
// '2. setTimeout (macro task)'
```

For details about `Promise` states, `then`/`catch`/`finally` callbacks, and chaining, see [Asynchronous Concurrency (Promise and async/await)](../arkts-utils/async-concurrency-overview.md#promise).

## Multithreaded Concurrency

Multithreaded concurrency allows multiple pieces of code to execute simultaneously: the UI main thread continues responding to user actions and updating the UI, while background threads perform time-consuming operations to avoid app freezes. ArkTS provides multithreaded concurrency through `TaskPool` and `Worker`. Both use the Actor concurrency model, with isolated thread memory and message-based communication.

For differences between `TaskPool` and `Worker` and guidance on choosing between them, see [Comparison Between TaskPool and Worker](../arkts-utils/taskpool-vs-worker.md).

### Worker Overview

`Worker` provides a multithreaded environment that separates app execution from the host thread. It suits scenarios with long-term host-thread interaction, complex task logic, and a need to manage thread lifecycles manually.

To use `Worker`, create an instance in the host thread, send messages to the Worker thread through `postMessage`, and receive results through `onmessage`. After the task finishes, call `terminate` to destroy the Worker thread and prevent resource leaks.

<!-- @[worker_basic_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/WorkerUsage.ts) -->

``` TypeScript
// WorkerUsage.ets
import { worker, MessageEvents } from '@kit.ArkTS';

// Use Worker to perform time-consuming tasks in a background thread.
function useWorker(): void {
  // Create a Worker thread instance (the Worker file must be in the module's ets directory).
  const wk: worker.ThreadWorker = new worker.ThreadWorker('entry/ets/workers/MyWorker.ets');

  // Receive messages from the Worker thread.
  wk.onmessage = (e: MessageEvents): void => {
    console.info(`Received Worker message: ${e.data}`);
    // Destroy the Worker thread after the task finishes to prevent resource leaks.
    wk.terminate();
  };

  // Send a message to the Worker thread to trigger the background task.
  wk.postMessage('hello world');
}

// useWorker(); // Typically called in a UI event callback such as a button click.
```

The Worker thread file (`entry/ets/workers/MyWorker.ets`) referenced by the host thread is shown below. The Worker thread receives messages through `workerPort` and sends results back after processing:

<!-- @[worker_thread_impl](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/workers/MyWorker.ets) -->

``` TypeScript
// entry/src/main/ets/workers/MyWorker.ets
import { worker, MessageEvents, ErrorEvent, ThreadWorkerGlobalScope } from '@kit.ArkTS';

// Port for communication between the Worker thread and the host thread.
const workerPort: ThreadWorkerGlobalScope = worker.workerPort;

// Receive messages sent by the host thread through postMessage.
workerPort.onmessage = (e: MessageEvents): void => {
  // Perform time-consuming work here (such as image decoding or data compression). Task details are omitted; do not operate the UI directly.
  if (e.data === 'hello world') {
    // Send results back through postMessage for the host thread to process and update the UI.
    workerPort.postMessage('success');
  }
}

// Callback for errors in the Worker thread.
workerPort.onerror = (err: ErrorEvent): void => {
  console.error(`MyWorker error: ${err.message}`);
}
```

Observe the following constraints when using Worker threads:

- **No UI operations**: UI operations must run in the main thread. Operating the UI from a Worker thread may cause display errors or crashes. Send results to the host thread through `postMessage` when UI updates are needed.
- **Isolated thread memory**: Worker and host threads have separate runtime environments and memory. A Worker thread cannot directly access host-thread objects. Data passed between threads must be serializable (such as primitive types and plain objects) or shareable Sendable objects. Functions, circular references, and special objects such as `Promise` and `Error` cannot be passed (except settled `Promise` objects).
- **Startup overhead and thread limits**: Starting each `Worker` incurs memory overhead. Prefer reuse over frequent creation and destruction. Memory permitting, a process supports up to 64 simultaneous Worker threads, and their total combined with runtimes created by `napi_create_ark_runtime` must not exceed 80. The actual available number adjusts dynamically based on memory usage.

For details about how `Worker` operates and how to create it, see [Worker Overview](../arkts-utils/worker-introduction.md).

### TaskPool Overview

`TaskPool` provides a system-managed multithreaded environment without requiring manual thread lifecycle management. The system dynamically scales worker threads according to task load for improved scheduling and resource utilization.

To use `TaskPool`, annotate a task function with `@Concurrent`, then pass the function and its arguments to `taskpool.execute`. The task is scheduled on a background thread, and its result is returned as a `Promise`. Compared with `Worker`, `TaskPool` has simpler APIs and lower resource overhead, making it the recommended choice for most time-consuming tasks (such as [Time-Consuming Task Concurrency Scenarios](../arkts-utils/time-consuming-task-overview.md)).

<!-- @[taskpool_basic_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TaskPoolUsage.ets) -->

``` TypeScript
import { taskpool } from '@kit.ArkTS';

// Annotate the task function with @Concurrent.
@Concurrent
function add(a: number, b: number): number {
  return a + b; // Execute in a TaskPool background thread.
}

async function useTaskPool(): Promise<void> {
  try {
    // Pass the task function and arguments to schedule it on a background thread.
    let result = await taskpool.execute(add, 2, 3);
    console.info(`Calculation result: ${result}`); // 5
  } catch (error) {
    console.error(`Task execution failed: ${(error as Error).message}`);
  }
}

useTaskPool();
```

For details about how `TaskPool` operates and its usage guidelines, see [TaskPool Overview](../arkts-utils/taskpool-introduction.md).

### Inter-Thread Communication and Sendable Object Sharing

ArkTS inter-thread communication uses the Actor concurrency model. Thread memory is isolated, so data and commands must be exchanged through message passing.

Ordinary objects (including regular class instances and arrays) are transferred using standard serialization (Structured Clone). The sender serializes an object into engine-independent data, and the receiver deserializes it into a new object with identical content. This is effectively a deep copy: the receiver obtains a copy, and modifying it does not affect the original. Serialization, deserialization, and deep-copy overhead grows with object size and nesting complexity, so consider communication time when passing large objects. Content that cannot be serialized, such as functions and circular references, cannot be transferred this way.

Use Sendable objects for large objects that must be passed across threads. Classes annotated with `@Sendable` can be passed by reference across threads, referring to the same object without copying and significantly reducing communication overhead. The main constraints for `@Sendable` classes are as follows:

- The parent class and implemented interfaces must also be Sendable. Member property types must be supported by Sendable (such as primitive types and other Sendable objects).
- Sendable objects cannot be initialized using object or array literals; create them with `new`.
- The class cannot access variables defined in the current module context.
- Members do not support type aliases, computed property names, or `!` assertions.

For complete rules, see [Sendable Usage Rules](../arkts-utils/sendable-constraints.md).

<!-- @[sendable_basic_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/SendableUsage.ets) -->

``` TypeScript
import { taskpool } from '@kit.ArkTS';

// Classes annotated with @Sendable can be shared by reference across threads.
@Sendable
class SharedCounter {
  public count: number = 0;

  increase(): void {
    this.count++;
  }
}

// Annotate the task function with @Concurrent; it can accept Sendable object arguments.
@Concurrent
function consumeSharedCounter(counter: SharedCounter): number {
  counter.increase();
  return counter.count;
}

async function useSendable(): Promise<void> {
  let counter = new SharedCounter();
  // A Sendable object is passed by reference and remains the same object across threads.
  let result = await taskpool.execute(consumeSharedCounter, counter);
  console.info(`Count returned by the child thread: ${result}`); // 1
  console.info(`Count read by the host thread: ${counter.count}`); // 1; shares the same object with the child thread.
}

useSendable();
```

For inter-thread communication methods, see [Inter-Thread Communication Overview](../arkts-utils/interthread-communication-overview.md). For Sendable object constraints and more examples, see [Sendable Object Overview](../arkts-utils/arkts-sendable.md).
