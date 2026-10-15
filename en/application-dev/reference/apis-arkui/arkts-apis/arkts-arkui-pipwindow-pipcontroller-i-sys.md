# PiPController

```TypeScript
interface PiPController
```

Implements a PiP controller that starts, stops, or updates a PiP window and registers callbacks.

Before calling any of the following APIs, you must use [PiPWindow.create()](arkts-arkui-pipwindow-create-f.md#create1) to create a PiPController instance.

**Since:** 11

<!--Device-PiPWindow-interface PiPController--><!--Device-PiPWindow-interface PiPController-End-->

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { PiPWindow } from '@kit.ArkUI';
```

## isPiPSupported

```TypeScript
isPiPSupported(): boolean
```

Returns a Boolean value that indicates whether picture-in-picture is supported

**Since:** 18

<!--Device-PiPController-isPiPSupported(): boolean--><!--Device-PiPController-isPiPSupported(): boolean-End-->

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | True if picture-in-picture is supported, otherwise false |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. Interface caller is not a system app. |
| [1300014](../errorcode-window.md#1300014-pip-internal-error) | PiP internal error. |
