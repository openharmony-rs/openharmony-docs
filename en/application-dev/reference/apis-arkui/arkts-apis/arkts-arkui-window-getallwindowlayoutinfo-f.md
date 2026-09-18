# getAllWindowLayoutInfo

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## getAllWindowLayoutInfo

```TypeScript
function getAllWindowLayoutInfo(displayId: number): Promise<Array<WindowLayoutInfo>>
```

Obtains the layout information array of all windows visible on a display. The layout information is arranged based on the current window stacking order, and the topmost window in the hierarchy is at index 0 of the array. This API uses a promise to return the result.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| displayId | number | Yes | ID of the display where the windows are located. The value must be an integer and can be obtained from [WindowProperties](arkts-arkui-window-windowproperties-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[WindowLayoutInfo](arkts-arkui-window-windowlayoutinfo-i.md)&gt;&gt; | Promise used to return an array of window layout information objects. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function getAllWindowLayoutInfo can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal.<br>**Applicable version:** 15 - 18 |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: Internal task error. |


## getAllWindowLayoutInfo

```TypeScript
function getAllWindowLayoutInfo(displayId: number, option?: WindowInfoOptions): Promise<Array<WindowLayoutInfo>>
```

Obtains the array of window layout info visible on a specified screen. The width and height of each rect are calculated after scaling. The array is sorted by the current window level. The index of the array corresponding to the highest level is 0.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| displayId | number | Yes | Indicate the id of display. |
| option | [WindowInfoOptions](arkts-arkui-window-windowinfooptions-i.md) | No | Filter criteria for window information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[WindowLayoutInfo](arkts-arkui-window-windowlayoutinfo-i.md)&gt;&gt; | Promise used to return the WindowLayoutInfo. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function getAllWindowLayoutInfo can not work correctly due to limited device capabilities. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: Internal task error. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: 1. Invalid parameter range. |
