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

| Result Code| Cause|
| -------- | -------- |
| 0 | Normal.|
| -1 | Passed-in **number** not exist.|
| -2 | Invalid parameter.|

## How to Develop

> **NOTE**
>
> You are advised to add a synchronous exit operation at the end of the exception callback to prevent multiple exception callbacks.

### Listening for a Single Thread

```ts
import { AbilityConstant, errorManager, UIAbility, Want } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { process } from '@kit.ArkTS';

let registerId = -1;
let callback: errorManager.ErrorObserver = {
    onUnhandledException: (errMsg) => {
        console.info(errMsg);
    },
    onException: (errorObj) => {
        console.info('onException, name: ', errorObj.name);
        console.info('onException, message: ', errorObj.message);
        if (typeof(errorObj.stack) == 'string') {
            console.info('onException, stack: ', errorObj.stack);
        }
        // After the callback is executed, exit the process synchronously to avoid multiple exceptions.
        let pro = new process.ProcessManager();
        pro.exit(0);
    }
}

let abilityWant: Want;

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
        console.info("[Demo] EntryAbility onCreate");
        registerId = errorManager.on("error", callback);
        abilityWant = want;
    }

    onDestroy() {
        console.info("[Demo] EntryAbility onDestroy");
        errorManager.off("error", registerId, (result) => {
            console.info("[Demo] result " + result.code + ";" + result.message);
        });
    }

    onWindowStageCreate(windowStage: window.WindowStage) {
        // Set the main page for the created main window.
        console.info("[Demo] EntryAbility onWindowStageCreate");

        windowStage.loadContent("pages/index", (err) => {
            if (err.code) {
                console.error('Failed to load the content. Cause:' + JSON.stringify(err));
                return;
            }
        });
    }

    onWindowStageDestroy() {
        // Destroy the main window and release related UI resources.
        console.info("[Demo] EntryAbility onWindowStageDestroy");
    }

    onForeground() {
        // Switch to the foreground.
        console.info("[Demo] EntryAbility onForeground");
    }

    onBackground() {
        // Switch to the background.
        console.info("[Demo] EntryAbility onBackground");
    }
};
```

### Listening for Process Exceptions

```ts
import { AbilityConstant, errorManager, UIAbility, Want } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { process } from '@kit.ArkTS';

function errorFunc(observer: errorManager.GlobalError) {
    console.info("[Demo] result name :" + observer.name);
    console.info("[Demo] result message :" + observer.message);
    console.info("[Demo] result stack :" + observer.stack);
    console.info("[Demo] result instanceName :" + observer.instanceName);
    console.info("[Demo] result instanceType :" + observer.instanceType);
    // After the callback is executed, exit the process synchronously to avoid multiple exceptions.
    let pro = new process.ProcessManager();
    pro.exit(0);
}

let abilityWant: Want;

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
        console.info("[Demo] EntryAbility onCreate");
        errorManager.on("globalErrorOccurred", errorFunc);
        abilityWant = want;
    }

    onDestroy() {
        console.info("[Demo] EntryAbility onDestroy");
        errorManager.off("globalErrorOccurred", errorFunc);
    }

    onWindowStageCreate(windowStage: window.WindowStage) {
        // Set the main page for the created main window.
        console.info("[Demo] EntryAbility onWindowStageCreate");

        windowStage.loadContent("pages/index", (err) => {
            if (err.code) {
                console.error('Failed to load the content. Cause:' + JSON.stringify(err));
                return;
            }
        });
    }

    onWindowStageDestroy() {
        // Destroy the main window and release related UI resources.
        console.info("[Demo] EntryAbility onWindowStageDestroy");
    }

    onForeground() {
        // Switch to the foreground.
        console.info("[Demo] EntryAbility onForeground");
    }

    onBackground() {
        // Switch to the background.
        console.info("[Demo] EntryAbility onBackground");
    }
};
```

### Listening for Process Promise Exceptions

```ts
import { AbilityConstant, errorManager, UIAbility, Want } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { process } from '@kit.ArkTS';

function promiseFunc(observer: errorManager.GlobalError) {
    console.info("[Demo] result name :" + observer.name);
    console.info("[Demo] result message :" + observer.message);
    console.info("[Demo] result stack :" + observer.stack);
    console.info("[Demo] result instanceName :" + observer.instanceName);
    console.info("[Demo] result instanceType :" + observer.instanceType);
    // After the callback is executed, exit the process synchronously to avoid multiple exceptions.
    let pro = new process.ProcessManager();
    pro.exit(0);
}


let abilityWant: Want;

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
        console.info("[Demo] EntryAbility onCreate");
        errorManager.on("globalUnhandledRejectionDetected", promiseFunc);
        abilityWant = want;
    }

    onDestroy() {
        console.info("[Demo] EntryAbility onDestroy");
        errorManager.off("globalUnhandledRejectionDetected", promiseFunc);
    }

    onWindowStageCreate(windowStage: window.WindowStage) {
        // Set the main page for the created main window.
        console.info("[Demo] EntryAbility onWindowStageCreate");

        windowStage.loadContent("pages/index", (err) => {
            if (err.code) {
                console.error('Failed to load the content. Cause:' + JSON.stringify(err));
                return;
            }
        });
    }

    onWindowStageDestroy() {
        // Destroy the main window and release related UI resources.
        console.info("[Demo] EntryAbility onWindowStageDestroy");
    }

    onForeground() {
        // Switch to the foreground.
        console.info("[Demo] EntryAbility onForeground");
    }

    onBackground() {
        // Switch to the background.
        console.info("[Demo] EntryAbility onBackground");
    }
};
```

### Listening for Main Thread Freeze Exceptions

```ts
import { AbilityConstant, errorManager, UIAbility, Want } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { process } from '@kit.ArkTS';

// Define freezeCallback
function freezeCallback() {
    console.info("freezecallback");
}


let abilityWant: Want;

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
        console.info("[Demo] EntryAbility onCreate");
        errorManager.on("freeze", freezeCallback);
        abilityWant = want;
    }

    onDestroy() {
        console.info("[Demo] EntryAbility onDestroy");
        errorManager.off("freeze", freezeCallback);
    }

    onWindowStageCreate(windowStage: window.WindowStage) {
        // Set the main page for the created main window.
        console.info("[Demo] EntryAbility onWindowStageCreate");

        windowStage.loadContent("pages/index", (err) => {
            if (err.code) {
                console.error('Failed to load the content. Cause:' + JSON.stringify(err));
                return;
            }
        });
    }

    onWindowStageDestroy() {
        // Destroy the main window and release related UI resources.
        console.info("[Demo] EntryAbility onWindowStageDestroy");
    }

    onForeground() {
        // Switch to the foreground.
        console.info("[Demo] EntryAbility onForeground");
    }

    onBackground() {
        // Switch to the background.
        console.info("[Demo] EntryAbility onBackground");
    }
};
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
