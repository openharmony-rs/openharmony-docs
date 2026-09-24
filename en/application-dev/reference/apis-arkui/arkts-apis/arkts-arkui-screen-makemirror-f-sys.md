# makeMirror (System API)

## Modules to Import

```TypeScript
import { screen } from '@kit.ArkUI';
```

## makeMirror

```TypeScript
function makeMirror(mainScreen:number, mirrorScreen:Array<number>, callback: AsyncCallback<number>): void
```

Sets the screen to mirror mode. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mainScreen | number | Yes | ID of the primary screen. The ID must be a non-negative integer. |
| mirrorScreen | Array&lt;number&gt; | Yes | Array of IDs of secondary screens. Each ID must be a positive integer. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the group ID of the secondary screens, where the ID is a positive integer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1400001](../errorcode-display.md#1400001-invalid-display-or-screen) | Invalid display or screen. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the screen ID using getAllScreens().
let mainScreenId: number = 0; // Main screen ID.
let mirrorScreenIds: Array<number> = [1, 2, 3]; // ID array of mirrored screens.
// Set the screen to mirror mode.
screen.makeMirror(mainScreenId, mirrorScreenIds, (err: BusinessError, data: number) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to set screen mirroring. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in setting screen mirroring. Data: ${data}`);
});
```


<a id="makemirror-1"></a>

## makeMirror

```TypeScript
function makeMirror(mainScreen:number, mirrorScreen:Array<number>): Promise<number>
```

Sets the screen to mirror mode. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mainScreen | number | Yes | ID of the primary screen. The ID must be a non-negative integer. |
| mirrorScreen | Array&lt;number&gt; | Yes | Array of IDs of secondary screens. Each ID must be a positive integer. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the group ID of the secondary screens, where the ID is a positive integer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1400001](../errorcode-display.md#1400001-invalid-display-or-screen) | Invalid display or screen. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the screen ID using getAllScreens().
let mainScreenId: number = 0; // Main screen ID.
let mirrorScreenIds: Array<number> = [1, 2, 3]; // ID array of mirrored screens.
// Set the screen to mirror mode.
screen.makeMirror(mainScreenId, mirrorScreenIds).then((data: number) => {
  console.info(`Succeeded in setting screen mirroring. Data: ${data}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set screen mirroring. Code: ${err.code}, message: ${err.message}`);
});
```
