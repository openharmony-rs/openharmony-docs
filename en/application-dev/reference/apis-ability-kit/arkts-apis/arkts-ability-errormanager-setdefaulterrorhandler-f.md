# setDefaultErrorHandler

## Modules to Import

```TypeScript
import { errorManager } from '@kit.AbilityKit';
```

## setDefaultErrorHandler

```TypeScript
function setDefaultErrorHandler(defaultHandler?: ErrorHandler) : ErrorHandler
```

Returns the previously registered handler when a JavaScript crash exception occurs. It can only be used in the main thread.

If an invalid parameter is passed or the API is called from a child thread, an error code is thrown and **undefined** is returned. You are advised to handle it with try-catch logic.

If the API parameter is empty, subsequently registered handlers are not able to establish a connection with previously registered handlers, thereby breaking the chain call mechanism.

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| defaultHandler | [ErrorHandler](arkts-ability-errormanager-errorhandler-t.md) | No | Newly registered error handler. The default value is empty. |

**Return value:**

| Type | Description |
| --- | --- |
| [ErrorHandler](arkts-ability-errormanager-errorhandler-t.md) | Previously registered error handler. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000205](../errorcode-ability.md#16000205-api-not-called-in-main-thread) | The API is not called on the main thread. |

**Examples**

```TypeScript
import { errorManager } from '@kit.AbilityKit';
import { process } from '@kit.ArkTS';

let oldHandler: errorManager.ErrorHandler;
const errorHandler: errorManager.ErrorHandler = (reason: Error) => {
  // Custom errorHandler implementation logic.
  console.info('[Handler] Uncaught exception handler invoked.');
  if (oldHandler) {
      oldHandler(reason);
  } else {
      // Add a null check. If the value is null, exit synchronously.
      const processManager = new process.ProcessManager();
      processManager.exit(0);
  }
};
oldHandler = errorManager.setDefaultErrorHandler(errorHandler);
```
