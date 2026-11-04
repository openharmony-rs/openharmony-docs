# Asynchronous Concurrency (Promise and Async/Await)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=6a2160de7f946f511924c492fc7938582c7172e2 translatedAt=2026-11-04T09:08:47.579Z pushedAt=2026-11-04T09:35:53.196Z nl=1 -->


Promise and async/await are standard JS asynchronous syntax that provide asynchronous concurrency capabilities. When asynchronous code is executed, it is suspended and resumes execution after the asynchronous operation is complete, ensuring that only one piece of code is running at a time. The following are typical asynchronous concurrency usage scenarios:

- Non-blocking I/O operations: network requests, file reads and writes, timers, etc.

- Lightweight tasks without CPU blocking: a single task has a short execution time.

- Clear logical dependencies: tasks with explicit order or parallel relationships.

Asynchronous concurrency is a feature of programming languages that allows programs to continue executing other asynchronous code without waiting for certain operations to complete.

## Promise

A Promise is an object used to process asynchronous operations. It converts asynchronous operations into a style similar to synchronous operations for easier code writing and maintenance. A Promise manages different phases of asynchronous operations through the state mechanism. There are three states for a Promise: pending (in progress), fulfilled (completed, also called resolved), and rejected (failed). After creation, a Promise is in the pending state and transitions to the fulfilled or rejected state upon completion of the asynchronous operation.

The Promise state is irreversible (once pending changes to fulfilled/rejected, it cannot change again).

Promise provides the **then**, **catch**, and **finally** methods to register callback functions to handle the success or failure of asynchronous operations. When the Promise status changes, the callback function is added to the microtask queue for execution. The event loop mechanism ensures that microtasks are executed first after macro tasks are executed, thereby ensuring asynchronous scheduling of callback functions.

The most basic usage is to instantiate a Promise object through the constructor, passing in a function with two parameters, called the executor function. The executor function receives two parameters: resolve and reject, which represent the callback functions for the success and failure of the asynchronous operation, respectively.

For example, the following code creates a Promise object and simulates an asynchronous operation:

<!-- @[promise_async_operation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/AsyncConcurrencyOverview/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
const promise: Promise<number> = new Promise((resolve: Function, reject: Function) => {
  setTimeout(() => {
    const randomNumber: number = Math.random();
    if (randomNumber > 0.5) {
      resolve(randomNumber);
    } else {
      reject(new Error('Random number is too small'));
    }
  }, 1000);
})
```


In the above code, the **setTimeout** function simulates an asynchronous operation and generates a random number after 1 second. If the random number is greater than 0.5, the **resolve** callback is invoked with the random number; otherwise, the **reject** callback is invoked with an error object.

Promise can also use finally to register a callback function, which is executed regardless of the final state of the Promise (fulfilled or rejected). For example:

<!-- @[promise_then_catch_handling](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/AsyncConcurrencyOverview/entry/src/main/ets/pages/Index.ets) --> 

``` TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// ...
  /*
   * After a Promise object is created, you can use the then method and the catch method to specify the callback functions for the fulfilled state and the rejected state.
   * The then method can accept two parameters: one function that handles the fulfilled state, and another function that handles the rejected state.
   *
   * If only one parameter is passed, it means that when the state of the Promise object changes to fulfilled, the then method automatically calls this callback function and passes the result of the Promise object to it as a parameter.
   * Use the catch method to register a callback function for handling the "failure" result, that is, to catch the exception thrown when the state of the Promise changes to the rejected state or when the operation fails.
   */
  // Use the then method to define the callbacks for success and failure.
  promise.then((result: number) => {
    console.info(`Succeeded in getting number, number is ${result}`); // Execute on success.
  }, (error: BusinessError) => {
    console.error(`Failed to get number. Code: ${error.code}, message: ${error.message}`); // Execute on failure.
  });

  // Use the then method to define the success callback, the catch method to define the failure callback, and the finally method to define the callback after the task ends.
  promise.then((result: number) => {
    console.info(`Succeeded in getting number, number is ${result}`); // Execute on success.
  }).catch((error: BusinessError) => {
    console.error(`Failed to get number. Code: ${error.code}, message: ${error.message}`); // Execute on failure.
  }).finally(() => {
    // Execute after the task ends, regardless of success or failure.
    console.info('Promise execution finished.');
  });
```


In the preceding code, the callback function of the **then** method receives the success result of the Promise object and outputs the result to the console. If the Promise object enters the rejected state, the callback function of the **catch** method receives the error object and outputs the error object to the console.

> **NOTE**
>
> When a Promise object is rejected and not handled by the **catch** method, it triggers the **globalUnhandledRejectionDetected** event. You can use the [errorManager.on('globalUnhandledRejectionDetected')](../reference/apis-ability-kit/js-apis-app-ability-errorManager.md#errormanageronglobalunhandledrejectiondetected18) API to listen for this event and globally capture unhandled Promise rejects.

## Async/Await

Async/Await is syntactic sugar for handling asynchronous operations with Promises, making it easier and more readable to write asynchronous code. You can use the **async** keyword to declare an asynchronous function and the **await** keyword to wait for the resolution (fulfilled or rejected) of a Promise, and write asynchronous operation code in synchronous mode.

An **async** function returns a Promise object to implement an asynchronous operation. It can contain zero or more **await** keywords, pausing execution until the associated Promise completes its state transition (fulfilled/rejected). If an exception is thrown during function execution, the exception directly triggers the returned Promise to enter the rejected state, and the error object can be captured using the **catch** method or the second callback parameter of **then**.

The code snippet below uses async/await to simulate an asynchronous operation that returns a string after 3 seconds.

<!-- @[async_await_sync_operation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/AsyncConcurrencyOverview/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
async function myAsyncFunction(): Promise<string> {
  const result: string = await new Promise((resolve: Function) => {
    setTimeout(() => {
      resolve('Hello, world!');
    }, 3000);
  });
  console.info(result); // Output: Hello, world!
  return result;
}

@Entry
@Component
struct PromiseAsyncAwait {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(async () => {
            let res: string = await myAsyncFunction();
            console.info(`Result is:  ${res}`);
            this.message = 'success';
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```


In the preceding example code, **await** waits for the Promise to resolve and stores the resolved value in the **result** variable.

Note that when waiting for an asynchronous operation, you need to place the operation in an async function and use it with await, and the await keyword is only valid inside an async function (it can only be used inside an async function). You can also use a try/catch block to catch exceptions.

<!-- @[async_operation_error_handling_with_try_catch](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/AsyncConcurrencyOverview/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
async function myAsyncFunction(): Promise<void> {
  try {
     const result: string = await new Promise((resolve: Function) => {
        resolve('Hello, world!');
     });
  } catch (e) {
     console.error(`Get exception: ${e}`);
  }
}
```

