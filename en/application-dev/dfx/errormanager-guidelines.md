# Development of Error Manager

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @rr_cn-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## Overview

If coding specification issues or errors exist in the code of an application, the application may encounter unexpected errors, for example, uncaught exceptions, while it is running. In such a case, the application may exit unexpectedly. Error logs, however, are usually stored on users' local storage devices, making it inconvenient to locate faults. With the APIs provided by the errorManager module, the related errors and logs will be reported to your service platform for fault locating before application exits.

After the errorManager APIs are used to listen for exceptions and errors, the application does not exit. You are advised to add the synchronous exit operation after the callback is executed. If you only want to obtain error logs, you are advised to use [HiAppEvent](hiappevent-intro.md) to subscribe to events.

## Available APIs

The errorManager APIs are provided by [@ohos.app.ability.errorManager(Error Management Module)](../reference/apis-ability-kit/js-apis-app-ability-errorManager.md). Before using the APIs, you need to register an error observer and import it through **import**. For details, see [How to Develop](#how-to-develop).

**errorManager APIs**

| API| Description|
| -------- | -------- |
| on(type: "error", observer: ErrorObserver): number | Registers an observer for application errors. A callback will be invoked when an application error is detected. This API works in a synchronous manner. The return value is the serial number (SN) of the registered observer.|
| off(type: "error", observerId: number, callback: AsyncCallback&lt;void>): void | Unregisters an observer in callback mode. The number is the SN of the registered observer.|
| off(type: "error", observerId: number): Promise&lt;void> | Unregisters an observer in promise mode. The number is the SN of the registered observer.|
| on(type: 'globalErrorOccurred', observer: GlobalObserver): void | Registers a global observer for process errors. This is a synchronous API. When the system detects an application exception, the observer is called. (**Recommended**)<br>Note: This API is supported since API version 18.|
| off(type: 'globalErrorOccurred', observer?: GlobalObserver): void | Unregisters an observer in callback mode. (**Recommended**)<br>Note: This API is supported since API version 18.|
| on(type: 'globalUnhandledRejectionDetected', observer: GlobalObserver): void | Registers a global observer for process errors. This is a synchronous API. When the system detects an application promise exception, the observer is called. (**Recommended**)<br>Note: This API is supported since API version 18.|
| off(type: 'globalUnhandledRejectionDetected', observer?: GlobalObserver): void | Unregisters an observer in callback mode. (**Recommended**)<br>Note: This API is supported since API version 18.|
| on(type: 'loopObserver', timeout: number, observer: LoopObserver): void | Registers an observer for the message processing timeouts of the main thread.<br>This API can be called only in the main thread. A new observer will overwrite the previous one.|
| off(type: 'loopObserver', observer?: LoopObserver): void | Unregisters an observer for the message processing timeouts of the main thread in LoopObserver mode.|
| on(type: 'freeze', observer: FreezeObserver): void | Registers an observer for the main thread freeze event of the application. This API can be called only in the main thread. A new observer will overwrite the previous one.|
| off(type: 'freeze', observer?: FreezeObserver): void | Unregisters an observer for the message processing timeouts of the main thread in FreezeObserver mode.<br>Note: This API is supported since API version 18.|
| setDefaultErrorHandler(defaultHandler?: ErrorHandler): ErrorHandler | Sets a default error handler. This API can be called only in the main thread. When the **JS_CRASH** exception occurs, chain callback is supported and the return value is the last registered handler.<br>Note: This API is supported since API version 21.|
When an asynchronous callback is used, the return value can be processed directly in the callback.
When a promise is used, the return value can also be processed in the promise. For details about the result codes, see [Result Codes for Unregistering an Observer](#result-codes-for-unregistering-an-observer).

**ErrorObserver APIs**

| API| Description|
| -------- | -------- |
| onUnhandledException(errMsg: string): void | Called when an uncaught exception is reported after the application is registered.|
| onException?(errObject: Error): void | Called when an application exception is reported to the JavaScript layer after the application is registered.|

**LoopObserver APIs**

| API| Description|
| -------- | -------- |
| onLoopTimeOut?(timeout: number): void | Called when the message processing of the main thread times out.|

### Result Codes for Unregistering an Observer

| Result Code| Description|
| -------- | -------- |
| 0 | Normal.|
| -1 | Input **number** not exist.|
| -2 | Invalid parameter.|

## How to Develop

> **NOTE**
>
> You are advised to add a synchronous exit operation at the end of the exception callback to prevent multiple exception callbacks.

### Listening for a Single Thread

 Import the header files.
<!-- @[index_h](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
```

 Add an observer.
<!-- @[error_observer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
let observer: errorManager.ErrorObserver = {
  onUnhandledException(errorMsg) {
    hilog.info(0x0000, 'testTag','onUnhandledException, errorMsg: ', errorMsg);
  },
  onException(errorObj) {
    hilog.info(0x0000, 'testTag','onException, name: ', errorObj.name);
    hilog.info(0x0000, 'testTag','onException, message: ', errorObj.message);
    if (typeof(errorObj.stack) === 'string') {
      hilog.info(0x0000, 'testTag','onException, stack: ', errorObj.stack);
    }
  }
};
```

 Add a trigger button.
<!-- @[onclick_error_observer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
Button('Listening for a single thread').onClick(()=>{
  let observerId = -1;
  try {
    observerId = errorManager.on('error', observer);
  } catch (paramError) {
    let code = (paramError as BusinessError).code;
    let message = (paramError as BusinessError).message;
    hilog.error(0x0000, 'testTag',`error: ${code}, ${message}`);
  }
}).position({x:50, y:50});
```


### Listening for Process Exceptions

 Import the header files.
<!-- @[index_h](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
```

 Add an observer.
<!-- @[error_func](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
function errorFunc(observer: errorManager.GlobalError) {
  hilog.info(0x0000, 'testTag','result name :' + observer.name);
  hilog.info(0x0000, 'testTag','result message :' + observer.message);
  hilog.info(0x0000, 'testTag','result stack :' + observer.stack);
  hilog.info(0x0000, 'testTag','result instanceName :' + observer.instanceName);
  hilog.info(0x0000, 'testTag','result instanceType :' + observer.instanceType);
};
```

 Add a trigger button.
<!-- @[onclick_error_func](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
Button ('Listening for process exceptions').onClick(()=>{
  try {
    errorManager.on('globalErrorOccurred', errorFunc);
  } catch (paramError) {
    let code = (paramError as BusinessError).code;
    let message = (paramError as BusinessError).message;
    hilog.error(0x0000, 'testTag',`error: ${code}, ${message}`);
  }
}).position({x:50, y:100});
```

### Listening for Process Promise Exceptions

 Import the header files.
<!-- @[index_h](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
```

 Add an observer.
<!-- @[promise_func](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
function promiseFunc(observer: errorManager.GlobalError) {
  hilog.info(0x0000, 'testTag','result name :' + observer.name);
  hilog.info(0x0000, 'testTag','result message :' + observer.message);
  hilog.info(0x0000, 'testTag','result stack :' + observer.stack);
  hilog.info(0x0000, 'testTag','result instanceName :' + observer.instanceName);
  hilog.info(0x0000, 'testTag','result instanceType :' + observer.instanceType);
}
```

 Add a trigger button.
<!-- @[onclick_promise_func](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
Button ('Listening for process promise exceptions').onClick(()=>{
  try {
    errorManager.on('globalUnhandledRejectionDetected', promiseFunc);
  } catch (paramError) {
    let code = (paramError as BusinessError).code;
    let message = (paramError as BusinessError).message;
    hilog.error(0x0000, 'testTag',`error: ${code}, ${message}`);
  }
}).position({x:50, y:200});
```

### Listening for Main Thread Freeze Exceptions

 Import the header files.
<!-- @[index_h](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
```

 Add an observer.
<!-- @[freeze_call_back](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
function freezeCallback() {
  hilog.info(0x0000, 'testTag','freezecallback');
}
```

 Add a trigger button.
<!-- @[onclick_freeze_call_back](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
Button('Listening for main thread freeze exceptions').onClick(()=>{
  try {
    errorManager.on('freeze', freezeCallback);
  } catch (paramError) {
    let code = (paramError as BusinessError).code;
    let message = (paramError as BusinessError).message;
    hilog.error(0x0000, 'testTag',`error: ${code}, ${message}`);
  }
}).position({x:50, y:300});
```

### Listening for Main Thread Timeouts

 Import the header files.
<!-- @[index_h](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
```

 Add an observer.
<!-- @[loop_observer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
let loopObserver: errorManager.LoopObserver = {
  onLoopTimeOut(timeout: number) {
    hilog.info(0x0000, 'testTag','Duration timeout: ' + timeout);
  }
};
```

 Add a trigger button.
<!-- @[onclick_loop_observer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
Button ('Listening for main thread timeouts').onClick(()=>{
  try {
    errorManager.on('loopObserver', 1, loopObserver);
  } catch (paramError) {
    let code = (paramError as BusinessError).code;
    let message = (paramError as BusinessError).message;
    hilog.error(0x0000, 'testTag',`error: ${code}, ${message}`);
  }
}).position({x:50, y:150});
```

### Listening for Process Promise Exceptions

 Import the header files.
<!-- @[index_h](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
```

 Add an observer.
<!-- @[unhandled_rejection_observer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
let promise1 = new Promise<void>(() => {}).then(() => {
  throw new Error('uncaught error');
});

let unhandledrejectionObserver: errorManager.UnhandledRejectionObserver = (reason: Error, promise: Promise<void>) => {
  if (promise === promise1) {
    hilog.info(0x0000, 'testTag','promise1 is rejected');
  }
  hilog.info(0x0000, 'testTag','reason.name: ', reason.name);
  hilog.info(0x0000, 'testTag','reason.message: ', reason.message);
  if (reason.stack) {
    hilog.info(0x0000, 'testTag','reason.stack: ', reason.stack);
  }
};
```

 Add a trigger button.
<!-- @[onclick_unhandled_rejection_observer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/ErrorManage/ErrorManage/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
Button('Listening for process promise exceptions').onClick(()=>{
  try {
    errorManager.on('unhandledRejection', unhandledrejectionObserver);
  } catch (paramError) {
    let code = (paramError as BusinessError).code;
    let message = (paramError as BusinessError).message;
    hilog.error(0x0000, 'testTag',`error: ${code}, ${message}`);
  }
}).position({x:50, y:250});
```

### Chaining Error Handlers

The following sample files are stored in the same directory.

Define the first error handler and register the method. If no pre-handler is available, the process exits.
```ts
// firstErrorHandler.ets
import { errorManager } from '@kit.AbilityKit';
import { process } from '@kit.ArkTS';

let firstHandler: errorManager.ErrorHandler;
const firstErrorHandler: errorManager.ErrorHandler = (reason: Error) => {
    // Implement the logic of the first custom error handler.
    console.info('[FirstHandler] First uncaught exception handler invoked.');
    if (firstHandler) {
        firstHandler(reason);
    } else {
        // You are advised to add a null check. If the value is null, use a synchronous exit approach.
        const processManager = new process.ProcessManager();
        processManager.exit(0);
    }  
};

export function setFirstErrorHandler() {
    firstHandler = errorManager.setDefaultErrorHandler(firstErrorHandler); 
    console.info('Registered First Error Handler');
}
```

Define the second error handler and register the method to implement a chain call.
```ts
// secondErrorHandler.ets
import { errorManager } from '@kit.AbilityKit';
import { process } from '@kit.ArkTS';

let secondHandler: errorManager.ErrorHandler;
const secondErrorHandler: errorManager.ErrorHandler = (reason: Error) => {
    // Implement the logic of the second custom error handler.
    console.info('[SecondHandler] Second uncaught exception handler invoked.');
    if (secondHandler) {
        secondHandler(reason);
    } else {
        const processManager = new process.ProcessManager();
        processManager.exit(0);
    }
};

export function setSecondErrorHandler() {
    secondHandler = errorManager.setDefaultErrorHandler(secondErrorHandler); 
    console.info('Registered Second Error Handler');
}
```

Trigger the test through the button for the main component, register two handlers, and throw an error to verify the handler chain.
```ts
// Index.ets
import { setFirstErrorHandler } from './firstErrorHandler';
import { setSecondErrorHandler } from './secondErrorHandler';

@Entry
@Component
// Register two error handlers and throw an error to verify the chain call.
struct ErrorHandlerTest {
    private testErrorHandlers() {
      setFirstErrorHandler();
      setSecondErrorHandler();
      throw new Error('Test uncaught exception!');
    }

    build() {
      Column() {
        Button('Test Handler Chain')
          .width('90%') 
          .height(48)
          .margin(16)
          .onClick(() => this.testErrorHandlers())
      }
      .width('100%')
      .height('100%')
      .justifyContent(FlexAlign.Center) 
    }
}

```
