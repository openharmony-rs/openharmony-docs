# getWindowsByCoordinate

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## getWindowsByCoordinate

```TypeScript
function getWindowsByCoordinate(displayId: number, windowNumber?: number, x?: number, y?: number):
      Promise<Array<Window>>
```

Obtains visible windows at the specified coordinates within the current application, sorted by their current layer order. The window at the topmost layer corresponds to index 0 of the array. This API uses a promise to return the result.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| displayId | number | Yes | ID of the display where the windows are located. The value must be an integer. If a non -integer is passed, the decimal part is ignored. The value can be obtained from [WindowProperties](arkts-arkui-window-windowproperties-i.md). |
| windowNumber | number | No | Number of windows to obtain. The value must be an integer greater than 0. If a non- integer is passed, the decimal part is ignored. If this parameter is not set or is less than or equal to 0, all windows that meet the conditions are returned. |
| x | number | No | X coordinate, with the top-left corner of the screen used as the origin. The value must be a non-negative integer. If a non-integer is passed, the decimal part is ignored. If this parameter is not set or is less than 0, all visible windows are returned. |
| y | number | No | Y coordinate, with the top-left corner of the screen used as the origin. The value must be a non-negative integer. If a non-integer is passed, the decimal part is ignored. If this parameter is not set or is less than 0, all visible windows are returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[Window](arkts-arkui-window-window-i.md)&gt;&gt; | Promise used to return an array of window objects. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: Internal task error. |
