# setSpecificSystemWindowZIndex (System API)

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## setSpecificSystemWindowZIndex

```TypeScript
function setSpecificSystemWindowZIndex(windowType: WindowType, zIndex: number): Promise<void>
```

Sets the z-level of a system window. This API uses a promise to return the result.

Adjusts the **zIndex** of all system windows of the specified type to the configured value. Before and after the adjustment, the relative z-level of these windows remains unchanged, and the focus window does not change. After the application is closed, the z-level of specified windows is restored to the default value.

You are advised to set different **zIndex** values for different types of windows. If there are windows with the same **zIndex**, the relative z-level of windows remains unchanged before and after the setting.

**Since:** 23

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| windowType | [WindowType](arkts-arkui-window-windowtype-e.md) | Yes | Window type. Only the following types are supported: **TYPE_WALLET_SWIPE_CARD**, **TYPE_VOICE_INTERACTION**, **TYPE_SCREENSHOT**, **TYPE_SCREEN_CONTROL**, **TYPE_FLOAT_NAVIGATION**, and **TYPE_MUTISCREEN_COLLABORATION**. |
| zIndex | number | Yes | Z-level of the system window. The value must be an integer. Floating-point numbers are rounded down. The value **0** or a negative number will place the window below the home screen. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, non-system application uses system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. |

**Examples**

```TypeScript
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
try {
  window.setSpecificSystemWindowZIndex(window.WindowType.TYPE_WALLET_SWIPE_CARD, 200).then(() => {
    console.info('Succeeded in setting zIndex');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set zIndex. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set zIndex. Cause code: ${exception.code}, message: ${exception.message}`);
}
```
