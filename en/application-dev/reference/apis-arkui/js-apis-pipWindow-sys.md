# @ohos.PiPWindow (PiP Window) (System API)
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @betafringe007-->
<!--Designer: @taoweihua-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

The module provides basic APIs for manipulating Picture in Picture (PiP). For example, you can use the APIs to check whether the PiP feature is supported and create a PiP controller to start or stop a PiP window. In this way, users can continue watching videos in a small window while performing other operations, improving multitasking efficiency. It is applicable to video playback, video calls, and video conferences.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - Before <!--RP2-->OpenHarmony 6.0<!--RP2End-->, the PiP feature is supported only on phones and tablets. Starting from <!--RP2-->OpenHarmony 6.0<!--RP2End-->, the PiP feature is supported on phones, PCs/2-in-1 devices, tablets, but is unavailable on all other devices.
>
> - For the system capability SystemCapability.Window.SessionManager, use [canIUse()](../common/js-apis-syscap.md#caniuse) to check whether the device supports this system capability and the corresponding APIs.
>
> - This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.PiPWindow (PiP Window)](js-apis-pipWindow.md).

## Modules to Import

```ts
import { PiPWindow } from '@kit.ArkUI';
```

## PiPController

Implements a PiP controller that starts, stops, or updates a PiP window and registers callbacks.

In the following API examples, you need to call [PiPWindow.create()](js-apis-pipWindow.md#pipwindowcreate) to obtain a PiPController instance and then call the corresponding APIs through this instance.

**System capability**: SystemCapability.Window.SessionManager

### isPiPSupported<sup>18+</sup>

isPiPSupported(): boolean

Checks whether the current device supports the PiP feature. Before starting the PiP window, you are advised to call this API to check whether the device supports the PiP feature. This prevents functionality exceptions caused by calling PiP-related APIs on devices that do not support the PiP feature.

**System API**: This is a system API.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 18

**Return value**

| Type     | Description                                 |
|----------|-------------------------------------|
| boolean  | Whether the current device supports the PiP feature. **true** if supported, **false** otherwise.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Window Error Codes](errorcode-window.md).

| ID| Error Message                                   |
|-------|---------------------------------------------|
| 202   | Not System App. Interface caller is not a system app. |
| 1300014    | PiP internal error.                                    |

**Example**

```ts
try {
  if (!this.pipController) {
    return;
  }
  // Obtain pipController using PiPWindow.create().
  // Check whether the current device supports the PiP feature.
  let isSupported: boolean = this.pipController!.isPiPSupported();
  console.info('isPiPSupported: ' + isSupported);
} catch (exception) {
  console.error(`Failed to check if pip is supported. Code: ${exception.code}, message: ${exception.message}`);
}
```
