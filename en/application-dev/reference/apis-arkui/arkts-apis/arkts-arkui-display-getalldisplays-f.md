# getAllDisplays

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## getAllDisplays

```TypeScript
function getAllDisplays(callback: AsyncCallback<Array<Display>>): void
```

Obtains all Display objects. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[Display](arkts-arkui-display-display-i.md)&gt;&gt; | Yes | Callback used to return all the Display objects. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1400001](../errorcode-display.md#1400001-invalid-display-or-screen) | Invalid display or screen. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let displayClass: Array<display.Display> = [];
display.getAllDisplays((err: BusinessError, data: Array<display.Display>) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to obtain all the display objects. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  displayClass = data;
  console.info(`Succeeded in obtaining all the display objects. Data: ${JSON.stringify(data)}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let displayClass: Array<display.Display> = [];
let promise: Promise<Array<display.Display>> = display.getAllDisplays();
promise.then((data: Array<display.Display>) => {
  displayClass = data;
  console.info(`Succeeded in obtaining all the display objects. Data:  ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain all the display objects. Code: ${err.code}, message: ${err.message}`);
});
```


## getAllDisplays

```TypeScript
function getAllDisplays(): Promise<Array<Display>>
```

Obtains all Display objects. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[Display](arkts-arkui-display-display-i.md)&gt;&gt; | Promise used to return all the Display objects. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1400001](../errorcode-display.md#1400001-invalid-display-or-screen) | Invalid display or screen. |

**Examples**

See [getAllDisplays](#getalldisplays)
