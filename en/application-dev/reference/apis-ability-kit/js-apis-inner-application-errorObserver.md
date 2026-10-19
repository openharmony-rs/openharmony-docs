# ErrorObserver

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Chenyufan466765692-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=d7833d54288ec20034339cf7164e5aaef52722e9 translatedAt=2026-09-03T11:56:53.702Z pushedAt=2026-09-05T10:47:30.786Z -->

Defines exception listening, which can be used as the input parameter of [errorManager.on('error')](js-apis-app-ability-errorManager.md#errormanageronerror) to listen for exceptions that occur in the current application. Through exception listening, developers can promptly capture and handle uncaught exceptions during application running and exceptions reported by the JavaScript layer, improving application stability and user experience.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { errorManager } from '@kit.AbilityKit';
```

## ErrorObserver.onUnhandledException

onUnhandledException(errMsg: string): void

Called when an uncaught exception occurs in the application. When an uncaught exception occurs in the application code, the system automatically invokes this method to pass the exception information to the developer for processing.

The difference from [ErrorObserver.onException](#errorobserveronexception10) is that onUnhandledException captures only unhandled exceptions, and its parameter contains only an error message string, whereas onException captures all exceptions reported to the JavaScript layer, and its parameter is a complete Error object containing more information such as name, message, and stack. It is recommended to use onException when complete error information is required, and onUnhandledException when only a simple error message is required. The two can be used in combination.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| errMsg | string | Yes | Information about the exception. |

**Example**

```ts
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observer: errorManager.ErrorObserver = {
  onUnhandledException(errMsg) {
    console.error('onUnhandledException, errMsg: ', errMsg);
  }
};

try {
  errorManager.on('error', observer);
} catch (error) {
  console.error(`registerErrorObserver failed, error.code: ${(error as BusinessError).code}, error.message: ${(error as BusinessError).message}`);
}
```

## ErrorObserver.onException<sup>10+</sup>

onException?(errObject: Error): void

Called when the application encounters an exception and reports it to the JavaScript layer. This callback is optional. If it is not implemented, the default system exception handling logic is used.

Can be used together with [ErrorObserver.onUnhandledException](#errorobserveronunhandledexception) to implement exception listening by registering an ErrorObserver object through errorManager.on('error').

It is recommended to implement both callback methods to obtain complete exception information.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| errObject | Error | Yes| Event name, message, and error stack of the exception.|

**Example**

```ts
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observer: errorManager.ErrorObserver = {
  onUnhandledException(errObject) {
    console.error('onUnhandledException, errObject: ', errObject);
  },
  onException(errorObj) {
    console.error('onException, name: ', errorObj.name);
    console.error('onException, message: ', errorObj.message);
    if (typeof (errorObj.stack) === 'string') {
      console.error('onException, stack: ', errorObj.stack);
    }
  }
};

try {
  errorManager.on('error', observer);
} catch (error) {
  console.error(`registerErrorObserver failed, error.code: ${(error as BusinessError).code}, error.message: ${(error as BusinessError).message}`);
}
```
