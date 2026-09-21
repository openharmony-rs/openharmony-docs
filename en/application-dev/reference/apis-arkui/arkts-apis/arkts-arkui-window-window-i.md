# Window

```TypeScript
interface Window
```

Represents a window instance, which is the basic unit managed by the window manager.

In the following API examples, you must use [getLastWindow()](arkts-arkui-window-getlastwindow-f.md), [createWindow()](arkts-arkui-window-createwindow-f.md), or [findWindow()](arkts-arkui-window-findwindow-f.md) to obtain a Window instance (named windowClass in this example) and then call a method in this instance.

**Since:** 6

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## clearWindowMask

```TypeScript
clearWindowMask(): Promise<void>
```

Clear the window mask of window

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. Internal task error. 3. The window has not set window mask yet. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only subwindows and float windows are supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
  let maskWidth = windowClass.getWindowProperties().windowRect.width;
  let maskHeight = windowClass.getWindowProperties().windowRect.height;
  let windowMask = Array<Array<number>>(maskHeight).fill([]).map((_, row) => {
    let array = Array<number>(maskWidth);
    for (let i = 0 ; i < maskWidth; i++) {
      array[i] = (i + row) > (maskWidth + maskHeight) / 2 ? 1 : 0;
    }
    return array;
  });
  windowClass.setWindowMask(windowMask).then(() => {
    console.info('Succeeded in setting the window mask.');
    windowClass?.clearWindowMask().then(() => {
      console.info('Succeeded in clearing the window mask.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to clear window mask. Cause code: ${err.code}, message: ${err.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`Failed to set window mask. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set or clear the window mask. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## clientToGlobalDisplay

```TypeScript
clientToGlobalDisplay(winX: number, winY: number): Position
```

Converts relative coordinates (based on the top-left corner of the current window) into global coordinates (based on the top-left corner of the primary screen).

This API is not supported in windows that are subject to display scaling, such as floating windows on phones or tablets not in free windows mode.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| winX | number | Yes | Offset along the X-axis, in pixels, with the top-left corner of the current window as the origin. A positive value moves the window to the right; a negative value moves it to the left. The value must be an integer. Non-integer values are rounded down. |
| winY | number | Yes | Offset along the Y-axis, in pixels, with the top-left corner of the current window as the origin. A positive value moves the window downward; a negative value moves it upward. The value must be an integer. Non-integer values are rounded down. |

**Return value:**

| Type | Description |
| --- | --- |
| [Position](arkts-arkui-window-position-i.md) | Coordinates after conversion. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300010](../errorcode-window.md#1300010-unsupported-operation-in-the-current-window-mode) | The operation in the current window status is invalid. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: 1. Invalid parameter range. |

**Examples**

```TypeScript
try {
  let position = windowClass.clientToGlobalDisplay(100, 100);
  console.info(`Succeeded in converting the position in the current window to the position in global display. Position: ` + JSON.stringify(position));
} catch (exception) {
  console.error(`Failed to convert the position. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## convertOrientationAndRotation

```TypeScript
convertOrientationAndRotation(from: RotationInfoType, to: RotationInfoType, value: number): number
```

Enables conversion between window orientation, screen orientation, and screen angle.

Window orientation refers to the direction of the screen where the window resides, using the Window module's definitions for portrait and landscape modes. Window orientations are represented by the digits 0, 1, 2, and 3, corresponding to portrait, reverse landscape, reverse portrait, and landscape, respectively. These definitions match those in [RotationChangeInfo](arkts-arkui-window-rotationchangeinfo-i.md) and the [Orientation](arkts-arkui-window-orientation-e.md) enum. For example, setting **Orientation** to **LANDSCAPE** indicates a landscape window orientation.  
> **NOTE:** 
> 
> The following figure and table show the relationship between the window orientation, screen orientation, and
> screen angle of a bar-type device.
> 
>  &gt;

| Screen Angle| Screen Orientation| Window Orientation|  
| ------- | ------- | ------- |  
| 0 | [PORTRAIT](arkts-arkui-window-orientation-e.md) | [PORTRAIT](arkts-arkui-window-orientation-e.md) |
| 90 | [LANDSCAPE](arkts-arkui-window-orientation-e.md) | [LANDSCAPE_INVERTED](arkts-arkui-window-orientation-e.md) |
| 180 | [PORTRAIT_INVERTED](arkts-arkui-window-orientation-e.md) | [PORTRAIT_INVERTED](arkts-arkui-window-orientation-e.md) |
| 270 | [LANDSCAPE_INVERTED](arkts-arkui-window-orientation-e.md) | [LANDSCAPE](arkts-arkui-window-orientation-e.md) |

**Since:** 23

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| from | [RotationInfoType](arkts-arkui-window-rotationinfotype-e.md) | Yes | Type of the value to convert. |
| to | [RotationInfoType](arkts-arkui-window-rotationinfotype-e.md) | Yes | Type of the target value. |
| value | number | Yes | Value to convert. The value is an integer. If a floating-point number is entered, the value is rounded down. The value range is [0, 3]. If the value is out of the range, it is an invalid parameter (error code [401](../../../reference/errorcode-universal.md#401-parameter-check-failed) is thrown). |

**Return value:**

| Type | Description |
| --- | --- |
| number | Converted value of the target type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
try {
  let originalValue: number = 0;
  let fromType: window.RotationInfoType = window.RotationInfoType.WINDOW_ORIENTATION;
  let toType: window.RotationInfoType = window.RotationInfoType.DISPLAY_ORIENTATION;
  let convertedValue: number = windowClass.convertOrientationAndRotation(fromType, toType, originalValue);
  console.info(`Convert ${originalValue} of type: ${fromType} to ${convertedValue} of type: ${toType}`);
} catch (exception) {
  console.error(`Failed to convert orientation and rotation between window and display. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## createSubWindowWithOptions

```TypeScript
createSubWindowWithOptions(name: string, options: SubWindowOptions): Promise<Window>
```

Creates a child window under the main window, another child window, or floating window. This API uses a promise to return the result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the child window. |
| options | [SubWindowOptions](arkts-arkui-window-subwindowoptions-i.md) | Yes | Parameters used for creating the child window. If **decorEnabled** is set to true, the child window does not use an [immersive layout](../../../windowmanager/window-terminology.md#immersive-layout). If **decorEnabled** is set to **false**, the child window uses an immersive layout. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Window](arkts-arkui-window-window-i.md)&gt; | Promise used to used to return the child window created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error; 3. The subWindow has been created and cannot be created again. 4. It is not allowed to create non-secure window when secure extension exists. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: 1. Invalid window type. Only main windows, subwindows, and floating windows are supported; 2. When SubWindowOptions.zLevelAboveParentLoosened is true, only main windows are supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let options : window.SubWindowOptions = {
    title: 'title',
    decorEnabled: true,
    isModal: true
  };
  let promise = windowClass.createSubWindowWithOptions('mySubWindow', options);
  promise.then((data) => {
    console.info(`Succeeded in creating the subwindow. Data: ${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to create the subwindow. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to create the subwindow. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## destroy

```TypeScript
destroy(callback: AsyncCallback<void>): void
```

Destroys this window. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [destroyWindow](#destroywindow)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

windowClass.destroy((err: BusinessError) => {
  const errCode: number = err.code;
  if (err.code) {
    console.error(`Failed to destroy the window. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in destroying the window.');
});
```

<a id="destroy-1"></a>

## destroy

```TypeScript
destroy(): Promise<void>
```

Destroys this window. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [destroyWindow](#destroywindow)()

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = windowClass.destroy();
promise.then(() => {
  console.info('Succeeded in destroying the window.');
}).catch((err: BusinessError) => {
  console.error(`Failed to destroy the window. Cause code: ${err.code}, message: ${err.message}`);
});
```

## destroyWindow

```TypeScript
destroyWindow(callback: AsyncCallback<void>): void
```

Destroys this window. This API uses an asynchronous callback to return the result. It takes effect for a system window, an application child window, a global floating window, or a modal window.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally.<br>**Applicable version:** 9 |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

windowClass.destroyWindow((err) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to destroy the window. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in destroying the window.');
});
```

<a id="destroywindow-1"></a>

## destroyWindow

```TypeScript
destroyWindow(): Promise<void>
```

Destroys this window. This API uses a promise to return the result. It takes effect for a system window, an application child window, a global floating window, or a modal window.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally.<br>**Applicable version:** 9 |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = windowClass.destroyWindow();
promise.then(() => {
  console.info('Succeeded in destroying the window.');
}).catch((err: BusinessError) => {
  console.error(`Failed to destroy the window. Cause code: ${err.code}, message: ${err.message}`);
});
```

## disableLandscapeMultiWindow

```TypeScript
disableLandscapeMultiWindow(): Promise<void>
```

Disables the landscape multi-window mode for the UI page that supports the horizontal layout.

This API takes effect only for the main window of the application. In addition, **preferMultiWindowOrientation** must be set to **landscape_auto** in the [abilities](../../../quick-start/module-configuration-file.md#abilities) tag in the **module.json5** file.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: Internal task error. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let promise = windowClass.disableLandscapeMultiWindow();
      promise.then(() => {
        console.info('Succeeded in making multi-window become not landscape.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to make multi-window become not landscape. Cause code: ${err.code}, message: ${err.message}`);
      });
    });
  }
}
```

## enableDrag

```TypeScript
enableDrag(enable: boolean): Promise<void>
```

Enables or disables window dragging. This API takes effect only for system windows, application child windows, global floating windows, and modal windows. This API uses a promise to return the result.

After window dragging is enabled, the window can be resized using the mouse or touch operations.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | The value true means to enable window dragging, and false means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 14 - 19 |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: 1.Invalid window type. Only system windows, application child windows, global floating windows and modal windows are supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  windowClass.enableDrag(true).then(() => {
    console.info('succeeded in setting window draggable');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set window draggable. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set window draggable. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## enableLandscapeMultiWindow

```TypeScript
enableLandscapeMultiWindow(): Promise<void>
```

Enables the landscape multi-window mode for the UI page that supports the horizontal layout. You are not advised to call this API for the UI page that adopts the vertical layout.

This API takes effect only for the main window of the application. In addition, **preferMultiWindowOrientation** must be set to **landscape_auto** in the [abilities](../../../quick-start/module-configuration-file.md#abilities) tag in the **module.json5** file.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: Internal task error. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let promise = windowClass.enableLandscapeMultiWindow();
      promise.then(() => {
        console.info('Succeeded in making multi-window become landscape.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to make multi-window become landscape. Cause code: ${err.code}, message: ${err.message}`);
      });
    });
  }
}
```

## getAvoidArea

```TypeScript
getAvoidArea(type: AvoidAreaType, callback: AsyncCallback<AvoidArea>): void
```

Obtains the area where this window cannot be displayed, for example, the system bar area, notch, gesture area, and soft keyboard area. This API uses an asynchronous callback to return the result.

Main window/Child window:

- In the free-floating window mode under the [freeform window](../../../windowmanager/window-terminology.md#freeform-window) state (the window mode is **window.WindowStatusType.FLOATING**), only the avoidance area of the fixed soft keyboard type ([AvoidAreaType](arkts-arkui-window-avoidareatype-e.md) is **TYPE_KEYBOARD**) is available.  
- In the free-floating window mode of the main window in the non-freeform window state, only the avoidance area  
of the system bar type ([AvoidAreaType](arkts-arkui-window-avoidareatype-e.md) is **TYPE_SYSTEM**) is available.  
- In other scenarios, this API can be called to obtain the calculated avoidance area only when the main window is  
not in the free-floating window mode or the device type is phone or tablet. Otherwise, the obtained avoidance area is empty.  
- For the child window in the non-freeform window state or non-free-floating window mode, this API can be called  
to obtain the calculated avoidance area only when the position and size of the child window are the same as those of the main window. Otherwise, the obtained avoidance area is empty.

Global floating window, modal window, or system window:

- This API can be called to obtain the avoidance area only after [setSystemAvoidAreaEnabled](#setsystemavoidareaenabled) is called. Otherwise, the obtained avoidance area is empty.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getWindowAvoidArea](#getwindowavoidarea)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [AvoidAreaType](arkts-arkui-window-avoidareatype-e.md) | Yes | Type of the area. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AvoidArea](arkts-arkui-window-avoidarea-i.md)&gt; | Yes | Callback used to return the area. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let type = window.AvoidAreaType.TYPE_SYSTEM;
windowClass.getAvoidArea(type, (err: BusinessError, data) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to obtain the area. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in obtaining the area. Data:' + JSON.stringify(data));
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let type = window.AvoidAreaType.TYPE_SYSTEM;
let promise = windowClass.getAvoidArea(type);
promise.then((data) => {
  console.info('Succeeded in obtaining the area. Data:' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the area. Cause code: ${err.code}, message: ${err.message}`);
});
```

<a id="getavoidarea-1"></a>

## getAvoidArea

```TypeScript
getAvoidArea(type: AvoidAreaType): Promise<AvoidArea>
```

Obtains the area where this window cannot be displayed, for example, the system bar area, notch, gesture area, and soft keyboard area. This API uses an asynchronous callback to return the result.

Main window/Child window:

- In the free-floating window mode under the [freeform window](../../../windowmanager/window-terminology.md#freeform-window) state (the window mode is **window.WindowStatusType.FLOATING**), only the avoidance area of the fixed soft keyboard type ([AvoidAreaType](arkts-arkui-window-avoidareatype-e.md) is **TYPE_KEYBOARD**) is available.  
- In the free-floating window mode of the main window in the non-freeform window state, only the avoidance area  
of the system bar type ([AvoidAreaType](arkts-arkui-window-avoidareatype-e.md) is **TYPE_SYSTEM**) is available.  
- In other scenarios, this API can be called to obtain the calculated avoidance area only when the main window is  
not in the free-floating window mode or the device type is phone or tablet. Otherwise, the obtained avoidance area is empty.  
- For the child window in the non-freeform window state or non-free-floating window mode, this API can be called  
to obtain the calculated avoidance area only when the position and size of the child window are the same as those of the main window. Otherwise, the obtained avoidance area is empty.

Global floating window, modal window, or system window:

- This API can be called to obtain the avoidance area only after [setSystemAvoidAreaEnabled](#setsystemavoidareaenabled) is called. Otherwise, the obtained avoidance area is empty.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getWindowAvoidArea](#getwindowavoidarea)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [AvoidAreaType](arkts-arkui-window-avoidareatype-e.md) | Yes | Type of the area. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AvoidArea](arkts-arkui-window-avoidarea-i.md)&gt; | Promise used to return the area. |

**Examples**

See [getAvoidArea](#getavoidarea)

## getColorSpace

```TypeScript
getColorSpace(): Promise<ColorSpace>
```

Obtains the color space of this window. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getWindowColorSpace](#getwindowcolorspace)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ColorSpace](arkts-arkui-window-colorspace-e.md)&gt; | Promise used to return the current color space. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = windowClass.getColorSpace();
promise.then((data) => {
  console.info('Succeeded in getting window color space. Cause:' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`Failed to get window colorspace. Cause code: ${err.code}, message: ${err.message}`);
});
```

<a id="getcolorspace-1"></a>

## getColorSpace

```TypeScript
getColorSpace(callback: AsyncCallback<ColorSpace>): void
```

Obtains the color space of this window. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getWindowColorSpace](#getwindowcolorspace)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ColorSpace](arkts-arkui-window-colorspace-e.md)&gt; | Yes | Callback used to return the result. When the color space is obtained successfully, **err** is **undefined**, and **data** is the current color space. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

windowClass.getColorSpace((err: BusinessError, data) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to get window colorspace. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in getting window colorspace. Cause:' + JSON.stringify(data));
});
```

## getDecorButtonStyle

```TypeScript
getDecorButtonStyle(): DecorButtonStyle
```

Obtains the button style of the decoration bar. The setting takes effect only for the main window and child windows.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| [DecorButtonStyle](arkts-arkui-window-decorbuttonstyle-i.md) | Button style on the decoration bar of the current window. The decoration button area is located in the top-right corner of the window. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows and subwindows are supported. |

**Examples**

```TypeScript
try {
  let decorButtonStyle = windowClass.getDecorButtonStyle();
  console.info(`Succeeded in getting the style of button. Data: ${JSON.stringify(decorButtonStyle)}`);
} catch (exception) {
  console.error(`Failed to get the style of button. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## getGlobalRect

```TypeScript
getGlobalRect(): Rect
```

Obtains the actual display area of this window on the physical screen. This API returns the result synchronously.

This API can determine the actual on-screen location and size of a window that has been resized on certain devices.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| [Rect](arkts-arkui-window-rect-i.md) | A set of four values, which indicates the horizontal distance from the screen's top-left corner to the window's left edge, the vertical distance from the screen's top-left corner to the window's top edge, the width of the window after scaling, and the height of the window after scaling. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. Failed to convert result into JS value object. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
try {
  let rect = windowClass.getGlobalRect();
  console.info(`Succeeded in getting window rect: ` + JSON.stringify(rect));
} catch (exception) {
  console.error(`Failed to get window rect. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## getImmersiveModeEnabledState

```TypeScript
getImmersiveModeEnabledState(): boolean
```

Checks whether the immersive layout is enabled for this window.

This API can be called only by the main window and child windows.

The return value is consistent with the settings applied via [setImmersiveModeEnabledState()](#setimmersivemodeenabledstate) and [setWindowLayoutFullScreen()](#setwindowlayoutfullscreen-1). If neither of these APIs has been called, the default return value is **false**.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | The value true means the immersive mode is enabled, and false means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows and subwindows are supported. |

**Examples**

```TypeScript
try {
  let isEnabled = windowClass.getImmersiveModeEnabledState();
} catch (exception) {
  console.error(`Failed to get the window immersive mode enabled status. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## getParentWindow

```TypeScript
getParentWindow(): Window
```

Obtains the parent window of this child window.

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| [Window](arkts-arkui-window-window-i.md) | Parent window. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Not called from subWindow. |
| [1300009](../errorcode-window.md#1300009-invalid-parent-window) | The parent window is invalid. |

**Examples**

```TypeScript
try {
  let windowClass: window.Window = window.findWindow("subWindow");
  let parentWindow: window.Window = windowClass.getParentWindow();
  let properties = parentWindow.getWindowProperties();
  console.info(`Succeeded in obtaining parent window properties. Property: ${JSON.stringify(properties)}`);
} catch (exception) {
  console.error(`Failed to get the parent window. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## getPreferredOrientation

```TypeScript
getPreferredOrientation(): Orientation
```

Obtains the orientation of the window. If no orientation is specified, **window.Orientation.UNSPECIFIED** is returned.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Orientation](arkts-arkui-window-orientation-e.md) | Display orientation. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      try {
        let orientation = windowClass.getPreferredOrientation();
      } catch (exception) {
        console.error(`Failed to get window orientation. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
};
```

## getProperties

```TypeScript
getProperties(callback: AsyncCallback<WindowProperties>): void
```

Obtains the properties of this window. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [getWindowProperties](#getwindowproperties)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[WindowProperties](arkts-arkui-window-windowproperties-i.md)&gt; | Yes | Callback used to return the window properties. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

windowClass.getProperties((err: BusinessError, data) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to obtain the window properties. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in obtaining the window properties. Data: ' + JSON.stringify(data));
});
```

<a id="getproperties-1"></a>

## getProperties

```TypeScript
getProperties(): Promise<WindowProperties>
```

Obtains the properties of this window. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [getWindowProperties](#getwindowproperties)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[WindowProperties](arkts-arkui-window-windowproperties-i.md)&gt; | Promise used to return the window properties. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = windowClass.getProperties();
promise.then((data) => {
  console.info('Succeeded in obtaining the window properties. Data: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the window properties. Cause code: ${err.code}, message: ${err.message}`);
});
```

## getStatusBarProperty

```TypeScript
getStatusBarProperty(): StatusBarProperty
```

Obtains the properties (for example, text color) of the status bar in the main window.

Calling this API is not supported for child window and will cause error code 1300004.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| [StatusBarProperty](arkts-arkui-window-statusbarproperty-i.md) | Status bar properties, such as its color. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. Internal task error. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows are supported. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage) {
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      try {
        let statusBarProperty = windowClass.getStatusBarProperty();
        console.info('Succeeded in obtaining system bar properties. Property: ' + JSON.stringify(statusBarProperty));
      } catch (err) {
        console.error(`Failed to get system bar properties. Code: ${err.code}, message: ${err.message}`);
      }
    });
  }
};
```

## getSubWindowZLevel

```TypeScript
getSubWindowZLevel(): number
```

Obtains the z-level of the current child window. This API cannot be called by the main window or system window.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| number | Z-level of the child window. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function getSubWindowZLevel can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only subwindows are supported. |

**Examples**

```TypeScript
// EntryAbility.ets
import { window } from '@kit.ArkUI';
import { UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let subWindowZLevel = -1;
    // Create a child window.
    windowStage.createSubWindow('testSubWindow').then((subWindow) => {
      if (subWindow == null) {
        console.error('Failed to create the sub window. Cause: The sub window is null');
        return;
      }
      try {
        subWindowZLevel = subWindow.getSubWindowZLevel();
        console.info(`Succeeded in obtaining sub window zLevel: ${subWindowZLevel}`);
      } catch (err) {
        console.error(`Failed to obtain the sub window zLevel. Cause code: ${err.code}, message: ${err.message}`);
      }
    });
  }
}
```

## getTitleButtonRect

```TypeScript
getTitleButtonRect(): TitleButtonRect
```

Obtains the rectangle that holds the minimize, maximize, and close buttons on the title bar of the main window or the decorated child window.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| [TitleButtonRect](arkts-arkui-window-titlebuttonrect-i.md) | Rectangle obtained, which is located in the top-right corner of the window. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      try {
        let titleButtonArea = windowClass.getTitleButtonRect();
        console.info('Succeeded in obtaining the area of title buttons. Data: ' + JSON.stringify(titleButtonArea));
      } catch (exception) {
        console.error(`Failed to get the area of title buttons. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

## getUIContext

```TypeScript
getUIContext() : UIContext
```

Obtains a UIContext instance.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | UIContext instance obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { window, UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // Load content for the main window.
    windowStage.loadContent("pages/page2", (err: BusinessError) => {
      let errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('Succeeded in loading the content.');
      // Obtain the main window.
      let windowClass: window.Window | undefined = undefined;
      windowStage.getMainWindow((err: BusinessError, data) => {
        let errCode: number = err.code;
        if (errCode) {
          console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        windowClass = data;
        console.info('Succeeded in obtaining the main window. Data: ' + JSON.stringify(data));
        // Obtain a UIContext instance.
        let uiContext: UIContext | null = null;
        uiContext = windowClass.getUIContext();
      });
    });
  }
};
```

## getWindowAvoidArea

```TypeScript
getWindowAvoidArea(type: AvoidAreaType): AvoidArea
```

Obtains the avoid area of this window.

Main window/Child window:

- In the free-floating window mode under the [freeform window](../../../windowmanager/window-terminology.md#freeform-window) state (the window mode is **window.WindowStatusType.FLOATING**), only the avoidance area of the fixed soft keyboard type ([AvoidAreaType](arkts-arkui-window-avoidareatype-e.md) is **TYPE_KEYBOARD**) is available.  
- In the free-floating window mode of the main window in the non-freeform window state, only the avoidance area  
of the system bar type ([AvoidAreaType](arkts-arkui-window-avoidareatype-e.md) is **TYPE_SYSTEM**) is available.  
- In other scenarios, this API can be called to obtain the calculated avoidance area only when the main window is  
not in the free-floating window mode or the device type is phone or tablet. Otherwise, the obtained avoidance area is empty.  
- For the child window in the non-freeform window state or non-free-floating window mode, this API can be called  
to obtain the calculated avoidance area only when the position and size of the child window are the same as those of the main window. Otherwise, the obtained avoidance area is empty.

Global floating window, modal window, or system window:

- This API can be called to obtain the avoidance area only after [setSystemAvoidAreaEnabled](#setsystemavoidareaenabled) is called. Otherwise, the obtained avoidance area is empty.

This API is generally applicable to the following scenarios:

- In the [onWindowStageCreate()](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md#onwindowstagecreate) callback, this  
API is used to obtain the initial layout avoid area when the application starts.  
- This API is used when a child window needs to temporarily display content and requires layout adjustments to  
avoid certain areas.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [AvoidAreaType](arkts-arkui-window-avoidareatype-e.md) | Yes | Type of the area |

**Return value:**

| Type | Description |
| --- | --- |
| [AvoidArea](arkts-arkui-window-avoidarea-i.md) | Area where the window cannot be displayed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Convert avoid area failed. |

**Examples**

```TypeScript
let type = window.AvoidAreaType.TYPE_SYSTEM;
try {
  let avoidArea = windowClass.getWindowAvoidArea(type);
} catch (exception) {
  console.error(`Failed to obtain the area. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## getWindowAvoidAreaIgnoringVisibility

```TypeScript
getWindowAvoidAreaIgnoringVisibility(type: AvoidAreaType): AvoidArea
```

Obtains the avoid area of this application window, even if the avoid area is invisible.

Main window/Child window:

- When the main window is in the free-floating window mode under a non-[freeform window](../../../windowmanager/window-terminology.md#freeform-window) state (the window mode is **window.WindowStatusType.FLOATING**), only the avoidance area of the system bar type ([AvoidAreaType](arkts-arkui-window-avoidareatype-e.md) is **TYPE_SYSTEM**) is available.  
- In other scenarios, this API can be called to obtain the calculated avoidance area only when the main window is  
not in the free-floating window mode or the device type is phone or tablet. Otherwise, the obtained avoidance area is empty.  
- For the child window in the non-freeform window state or non-free-floating window mode, this API can be called  
to obtain the calculated avoidance area only when the position and size of the child window are the same as those of the main window. Otherwise, the obtained avoidance area is empty.

Global floating window, modal window, or system window:

- This API can be called to obtain the avoidance area only after [setSystemAvoidAreaEnabled](#setsystemavoidareaenabled) is called. Otherwise, the obtained avoidance area is empty.

**Since:** 22

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [AvoidAreaType](arkts-arkui-window-avoidareatype-e.md) | Yes | Type of the area. |

**Return value:**

| Type | Description |
| --- | --- |
| [AvoidArea](arkts-arkui-window-avoidarea-i.md) | Area where the window cannot be displayed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Convert avoid area failed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: Invalid parameter range. |

**Examples**

```TypeScript
let type = window.AvoidAreaType.TYPE_SYSTEM;
try {
  let avoidArea = windowClass.getWindowAvoidAreaIgnoringVisibility(type);
} catch (exception) {
  console.error(`Failed to obtain the area. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## getWindowColorSpace

```TypeScript
getWindowColorSpace(): ColorSpace
```

Obtains the color space of this window.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| [ColorSpace](arkts-arkui-window-colorspace-e.md) | Color space obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let colorSpace = windowClass.getWindowColorSpace();
  console.info(`Succeeded in getting the window color space. ColorSpace: ${colorSpace}`);
} catch (exception) {
  console.error(`Failed to get the window color space. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## getWindowCornerRadius

```TypeScript
getWindowCornerRadius(): number
```

Obtains the radius of rounded corners of a child window or floating window. If [setWindowCornerRadius()](#setwindowcornerradius) is not called to set the radius of rounded corners, this API returns the default radius of rounded corners.

**Since:** 17

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| number | Radius of the rounded corner of the child window or floating window, measured in vp. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only subwindows and float windows are supported. |

**Examples**

```TypeScript
try {
  let cornerRadius = windowClass.getWindowCornerRadius();
} catch (exception) {
  console.error(`Failed to get corner radius. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## getWindowDecorHeight

```TypeScript
getWindowDecorHeight(): number
```

Obtains the height of the title bar of this window. This API takes effect for the window that has a title bar and a three-button area. In the stage model, this API must be used after the call of [loadContent](#loadcontent) or [setUIContent()](#setuicontent) takes effect.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| number | Height of the title bar. The value is an integer in the range [37,112]. The unit is vp. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |

**Examples**

```TypeScript
windowClass.setUIContent('pages/WindowPage').then(() => {
  try {
    let height = windowClass?.getWindowDecorHeight();
    console.info(`Succeeded in getting the height of window decor: ${height}`);
  } catch (exception) {
    console.error(`Failed to get the height of window decor. Cause code: ${exception.code}, message: ${exception.message}`);
  }
})
```

## getWindowDecorVisible

```TypeScript
getWindowDecorVisible(): boolean
```

Checks whether the title bar of this window is visible. In the stage model, this API must be used after the call of [loadContent](#loadcontent) or [setUIContent()](#setuicontent) takes effect.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether the title bar is visible. **true** if visible, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |

**Examples**

```TypeScript
let isVisible: boolean | undefined = undefined;
windowClass.setUIContent('pages/WindowPage').then(() => {
  try {
    isVisible = windowClass?.getWindowDecorVisible();
  } catch (exception) {
    console.error(`Failed to get the window decor visibility. Cause code: ${exception.code}, message: ${exception.message}`);
  }
})
```

## getWindowDensityInfo

```TypeScript
getWindowDensityInfo(): WindowDensityInfo
```

Obtains the display density information of this window.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| [WindowDensityInfo](arkts-arkui-window-windowdensityinfo-i.md) | Display density information of the window. If the return value is [-1, -1, -1], the current device does not support this API. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |

**Examples**

```TypeScript
try {
  let densityInfo = windowClass.getWindowDensityInfo();
} catch (exception) {
  console.error(`Failed to obtain the window densityInfo. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## getWindowLimits

```TypeScript
getWindowLimits(): WindowLimits
```

Obtains the size limits of this application window, in px.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| [WindowLimits](arkts-arkui-window-windowlimits-i.md) | Window size limits. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |

**Examples**

```TypeScript
try {
  let windowLimits = windowClass.getWindowLimits();
} catch (exception) {
  console.error(`Failed to obtain the window limits of window. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## getWindowLimitsVP

```TypeScript
getWindowLimitsVP(): WindowLimits
```

Obtains the size limits of this application window, in vp.

For system windows and global floating windows, the default minimum width and height are set to 1 px. The 1 vp value obtained via this API represents the result after rounding calculations.

**Since:** 22

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| [WindowLimits](arkts-arkui-window-windowlimits-i.md) | Window size limits. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |

**Examples**

```TypeScript
try {
  let windowLimits: window.WindowLimits = windowClass.getWindowLimitsVP();
} catch (exception) {
  console.error(`Failed to obtain the window limits. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## getWindowProperties

```TypeScript
getWindowProperties(): WindowProperties
```

Obtains the properties of this window.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| [WindowProperties](arkts-arkui-window-windowproperties-i.md) | Window properties obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |

**Examples**

```TypeScript
try {
  let properties = windowClass.getWindowProperties();
} catch (exception) {
  console.error(`Failed to obtain the window properties. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## getWindowStateSnapshot

```TypeScript
getWindowStateSnapshot(): Promise<string>
```

Get window state snapshot, including isPcMode information.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Window.SessionManager

**Test API:** This API is used only in automated test scripts.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the window state snapshot. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. Possible cause: The device does not support the API itself. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed; |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: The internal services of the window are not started normally. |

## getWindowStatus

```TypeScript
getWindowStatus(): WindowStatusType
```

Obtains the mode of this window.

> **NOTE:** 
> 
> In [freeform window](../../../windowmanager/window-terminology.md#freeform-window) mode, when the window is
> maximized (covering the entire screen, with a dock bar and status bar on 2-in-1 devices, and a status bar on
> tablets), the return value differs based on the
> [targetAPIVersion](../../../quick-start/app-configuration-file.md#tags-in-the-configuration-file) setting. For
> versions below 14, the return value is **WindowStatusType::FULL_SCREEN**. For versions 14 and above, the return
> value is **WindowStatusType::MAXIMIZE**.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| [WindowStatusType](arkts-arkui-window-windowstatustype-e.md) | Window mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |

**Examples**

```TypeScript
try {
  let windowStatusType = windowClass.getWindowStatus();
} catch (exception) {
  console.error(`Failed to obtain the window status of window. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## getWindowSystemBarProperties

```TypeScript
getWindowSystemBarProperties(): SystemBarProperties
```

Obtains the properties of the <!--Del-->three-button navigation bar and <!--DelEnd-->status bar in the main window.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| [SystemBarProperties](arkts-arkui-window-systembarproperties-i.md) | Properties of the<!--Del-->three-button navigation bar and <!--DelEnd-->status bar. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: Create js object failed. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows are supported. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      try {
        let systemBarProperty = windowClass.getWindowSystemBarProperties();
        console.info('Success in obtaining system bar properties. Property: ' + JSON.stringify(systemBarProperty));
      } catch (err) {
        console.error(`Failed to get system bar properties. Code: ${err.code}, message: ${err.message}`);
      }
    });
  }
};
```

## getWindowTransitionAnimation

```TypeScript
getWindowTransitionAnimation(transitionType: WindowTransitionType): TransitionAnimation | undefined
```

Obtains the window transition animation configuration in a specific scenario.

Currently, this API can be used only on the main window of an application.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transitionType | [WindowTransitionType](arkts-arkui-window-windowtransitiontype-e.md) | Yes | Scene of the transition animation. Currently, only the destruction scene is supported. |

**Return value:**

| Type | Description |
| --- | --- |
| [TransitionAnimation](arkts-arkui-window-transitionanimation-i.md) &#124; undefined | Transition animation configuration in the corresponding scene. If the [setWindowTransitionAnimation](#setwindowtransitionanimation) API is not used, undefined is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: 1. Invalid parameter range. |

**Examples**

```TypeScript
// EntryAbility.ets
import { BusinessError } from '@kit.BasicServicesKit';
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      try {
        let transitionAnimationResult = windowClass.getWindowTransitionAnimation(window.WindowTransitionType.DESTROY);
        console.info('Succeeded in getting window transition animation: ' + JSON.stringify(transitionAnimationResult));
      } catch (exception) {
        console.error(`Failed to obtain the window transition animation. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    })
  }
}
```

## globalDisplayToClient

```TypeScript
globalDisplayToClient(globalDisplayX: number, globalDisplayY: number): Position
```

Converts global coordinates (based on the top-left corner of the primary screen) into relative coordinates (based on the top-left corner of the current window).

This API is not supported in windows that are subject to display scaling, such as floating windows on phones or tablets not in free windows mode.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| globalDisplayX | number | Yes | Offset along the X-axis, in pixels, with the top-left corner of the current window as the origin. A positive value moves the window to the right; a negative value moves it to the left. The value must be an integer. Non-integer values are rounded down. |
| globalDisplayY | number | Yes | Offset along the Y-axis, in pixels, with the top-left corner of the current window as the origin. A positive value moves the window downward; a negative value moves it upward. The value must be an integer. Non-integer values are rounded down. |

**Return value:**

| Type | Description |
| --- | --- |
| [Position](arkts-arkui-window-position-i.md) | Coordinates after conversion. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300010](../errorcode-window.md#1300010-unsupported-operation-in-the-current-window-mode) | The operation in the current window status is invalid. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: 1. Invalid parameter range. |

**Examples**

```TypeScript
try {
  let position = windowClass.globalDisplayToClient(100, 100);
  console.info(`Succeeded in converting in the position in global display to the position in the current window. Position: ` + JSON.stringify(position));
} catch (exception) {
  console.error(`Failed to convert the position. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## isFloatNavigationAvoidAreaEnabled

```TypeScript
isFloatNavigationAvoidAreaEnabled(): boolean
```

Get whether the float navigation avoid area can be obtained.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| boolean | enable - If true, the float navigation avoid area can be obtained. If false, the float navigation avoid area can not be obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Create js value failed. |

**Examples**

```TypeScript
try {
  let isEnabled = windowClass.isFloatNavigationAvoidAreaEnabled();
} catch (exception) {
  console.error(`Failed to check if the window is enabled float navigation avoid area. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## isFocused

```TypeScript
isFocused(): boolean
```

Checks whether this window is focused.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether the window is focused. **true** if focused, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |

**Examples**

```TypeScript
try {
  let focus = windowClass.isFocused();
  console.info(`Succeeded in checking whether the window is focused. Data: ${focus}`);
} catch (exception) {
  console.error(`Failed to check whether the window is focused. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## isGestureBackEnabled

```TypeScript
isGestureBackEnabled(): boolean
```

Obtains whether the back gesture is enabled for the current window. This API can be successfully called only for the main window, and error code 1300004 is returned on other windows.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the back gesture feature is enabled. **true** if enabled, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows are supported. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;

      // Check whether the back gesture feature is enabled in the current window.
      try {
        let gestureBackEnabled: boolean = windowClass.isGestureBackEnabled();
        console.info(`Succeeded in obtaining gesture back enabled status: ${gestureBackEnabled}`);
      } catch (exception) {
        console.error(`Failed to get gesture back enabled status. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

## isImmersiveLayout

```TypeScript
isImmersiveLayout(): boolean
```

Checks whether this window is in immersive mode.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| boolean | The value true means that the layout is immersive, and false means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |

**Examples**

```TypeScript
try {
  let isEnabled = windowClass.isImmersiveLayout();
} catch (exception) {
  console.error(`Failed to check if the window layout is in immersive mode. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## isInFreeWindowMode

```TypeScript
isInFreeWindowMode(): boolean
```

Checks whether this window is in [freeform window](../../../windowmanager/window-terminology.md#freeform-window) mode.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether the window is in freeform window mode. **true** if the window is in freeform window mode, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
let isInFreeWindowMode: boolean = windowClass.isInFreeWindowMode();
console.info(`isInFreeWindowMode: ${isInFreeWindowMode}`);
```

## isInWindowPostureMode

```TypeScript
isInWindowPostureMode(mode: WindowPostureMode): boolean
```

Checks whether this window is in the specified window posture mode.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [WindowPostureMode](arkts-arkui-window-windowposturemode-e.md) | Yes | The window posture mode. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether this window is in the specified window posture mode. **true** if the window is in the specified window posture mode. **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: The internal services of the window are not started normally. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: Invalid parameter range. |

## isReceiveDragEventEnabled

```TypeScript
isReceiveDragEventEnabled(): boolean
```

Obtains whether the current window can receive [drag events](../arkts-components/arkts-arkui-common-comp-dragevent-i.md).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the current window can receive drag events.<br>**true** if the current window can receive drag events; **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function cannot work because the current device does not support this ability. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isReceiveDragEventEnabled = windowClass.isReceiveDragEventEnabled();
  console.info(`Succeeded in getting the window receiveDragEvent status: ${isReceiveDragEventEnabled}`);
} catch (exception) {
  console.error(`Failed to get the window receiveDragEvent status. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## isSeparationTouchEnabled

```TypeScript
isSeparationTouchEnabled(): boolean
```

Obtains whether the current window supports the event separation state.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the current window supports the event separation state.<br>**true** if support; **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function cannot work because the current device does not support this ability. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isSeparationTouchEnabled = windowClass.isSeparationTouchEnabled();
  console.info(`Succeeded in getting the window separationTouchEnabled status: ${isSeparationTouchEnabled}`);
} catch (exception) {
  console.error(`Failed to get the window separationTouchEnabled status.. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## isShowing

```TypeScript
isShowing(callback: AsyncCallback<boolean>): void
```

Checks whether this window is displayed. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [isWindowShowing](#iswindowshowing)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. **true** if the window is displayed, **false** otherwise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

windowClass.isShowing((err: BusinessError, data) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to check whether the window is showing. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in checking whether the window is showing. Data: ' + JSON.stringify(data));
});
```

<a id="isshowing-1"></a>

## isShowing

```TypeScript
isShowing(): Promise<boolean>
```

Checks whether this window is displayed. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [isWindowShowing](#iswindowshowing)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. **true** if the window is displayed, **false** otherwise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = windowClass.isShowing();
promise.then((data) => {
  console.info('Succeeded in checking whether the window is showing. Data: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`Failed to check whether the window is showing. Cause code: ${err.code}, message: ${err.message}`);
});
```

## isSupportWideGamut

```TypeScript
isSupportWideGamut(): Promise<boolean>
```

Checks whether this window supports the wide-gamut color space. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isWindowSupportWideGamut](#iswindowsupportwidegamut)()

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. **true** if the wide-gamut color space is supported, **false** otherwise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = windowClass.isSupportWideGamut();
promise.then((data) => {
  console.info('Succeeded in checking whether the window support WideGamut. Data: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`Failed to check whether the window support WideGamut. Cause code: ${err.code}, message: ${err.message}`);
});
```

<a id="issupportwidegamut-1"></a>

## isSupportWideGamut

```TypeScript
isSupportWideGamut(callback: AsyncCallback<boolean>): void
```

Checks whether this window supports the wide-gamut color space. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isWindowSupportWideGamut](#iswindowsupportwidegamut-1)(callback: AsyncCallback&lt;boolean&gt;)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. **true** if the wide-gamut color space is supported, **false** otherwise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

windowClass.isSupportWideGamut((err: BusinessError, data) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to check whether the window support WideGamut. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in checking whether the window support WideGamut Data: ' + JSON.stringify(data));
});
```

## isSystemAvoidAreaEnabled

```TypeScript
isSystemAvoidAreaEnabled(): boolean
```

Checks whether a floating window, modal window, or system window (**WindowType** is a system window) is enabled to access the [avoid area](arkts-arkui-window-avoidarea-i.md).

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether the window is enabled to access the avoid area.<br> **true** if enabled, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Create js value failed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        console.error('Failed to load the content. Cause: %{public}s', JSON.stringify(err));
        return;
      }
      console.info('Succeeded in loading the content.');
      let windowClass: window.Window | undefined = undefined;
      let config: window.Configuration = {
        name: "test",
        windowType: window.WindowType.TYPE_DIALOG,
        decorEnabled: true,
        ctx: this.context
      };
      try {
        window.createWindow(config, (err: BusinessError, data) => {
          const errCode: number = err.code;
          if (errCode) {
            console.error(`Failed to create the system window. Cause code: ${err.code}, message: ${err.message}`);
            return;
          }
          windowClass = data;
          windowClass.setUIContent("pages/Test");
          let promise = windowClass.setSystemAvoidAreaEnabled(true);
          promise.then(() => {
            let enabled = windowClass?.isSystemAvoidAreaEnabled();
          }).catch((err: BusinessError) => {
            console.error(`Failed to obtain the system window avoid area enable. Cause code: ${err.code}, message: ${err.message}`);
          });
        });
      } catch (exception) {
        console.error(`Failed to create the system window. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

## isWindowHighlighted

```TypeScript
isWindowHighlighted(): boolean
```

Checks whether the window is active. To obtain the active state, call this API when the [WindowEventType](arkts-arkui-window-windoweventtype-e.md) lifecycle is **WINDOW_ACTIVE**.

You can use [on('windowHighlightChange')](#onwindowhighlightchange) to listen for status changes and then execute the corresponding service.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether the window is active. **true** if active, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isHighlighted = windowClass.isWindowHighlighted();
  console.info(`Succeeded in getting the window highlight status: ${isHighlighted}`);
} catch (exception) {
  console.error(`Failed to get the window highlight status.. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## isWindowShowing

```TypeScript
isWindowShowing(): boolean
```

Checks whether this window is displayed.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the window is displayed. **true** if displayed, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |

**Examples**

```TypeScript
try {
  let data = windowClass.isWindowShowing();
  console.info('Succeeded in checking whether the window is showing. Data: ' + JSON.stringify(data));
} catch (exception) {
  console.error(`Failed to check whether the window is showing. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## isWindowSupportWideGamut

```TypeScript
isWindowSupportWideGamut(): Promise<boolean>
```

Checks whether this window supports the wide-gamut color space. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. **true** if the wide-gamut color space is supported, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = windowClass.isWindowSupportWideGamut();
promise.then((data) => {
  console.info(`Succeeded in checking whether the window support WideGamut. Data: ${data}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to check whether the window support WideGamut. Cause code: ${err.code}, message: ${err.message}`);
});
```

<a id="iswindowsupportwidegamut-1"></a>

## isWindowSupportWideGamut

```TypeScript
isWindowSupportWideGamut(callback: AsyncCallback<boolean>): void
```

Checks whether this window supports the wide-gamut color space. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

windowClass.isWindowSupportWideGamut((err: BusinessError, data) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to check whether the window support WideGamut. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in checking whether the window support WideGamut Data: ${data}`);
});
```

## keepKeyboardOnFocus

```TypeScript
keepKeyboardOnFocus(keepKeyboardFlag: boolean): void
```

Determines whether to retain the soft keyboard created by another window when the current window gains focus. This API is only supported by system windows and application child windows.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keepKeyboardFlag | boolean | Yes | Whether to keep the soft keyboard created by others. **true** to keep, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Only float windows, subwindows, dialog windows, or window type as system windows are supported. |

**Examples**

```TypeScript
try {
  windowClass.keepKeyboardOnFocus(true);
} catch (exception) {
  console.error(`Failed to keep keyboard onFocus. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## loadContent

```TypeScript
loadContent(path: string, storage: LocalStorage, callback: AsyncCallback<void>): void
```

Loads the content of a page, with its path in the current project specified, to this window, and transfers the state attribute to the page through a local storage. This API uses an asynchronous callback to return the result. You are advised to call this API during UIAbility startup. If called repeatedly, this API will destroy the existing page content (UIContent) before loading the new content. Exercise caution when using it. The execution context of the current UI may be unclear. Therefore, you are advised not to perform UI-related operations within the callback.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the page from which the content will be loaded. The path is configured in the **main_pages.json** file of the project. |
| storage | LocalStorage | Yes | Page-level UI state storage unit, which is used to transfer the state attribute for the page. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Invalid path parameter. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally.<br>**Applicable version:** 9 |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let storage: LocalStorage = new LocalStorage();
storage.setOrCreate('storageSimpleProp', 121);
windowClass.loadContent('pages/page2', storage, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in loading the content.');
});
```

<a id="loadcontent-1"></a>

## loadContent

```TypeScript
loadContent(path: string, storage: LocalStorage): Promise<void>
```

Loads the content of a page, with its path in the current project specified, to this window, and transfers the state attribute to the page through a local storage. This API uses a promise to return the result. You are advised to call this API during UIAbility startup. If called repeatedly, this API will destroy the existing page content (UIContent) before loading the new content. Exercise caution when using it. The execution context of the current UI may be unclear. Therefore, you are advised not to perform UI-related operations within the callback.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the page from which the content will be loaded. The path is configured in the **main_pages.json** file of the project. |
| storage | LocalStorage | Yes | Page-level UI state storage unit, which is used to transfer the state attribute for the page. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Invalid path parameter. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally.<br>**Applicable version:** 9 |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let storage: LocalStorage = new LocalStorage();
storage.setOrCreate('storageSimpleProp', 121);
let promise = windowClass.loadContent('pages/page2', storage);
promise.then(() => {
  console.info('Succeeded in loading the content.');
}).catch((err: BusinessError) => {
  console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
});
```

<a id="loadcontent-2"></a>

## loadContent

```TypeScript
loadContent(path: string, callback: AsyncCallback<void>): void
```

Loads content from a page to this window. This API uses an asynchronous callback to return the result. You are advised to call this API during UIAbility startup. If called multiple times, this API will destroy the existing page content (UIContent) before loading the new content. Exercise caution when using it. The execution context of the current UI may be unclear. Therefore, you are advised not to perform UI-related operations within the callback.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setUIContent](#setuicontent)(path: string, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the page from which the content will be loaded. In the stage model, the path is configured in the **main_pages.json** file of the project. In the FA model, the path is configured in the **config.json** file of the project. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

windowClass.loadContent('pages/page2/page3', (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in loading the content.');
});
```

<a id="loadcontent-3"></a>

## loadContent

```TypeScript
loadContent(path: string): Promise<void>
```

Loads content from a page to this window. This API uses a promise to return the result. You are advised to call this API during UIAbility startup. If called multiple times, this API will destroy the existing page content (UIContent) before loading the new content. Exercise caution when using it. The execution context of the current UI may be unclear. Therefore, you are advised not to perform UI-related operations within the callback.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setUIContent](#setuicontent-1)(path: string)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the page from which the content will be loaded. In the stage model, the path is configured in the **main_pages.json** file of the project. In the FA model, the path is configured in the **config.json** file of the project. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = windowClass.loadContent('pages/page2/page3');
promise.then(() => {
  console.info('Succeeded in loading the content.');
}).catch((err: BusinessError) => {
  console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
});
```

## loadContentByName

```TypeScript
loadContentByName(name: string, storage: LocalStorage, callback: AsyncCallback<void>): void
```

Loads the content of a [named route](../../../ui/arkts-routing.md#named-route) page to this window, and transfers the state attribute to the page through a local storage. This API uses an asynchronous callback to return the result. You are advised to call this API during UIAbility startup. If called repeatedly, this API will destroy the existing page content (UIContent) before loading the new content. Exercise caution when using it. The execution context of the current UI may be unclear. Therefore, you are advised not to perform UI-related operations within the callback.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the named route page. |
| storage | LocalStorage | Yes | Page-level UI state storage unit, which is used to transfer the state attribute for the page. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
// EntryAbility.ets

import { window } from '@kit.ArkUI';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import * as Index from '../pages/Index'; // Import the named route page.

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    let storage: LocalStorage = new LocalStorage();
    let newValue: Number = 121;
    storage.setOrCreate('storageSimpleProp', newValue);
    try {
      let windowClass: window.Window = windowStage.getMainWindowSync();
      if (!windowClass) {
        console.error('Failed to get main window.');
        return;
      }
      windowClass.loadContentByName(Index.entryName, storage, (err: BusinessError) => {
        const errCode: number = err?.code;
        if (errCode) {
          console.error(`Failed to load the content. Cause code: ${err?.code}, message: ${err?.message}`);
          return;
        }
        console.info('Succeeded in loading the content.');
      });
    } catch (exception) {
      console.error(`Failed to load the content. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

```TypeScript
// ets/pages/Index.ets
export const entryName : string = 'Index';
@Entry({routeName: entryName, useSharedStorage: true})
@Component
export struct Index {
  @State message: string = 'Hello World'
  @LocalStorageLink('storageSimpleProp') storageSimpleProp: number = 1;
  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

<a id="loadcontentbyname-1"></a>

## loadContentByName

```TypeScript
loadContentByName(name: string, callback: AsyncCallback<void>): void
```

Loads the content of a [named route](../../../ui/arkts-routing.md#named-route) page to this window. This API uses an asynchronous callback to return the result. You are advised to call this API during UIAbility startup. If called repeatedly, this API will destroy the existing page content (UIContent) before loading the new content. Exercise caution when using it. The execution context of the current UI may be unclear. Therefore, you are advised not to perform UI-related operations within the callback.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the named route page. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import * as Index from '../pages/Index'; // Import the named route page.

try {
  (windowClass as window.Window).loadContentByName(Index.entryName, (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in loading the content.');
  });
} catch (exception) {
  console.error(`Failed to load the content. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

```TypeScript
// ets/pages/Index.ets
export const entryName : string = 'Index';
@Entry({routeName: entryName})
@Component
export struct Index {
  @State message: string = 'Hello World'
  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

<a id="loadcontentbyname-2"></a>

## loadContentByName

```TypeScript
loadContentByName(name: string, storage?: LocalStorage): Promise<void>
```

Loads the content of a [named route](../../../ui/arkts-routing.md#named-route) page to this window, and transfers the state attribute to the page through a local storage. This API uses a promise to return the result. You are advised to call this API during UIAbility startup. If called repeatedly, this API will destroy the existing page content (UIContent) before loading the new content. Exercise caution when using it. The execution context of the current UI may be unclear. Therefore, you are advised not to perform UI-related operations within the callback.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the named route page. |
| storage | LocalStorage | No | Page-level UI state storage unit, which is used to transfer the state attribute for the page. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import * as Index from '../pages/Index'; // Import the named route page.

let storage: LocalStorage = new LocalStorage();
storage.setOrCreate('storageSimpleProp', 121);
try {
  let promise = (windowClass as window.Window).loadContentByName(Index.entryName, storage);
  promise.then(() => {
    console.info('Succeeded in loading the content.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to load the content. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

```TypeScript
// ets/pages/Index.ets
export const entryName : string = 'Index';
@Entry({routeName: entryName, useSharedStorage: true})
@Component
export struct Index {
  @State message: string = 'Hello World'
  @LocalStorageLink('storageSimpleProp') storageSimpleProp: number = 1;
  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## maximize

```TypeScript
maximize(presentation?: MaximizePresentation): Promise<void>
```

Maximizes the window. The main window can use this API to maximize. For child windows, you need to set **maximizeSupported** to **true** when creating the windows and then call this API to maximize. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| presentation | [MaximizePresentation](arkts-arkui-window-maximizepresentation-e.md) | No | Layout when the window is maximized. The default value is window.MaximizePresentation.ENTER_IMMERSIVE, indicating that the window enters the immersive layout when maximized.<br>**Since:** 20 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function maximize can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows and maximizable subwindows are supported. |
| [1300005](../errorcode-window.md#1300005-abnormal-windowstage) | This window stage is abnormal.<br>**Applicable version:** 12 - 19 |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let promise = windowClass.maximize();
      // let promise = windowClass.maximize(window.MaximizePresentation.ENTER_IMMERSIVE);
      promise.then(() => {
        console.info('Succeeded in maximizing the window.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to maximize the window. Cause code: ${err.code}, message: ${err.message}`);
      });
    });
  }
};
```

<a id="maximize-1"></a>

## maximize

```TypeScript
maximize(presentation?: MaximizePresentation, acrossDisplay?: boolean): Promise<void>
```

Maximizes the window. The main window can use this API to maximize. For child windows, you need to set **maximizeSupported** to **true** when creating the windows and then call this API to maximize. On 2-in-1 devices with folding capabilities, you can use the **acrossDisplay** parameter to control the main window's behavior in waterfall mode when maximized in the hover state. (See [Semi-Folded State of Foldable Screens](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-folded-hover)). This API uses a promise to return the result.

**Since:** 22

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| presentation | [MaximizePresentation](arkts-arkui-window-maximizepresentation-e.md) | No | Layout when the window is maximized. The default value is window.MaximizePresentation.ENTER_IMMERSIVE, indicating that the window enters the immersive layout when maximized. |
| acrossDisplay | boolean | No | Parameter controls the across-display mode policy of main windows in the half-folded state. The value true Indicates that the window could enter the across-display mode directly, and maintains the across-display mode when the device is half-folded. The default value is undefined. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function maximize can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows and maximizable subwindows are supported. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      let mainWindow = windowStage.getMainWindowSync();
      mainWindow.maximize(window.MaximizePresentation.ENTER_IMMERSIVE, true)
        .then(() => {
          console.info('Window maximized successfully.');
        })
        .catch((err: BusinessError) => {
          console.error(`Failed to maximize the window. Cause code: ${err.code}, message: ${err.message}`);
        });
    });
  }
};
```

## maximizeWithOptions

```TypeScript
maximizeWithOptions(maximizeOptions?: MaximizeOptions): Promise<void>
```

Maximize the app window.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| maximizeOptions | [MaximizeOptions](arkts-arkui-window-maximizeoptions-i.md) | No | The configuration of maximize. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: 1. Invalid window type. Only main windows and maximizable subwindows are supported; 2. The acrossDisplay parameter only supports main windows. 3. The snapshotAnimationConfig parameter only supports main windows. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: Invalid parameter range. |

## minimize

```TypeScript
minimize(callback: AsyncCallback<void>): void
```

The behavior of this API varies based on the caller:

- Minimizes the main window if the caller is the main window. The main window can be restored in the dock bar.  
For 2-in-1 devices, it can be restored by calling [restore()](#restore).  
- Hides the child window or global floating window if the caller is a child window. The child window or floating  
window cannot be restored in the dock bar. It can be made visible again by calling [showWindow()](#showwindow).

This API can be called only by the main window, child window, or global floating window. If it is called by other windows, error code 1300002 is thrown. This API uses an asynchronous callback to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error; 3. Invalid window type. Only main windows, subwindows, and float windows are supported. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

windowClass.minimize((err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to minimize the window. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in minimizing the window.');
});
```

<a id="minimize-1"></a>

## minimize

```TypeScript
minimize(): Promise<void>
```

The behavior of this API varies based on the caller:

- Minimizes the main window if the caller is the main window. The main window can be restored in the dock bar.  
For 2-in-1 devices, it can be restored by calling [restore()](#restore).  
- Hides the child window or global floating window if the caller is a child window. The child window or floating  
window cannot be restored in the dock bar. It can be made visible again by calling [showWindow()](#showwindow).

This API can be called only by the main window, child window, or global floating window. If it is called by other windows, error code 1300002 is thrown. This API uses a promise to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error; 3. Invalid window type. Only main windows, subwindows, and float windows are supported. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = windowClass.minimize();
promise.then(() => {
  console.info('Succeeded in minimizing the window.');
}).catch((err: BusinessError) => {
  console.error(`Failed to minimize the window. Cause code: ${err.code}, message: ${err.message}`);
});
```

## moveTo

```TypeScript
moveTo(x: number, y: number): Promise<void>
```

Moves this window. This API uses a promise to return the result.

This operation is not supported in a window in full-screen mode.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [moveWindowTo](#movewindowto)(x: number, y: number)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Coordinate position along the x-axis to which the window is moved, measured in px. A positive value means the position is to the right of the x-axis origin; a negative value means it is to the left; the value **0** means it is at the x-axis origin. The value must be an integer. Non-integer values are rounded down. |
| y | number | Yes | Coordinate position along the y-axis to which the window is moved, measured in px. A positive value means the position is below the y-axis origin; a negative value means it is above; the value **0** means it is at the y-axis origin. The value must be an integer. Non-integer values are rounded down. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = windowClass.moveTo(300, 300);
promise.then(() => {
  console.info('Succeeded in moving the window.');
}).catch((err: BusinessError) => {
  console.error(`Failed to move the window. Cause code: ${err.code}, message: ${err.message}`);
});
```

<a id="moveto-1"></a>

## moveTo

```TypeScript
moveTo(x: number, y: number, callback: AsyncCallback<void>): void
```

Moves this window. This API uses an asynchronous callback to return the result.

This operation is not supported in a window in full-screen mode.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [moveWindowTo](#movewindowto)(x: number, y: number, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Coordinate position along the x-axis to which the window is moved, measured in px. A positive value means the position is to the right of the x-axis origin; a negative value means it is to the left; the value **0** means it is at the x-axis origin. The value must be an integer. Non-integer values are rounded down. |
| y | number | Yes | Coordinate position along the y-axis to which the window is moved, measured in px. A positive value means the position is below the y-axis origin; a negative value means it is above; the value **0** means it is at the x-axis origin. The value must be an integer. Non-integer values are rounded down. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

windowClass.moveTo(300, 300, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to move the window. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in moving the window.');
});
```

## moveWindowTo

```TypeScript
moveWindowTo(x: number, y: number): Promise<void>
```

Moves this window. This API uses a promise to return the result. A value is returned once the API is called successfully. However, the final effect cannot be obtained immediately from the return value. To obtain the final effect immediately, call [moveWindowToAsync()](#movewindowtoasync).

> **NOTE:** 
> 
> - This API is best suited for the floating window mode (when the window mode is
> **window.WindowStatusType.FLOATING**, which you can check using
> [getWindowStatus()](#getwindowstatus)). You are not advised to use it in other window modes.
> 
> - In [freeform window](../../../windowmanager/window-terminology.md#freeform-window) mode, the window moves relative to the upper-left corner of the screen. In non-freeform window mode, the window moves relative to the upper-left corner of its parent window.
> 
> - To move the window relative to the top-left corner of the screen while in non-freeform window mode, call [moveWindowToGlobal()](#movewindowtoglobal).
> 
> - This API does not work for the main window in non-freeform window mode.
> 
> - In [freeform window](../../../windowmanager/window-terminology.md#freeform-window) mode,if the title bar of the main window or a child window is moved out of the screen's visible area,the system will automatically snap the window back to ensure the title bar is visible.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate to which the window moves, in px. A positive value indicates a position to the right of the origin, and a negative value indicates a position to the left of the origin. The value must be an integer. Non-integer values are rounded down. |
| y | number | Yes | Y-coordinate to which the window moves, in pixels. A positive value indicates a position above the origin, and a negative value indicates a position below the origin. The value must be an integer. Non-integer values are rounded down. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. The main windows in non-freeform window mode are not supported. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let promise = windowClass.moveWindowTo(300, 300);
  promise.then(() => {
    console.info('Succeeded in moving the window.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to move the window. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to move the window. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

<a id="movewindowto-1"></a>

## moveWindowTo

```TypeScript
moveWindowTo(x: number, y: number, callback: AsyncCallback<void>): void
```

Moves this window. This API uses an asynchronous callback to return the result. A value is returned once the API is called successfully. However, the final effect cannot be obtained immediately from the return value. To obtain the final effect immediately, call [moveWindowToAsync()](#movewindowtoasync).

> **NOTE:** 
> 
> - This API is best suited for the floating window mode (when the window mode is
> **window.WindowStatusType.FLOATING**, which can obtained using
> [getWindowStatus()](#getwindowstatus)). You are advised not to use it in other window modes.
> 
> - In [freeform window](../../../windowmanager/window-terminology.md#freeform-window) mode, the window moves relative to the upper-left corner of the screen. In non-freeform window mode, the window moves relative to the upper-left corner of its parent window.
> 
> - To move the window relative to the top-left corner of the screen while in non-freeform window mode, call [moveWindowToGlobal()](#movewindowtoglobal).
> 
> - This API does not work for the main window in non-freeform window mode.
> 
> - In [freeform window](../../../windowmanager/window-terminology.md#freeform-window) mode,if the title bar of the main window or a child window is moved out of the screen's visible area,the system will automatically snap the window back to ensure the title bar is visible.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate to which the window moves, in px. A positive value indicates a position to the right of the origin, and a negative value indicates a position to the left of the origin. The value must be an integer. Non-integer values are rounded down. |
| y | number | Yes | Y-coordinate to which the window moves, in pixels. A positive value indicates a position above the origin, and a negative value indicates a position below the origin. The value must be an integer. Non-integer values are rounded down. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. The main windows in non-freeform window mode are not supported. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  windowClass.moveWindowTo(300, 300, (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to move the window. Cause code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in moving the window.');
  });
} catch (exception) {
  console.error(`Failed to move the window. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## moveWindowToAsync

```TypeScript
moveWindowToAsync(x: number, y: number): Promise<void>
```

Moves this window. This API uses a promise to return the result. A value is returned once the call takes effect. You can use [getWindowProperties()](#getwindowproperties) in the callback (see the code snippet below) to obtain the final effect immediately.

This API takes effect only when the window is in floating window mode (**window.WindowStatusType.FLOATING**). In other window modes, this API returns error code 1300010. (The window mode can be obtained through [getWindowStatus()](#getwindowstatus)). In floating window mode, the movement behavior of different types of windows is as follows.

> **NOTE:** 
> 
> - In [freeform window](../../../windowmanager/window-terminology.md#freeform-window) mode,if the title bar of the main window or a child window is moved out of the screen's visible area,the system will automatically snap the window back to ensure the title bar is visible.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Coordinate position along the x-axis to which the window is moved, measured in px. A positive value means the position is to the right of the x-axis origin; a negative value means it is to the left; the value **0** means it is at the x-axis origin. The value must be an integer. Non-integer values are rounded down. |
| y | number | Yes | Coordinate position along the y-axis to which the window is moved, measured in px. A positive value means the position is below the y-axis origin; a negative value means it is above; the value **0** means it is at the y-axis origin. The value must be an integer. Non-integer values are rounded down. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. The window type is not supported for this operation. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300010](../errorcode-window.md#1300010-unsupported-operation-in-the-current-window-mode) | The operation in the current window status is invalid. Possible cause: The window status is not FLOATING. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let promise = windowClass.moveWindowToAsync(300, 300);
  promise.then(() => {
    console.info('Succeeded in moving the window.');
    let rect = windowClass?.getWindowProperties().windowRect;
    console.info(`Get window rect: ` + JSON.stringify(rect));
  }).catch((err: BusinessError) => {
    console.error(`Failed to move the window. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to move the window. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

<a id="movewindowtoasync-1"></a>

## moveWindowToAsync

```TypeScript
moveWindowToAsync(x: number, y: number, moveConfiguration?: MoveConfiguration): Promise<void>
```

Moves this window to the specified position. This API uses a promise to return the result. You can use the **moveConfiguration** parameter to specify the target display ID for the window movement. A value is returned once the call takes effect. You can use [getWindowProperties()](#getwindowproperties) in the callback (see the code snippet below) to obtain the final effect immediately.

This API takes effect only when the window is in floating window mode (**window.WindowStatusType.FLOATING**). In other window modes, this API returns error code 1300010. (The window mode can be obtained through [getWindowStatus()](#getwindowstatus)). In floating window mode, the movement behavior of different types of windows is as follows.

| Window Type| [Freeform Window](../../../windowmanager/window-terminology.md#freeform-window) State| Non-freeform Window State|  
|---------|---------------|-----------------|  
| Main window| Move relative to the screen.| API calls do not take effect or return an error.|
| App subwindow/Modal window| Move relative to the screen.| Move relative to the main window.|
| System window/Global floating window| Move relative to the screen.| Move relative to the screen.|

> **NOTE:** 
> 
> - In [freeform window](../../../windowmanager/window-terminology.md#freeform-window) mode,if the title bar of the main window or a child window is moved out of the screen's visible area,the system will automatically snap the window back to ensure the title bar is visible.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Distance that the window moves along the x-axis, in px. A positive value indicates that the window moves to the right. The value must be an integer. Non-integer values are rounded down. |
| y | number | Yes | Distance that the window moves along the y-axis, in px. A positive value indicates that the window moves downwards. The value must be an integer. Non-integer values are rounded down. |
| moveConfiguration | [MoveConfiguration](arkts-arkui-window-moveconfiguration-i.md) | No | Window movement configuration. If this parameter is not set, the window will stay on the current display. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. The window type is not supported for this operation. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300010](../errorcode-window.md#1300010-unsupported-operation-in-the-current-window-mode) | The operation in the current window status is invalid. Possible cause: The window status is not FLOATING. |

**Examples**

```TypeScript
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let moveConfiguration: window.MoveConfiguration = {
    displayId: 0
  };
  let promise = windowClass.moveWindowToAsync(300, 300, moveConfiguration);
  promise.then(() => {
    console.info('Succeeded in moving the window.');
    let rect = windowClass?.getWindowProperties().windowRect;
    console.info(`Get window rect: ` + JSON.stringify(rect));
  }).catch((err: BusinessError) => {
    console.error(`Failed to move the window. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to move the window. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## moveWindowToGlobal

```TypeScript
moveWindowToGlobal(x: number, y: number): Promise<void>
```

Moves this window based on the coordinates. This API uses a promise to return the result. A value is returned once the call takes effect. You can use [getWindowProperties()](#getwindowproperties) in the callback (see the code snippet below) to obtain the final effect immediately.

This API takes effect only when the window is in floating window mode (**window.WindowStatusType.FLOATING**). In other window modes, this API returns error code 1300010. (The window mode can be obtained through [getWindowStatus()](#getwindowstatus)).

> **NOTE:** 
> 
> - When the main window is in floating window mode, this API does not take effect or return an error if called in non-[freeform window](../../../windowmanager/window-terminology.md#freeform-window) state.
> 
> - In [freeform window](../../../windowmanager/window-terminology.md#freeform-window) mode,if the title bar of the main window or a child window is moved out of the screen's visible area,the system will automatically snap the window back to ensure the title bar is visible.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Distance that the window moves along the x-axis, in px, with the top-left corner of the display used as the origin. A positive value indicates that the window moves to the right, and a negative value indicates that the window moves to the left. The value must be an integer. Non-integer values are rounded down. |
| y | number | Yes | Distance that the window moves along the y-axis, in px, with the top-left corner of the display used as the origin. A positive value indicates that the window moves downwards, and a negative value indicates that the window moves upwards. The value must be an integer. Non-integer values are rounded down. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. The window type is not supported for this operation. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300010](../errorcode-window.md#1300010-unsupported-operation-in-the-current-window-mode) | The operation in the current window status is invalid. Possible cause: The window status is not FLOATING. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let promise = windowClass.moveWindowToGlobal(300, 300);
  promise.then(() => {
    console.info('Succeeded in moving the window.');
    let rect = windowClass?.getWindowProperties().windowRect;
    console.info(`Get window rect: ` + JSON.stringify(rect));
  }).catch((err: BusinessError) => {
    console.error(`Failed to move the window. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to move the window. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

<a id="movewindowtoglobal-1"></a>

## moveWindowToGlobal

```TypeScript
moveWindowToGlobal(x: number, y: number, moveConfiguration?: MoveConfiguration): Promise<void>
```

Moves this window to the specified position based on the coordinates. This API uses a promise to return the result. You can use the **moveConfiguration** parameter to specify the target display ID for the window movement. A value is returned once the call takes effect. You can use [getWindowProperties()](#getwindowproperties) in the callback (see the code snippet below) to obtain the final effect immediately.

This API takes effect only when the window is in floating window mode (**window.WindowStatusType.FLOATING**). In other window modes, this API returns error code 1300010. (The window mode can be obtained through [getWindowStatus()](#getwindowstatus)).

> **NOTE:** 
> 
> - When the main window is in floating window mode, this API does not take effect or return an error if called in non-[freeform window](../../../windowmanager/window-terminology.md#freeform-window) state.
> 
> - In [freeform window](../../../windowmanager/window-terminology.md#freeform-window) mode,if the title bar of the main window or a child window is moved out of the screen's visible area,the system will automatically snap the window back to ensure the title bar is visible.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Distance that the window moves along the x-axis, in px, with the top-left corner of the display used as the origin. A positive value indicates that the window moves to the right, and a negative value indicates that the window moves to the left. The value must be an integer. Non-integer values are rounded down. |
| y | number | Yes | Distance that the window moves along the y-axis, in px, with the top-left corner of the display used as the origin. A positive value indicates that the window moves downwards, and a negative value indicates that the window moves upwards. The value must be an integer. Non-integer values are rounded down. |
| moveConfiguration | [MoveConfiguration](arkts-arkui-window-moveconfiguration-i.md) | No | Indicate the window move configuration. If not provided, the window stays on the current display. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. The window type is not supported for this operation. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300010](../errorcode-window.md#1300010-unsupported-operation-in-the-current-window-mode) | The operation in the current window status is invalid. Possible cause: The window status is not FLOATING. |

**Examples**

```TypeScript
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let moveConfiguration: window.MoveConfiguration = {
    displayId: 0
  };
  let promise = windowClass.moveWindowToGlobal(300, 300, moveConfiguration);
  promise.then(() => {
    console.info('Succeeded in moving the window.');
    let rect = windowClass?.getWindowProperties().windowRect;
    console.info(`Get window rect: ` + JSON.stringify(rect));
  }).catch((err: BusinessError) => {
    console.error(`Failed to move the window. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to move the window. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## moveWindowToGlobalDisplay

```TypeScript
moveWindowToGlobalDisplay(x: number, y: number): Promise<void>
```

Moves the window based on the [global coordinate system](../../../windowmanager/window-terminology.md#global-coordinate-system). This API uses a promise to return the result asynchronously.

This API takes effect only when the window is in floating window mode (**window.WindowStatusType.FLOATING**). In other window modes, this API returns error code 1300010. (The window mode can be obtained through [getWindowStatus()](#getwindowstatus)).

> **NOTE:** 
> 
> - When the main window is in floating window mode, this API does not take effect or return an error if called in non-[freeform window](../../../windowmanager/window-terminology.md#freeform-window) state.
> 
> - After a window is moved, if it spans multiple screens, the window will belong to the screen with which it has the largest overlapping area.
> 
> - In [freeform window](../../../windowmanager/window-terminology.md#freeform-window) mode,if the title bar of the main window or a child window is moved out of the screen's visible area,the system will automatically snap the window back to ensure the title bar is visible.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Distance that the window moves along the x-axis, in px, with the top-left corner of the primary display used as the origin. A positive value indicates that the window moves to the right, and a negative value indicates that the window moves to the left. The value must be an integer. Non-integer values are rounded down. |
| y | number | Yes | Distance that the window moves along the y-axis, in px, with the top-left corner of the primary display used as the origin. A positive value indicates that the window moves downwards, and a negative value indicates that the window moves upwards. The value must be an integer. Non-integer values are rounded down.ured in px. This parameter only accepts integer values; any floating-point input will be rounded down. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300010](../errorcode-window.md#1300010-unsupported-operation-in-the-current-window-mode) | The operation in the current window status is invalid. Possible cause: The window status is not FLOATING. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: 1. Invalid parameter range. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let promise = windowClass.moveWindowToGlobalDisplay(300, 300);
  promise.then(() => {
    console.info('Succeeded in moving the window in global display.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to move the window in global display. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to move the window in global display. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('rotationChange')

```TypeScript
off(type: 'rotationChange', 
       callback?: RotationChangeCallback<RotationChangeInfo, RotationChangeResult | void>): void
```

Unsubscribes from the window rotation change event.

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'rotationChange' | Yes | Event type. The value is fixed at **'rotationChange'**, indicating the window rotation change event. |
| callback | [RotationChangeCallback](arkts-arkui-window-rotationchangecallback-t.md)&lt;[RotationChangeInfo](arkts-arkui-window-rotationchangeinfo-i.md), [RotationChangeResult](arkts-arkui-window-rotationchangeresult-i.md) &#124; void&gt; | No | Callback used to return the result. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
const callback = (info: window.RotationChangeInfo): window.RotationChangeResult | void => {
  // ...
  return;
}
try {
  windowClass.off('rotationChange', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('rotationChange');
} catch (exception) {
  console.error(`Failed to unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

<a id="off-1"></a>

## off

```TypeScript
off(eventType: 'uiExtensionSecureLimitChange', callback?: Callback<boolean>): void
```

Unsubscribes from the event indicating changes in the security restrictions of the UIExtensionAbility within the window.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| eventType | 'uiExtensionSecureLimitChange' | Yes | Event type. The value is fixed at **'uiExtensionSecureLimitChange'**, indicating that the UIExtensionAbility security restrictions in the window changes. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;boolean&gt; | No | Callback used to return the result. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function off('uiExtensionSecureLimitChange') cannot work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
const callback = (data: boolean) => {
  // ...
}
try {
  // Enable listening through the on API.
  windowClass.on('uiExtensionSecureLimitChange', callback);
  // Disable the listening of a specified callback.
  windowClass.off('uiExtensionSecureLimitChange', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('uiExtensionSecureLimitChange');
} catch (exception) {
  console.error(`Failed to unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('frameMetricsMeasured')

```TypeScript
off(type: 'frameMetricsMeasured', callback?: Callback<FrameMetrics>): void
```

Unsubscribes from events indicating changes in window frame metrics. This API must be used after the call of [loadContent](#loadcontent) or [setUIContent()](#setuicontent) takes effect.

**Since:** 22

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'frameMetricsMeasured' | Yes | Event type. The value is fixed at **'frameMetricsMeasured'**, indicating the window frame metrics change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[FrameMetrics](arkts-arkui-window-framemetrics-i.md)&gt; | No | If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created. |

**Examples**

```TypeScript
try {
  let callback: Callback<window.FrameMetrics> = (data: window.FrameMetrics) => {
    console.info(`Window frame metrics changed: ${JSON.stringify(data)}`);
  };
  // Enable listening through the on API.
  windowClass.on('frameMetricsMeasured', callback);
  // Disable the listening of a specified callback.
  windowClass.off('frameMetricsMeasured', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('frameMetricsMeasured');
} catch (exception) {
  console.error(`Failed to register callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('occlusionStateChanged')

```TypeScript
off(type: 'occlusionStateChanged', callback?: Callback<OcclusionState>): void
```

Unsubscribes from the visibility status change event of the window.

**Since:** 22

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'occlusionStateChanged' | Yes | Event type. The value is fixed at **'occlusionStateChanged'**, indicating the window visibility status change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[OcclusionState](arkts-arkui-window-occlusionstate-e.md)&gt; | No | If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
try {
  let callback: Callback<window.OcclusionState> = (data: window.OcclusionState) => {
    console.info(`Window occlusion state changed: ${data}`);
  };
  // Enable listening through the on API.
  windowClass.on('occlusionStateChanged', callback);
  // Disable the listening of a specified callback.
  windowClass.off('occlusionStateChanged', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('occlusionStateChanged');
} catch (exception) {
  console.error(`Failed to register callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('windowSizeChange')

```TypeScript
off(type: 'windowSizeChange', callback?: Callback<Size>): void
```

Unsubscribes from the window size change event. This API can be called only by the main thread.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'windowSizeChange' | Yes | Event type. The value is fixed at **'windowSizeChange'**, indicating the window size change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;Size&gt; | No | Callback used to return the window size. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Incorrect parameter types; 2. Parameter verification failed. |

**Examples**

```TypeScript
const callback = (size: window.Size) => {
  // ...
}
try {
  // Enable listening through the on API.
  windowClass.on('windowSizeChange', callback);
  // Disable the listening of a specified callback.
  windowClass.off('windowSizeChange', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('windowSizeChange');
} catch (exception) {
  console.error(`Failed to disable the listener for window size changes. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('systemAvoidAreaChange')

```TypeScript
off(type: 'systemAvoidAreaChange', callback?: Callback<AvoidArea>): void
```

Unsubscribes from the event indicating changes to the area where this window cannot be displayed.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [off](#offavoidareachange)(type: 'avoidAreaChange', callback?: Callback&lt;AvoidAreaOptions&gt;)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'systemAvoidAreaChange' | Yes | Event type. The value is fixed at **'systemAvoidAreaChange'**, indicating the event of changes to the area where the window cannot be displayed. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[AvoidArea](arkts-arkui-window-avoidarea-i.md)&gt; | No | Callback used to return the area. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Examples**

```TypeScript
const callback = (avoidArea: window.AvoidArea) => {
  // ...
}
windowClass.on('systemAvoidAreaChange', callback);
windowClass.off('systemAvoidAreaChange', callback);
// Unregister all the callbacks that have been registered through on().
windowClass.off('systemAvoidAreaChange');
```

## off('avoidAreaChange')

```TypeScript
off(type: 'avoidAreaChange', callback?: Callback<AvoidAreaOptions>): void
```

Unsubscribes from the event indicating changes to the area where this window cannot be displayed.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'avoidAreaChange' | Yes | Event type. The value is fixed at **'avoidAreaChange'**, indicating the event of changes to the area where the window cannot be displayed. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[AvoidAreaOptions](arkts-arkui-window-avoidareaoptions-i.md)&gt; | No | Callback used to return the area and area type. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled.<br>**Since:** 20 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

**Examples**

```TypeScript
interface Param {
  type: window.AvoidAreaType,
  area: window.AvoidArea
}
const callback = (data: Param) => {
  // ...
}
try {
  windowClass.on('avoidAreaChange', callback);

  windowClass.off('avoidAreaChange', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('avoidAreaChange');
} catch (exception) {
  console.error(`Failed to enable or disable the listener for system avoid area changes. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('keyboardHeightChange')

```TypeScript
off(type: 'keyboardHeightChange', callback?: Callback<number>): void
```

Unsubscribes from the event indicating soft keyboard height changes in the fixed state so that the application does not receive notifications of soft keyboard height changes. Starting from API version 10, the soft keyboard can be set to the fixed or floating state. For details, see [Input Method Service](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethodengine-panel-i.md#changeflag).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyboardHeightChange' | Yes | Event type. The value is fixed at **'keyboardHeightChange'**, indicating the keyboard height change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;number&gt; | No | Callback used to return the current keyboard height, which is an integer, in px. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Incorrect parameter types; 2. Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const callback = (height: number) => {
  // ...
}
try {
  windowClass.on('keyboardHeightChange', callback);

  windowClass.off('keyboardHeightChange', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('keyboardHeightChange');
} catch (exception) {
  console.error(`Failed to disable the listener for keyboard height changes. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('keyboardWillShow')

```TypeScript
off(type: 'keyboardWillShow', callback?: Callback<KeyboardInfo>): void
```

Unsubscribes from the event indicating that the soft keyboard in the fixed state is about to show. For details about the APIs used to set the input method panel to the fixed or floating state, see [Input Method Service](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethodengine-panel-i.md#changeflag).

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyboardWillShow' | Yes | Event type. The value is fixed at **'keyboardWillShow'**, indicating the soft keyboard in the fixed state is about to show. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[KeyboardInfo](arkts-arkui-window-keyboardinfo-i.md)&gt; | No | Callback used to return the information about the soft keyboard. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function keyboardWillShow can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const callback = (keyboardInfo: window.KeyboardInfo) => {
  console.info(`Keyboard will show animation. keyboardInfo: ` + JSON.stringify(keyboardInfo));
}
try {
  windowClass.on('keyboardWillShow', callback);
  windowClass.off('keyboardWillShow', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('keyboardWillShow');
  console.info(`Unregister keyboard will show animation success`);
} catch (exception) {
  console.error(`Failed to register or unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('keyboardDidShow')

```TypeScript
off(type: 'keyboardDidShow', callback?: Callback<KeyboardInfo>): void
```

Unsubscribes from the event indicating that the show animation of the soft keyboard in the fixed state is completed, For details about the APIs used to set the input method panel to the fixed or floating state, see [Input Method Service](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethodengine-panel-i.md#changeflag).

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyboardDidShow' | Yes | Event type. The value is fixed at **'keyboardDidShow'**, indicating the show animation of the soft keyboard in the fixed state is completed. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[KeyboardInfo](arkts-arkui-window-keyboardinfo-i.md)&gt; | No | Callback used to return the information about the soft keyboard. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function keyboardDidShow can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const callback = (keyboardInfo: window.KeyboardInfo) => {
  // ...
}
try {
  windowClass.on('keyboardDidShow', callback);
  windowClass.off('keyboardDidShow', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('keyboardDidShow');
} catch (exception) {
  console.error(`Failed to register or unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('keyboardWillHide')

```TypeScript
off(type: 'keyboardWillHide', callback?: Callback<KeyboardInfo>): void
```

Unsubscribes from the event indicating that the soft keyboard in the fixed state is about to hide. For details about the APIs used to transition the input method panel from the fixed state to the floating state, see [Input Method Service](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethodengine-panel-i.md#changeflag).

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyboardWillHide' | Yes | Event type. The value is fixed at **'keyboardWillHide'**, indicating the soft keyboard in the fixed state is about to hide. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[KeyboardInfo](arkts-arkui-window-keyboardinfo-i.md)&gt; | No | Callback used to return the information about the soft keyboard. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function keyboardWillHide can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const callback = (keyboardInfo: window.KeyboardInfo) => {
  console.info(`Keyboard will hide animation. keyboardInfo: ` + JSON.stringify(keyboardInfo));
}
try {
  windowClass.on('keyboardWillHide', callback);
  windowClass.off('keyboardWillHide', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('keyboardWillHide');
  console.info(`Unregister keyboard will hide animation success`);
} catch (exception) {
  console.error(`Failed to register or unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('keyboardDidHide')

```TypeScript
off(type: 'keyboardDidHide', callback?: Callback<KeyboardInfo>): void
```

Unsubscribes from the event indicating that the hide animation of the soft keyboard in the fixed state is completed, For details about the APIs used to transition the input method panel from the fixed state to the floating state, see [Input Method Service](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethodengine-panel-i.md#changeflag).

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyboardDidHide' | Yes | Event type. The value is fixed at **'keyboardDidHide'**, indicating the hide animation of the soft keyboard in the fixed state is completed. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[KeyboardInfo](arkts-arkui-window-keyboardinfo-i.md)&gt; | No | Callback used to return the information about the soft keyboard. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function keyboardDidHide can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const callback = (keyboardInfo: window.KeyboardInfo) => {
  // ...
}
try {
  windowClass.on('keyboardDidHide', callback);
  windowClass.off('keyboardDidHide', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('keyboardDidHide');
} catch (exception) {
  console.error(`Failed to register or unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('touchOutside')

```TypeScript
off(type: 'touchOutside', callback?: Callback<void>): void
```

Unsubscribes from the touch event outside this window.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'touchOutside' | Yes | Event type. The value is fixed at **'touchOutside'**, indicating the touch event outside this window. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;void&gt; | No | Callback used to return the touch event outside this window. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Incorrect parameter types; 2. Parameter verification failed. |

**Examples**

```TypeScript
const callback = () => {
  // ...
}
try {
  windowClass.on('touchOutside', callback);
  windowClass.off('touchOutside', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('touchOutside');
} catch (exception) {
  console.error(`Failed to register or unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('displayIdChange')

```TypeScript
off(type: 'displayIdChange', callback?: Callback<number>): void
```

Unsubscribes from the display change event of this window.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'displayIdChange' | Yes | Event type. The value is fixed at **'displayIdChange'**, indicating the display change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;number&gt; | No | Callback invoked when the display where the window is located changes. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created. |

**Examples**

```TypeScript
const callback = (displayId: number) => {
  // ...
}
try {
  // Enable listening through the on API.
  windowClass.on('displayIdChange', callback);
  // Disable the listening of a specified callback.
  windowClass.off('displayIdChange', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('displayIdChange');
} catch (exception) {
  console.error(`Failed to unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('windowVisibilityChange')

```TypeScript
off(type: 'windowVisibilityChange', callback?: Callback<boolean>): void
```

Unsubscribes from the visibility status change event of this window.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'windowVisibilityChange' | Yes | Event type. The value is fixed at **'windowVisibilityChange'**, indicating the visibility status change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;boolean&gt; | No | Callback used to return the visibility status of the window. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled.<br>**Since:** 12 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
const callback = (bool: boolean) => {
  // ...
}
try {
  // Enable listening through the on API.
  windowClass.on('windowVisibilityChange', callback);
  // Disable the listening of a specified callback.
  windowClass.off('windowVisibilityChange', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('windowVisibilityChange');
} catch (exception) {
  console.error(`Failed to unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('systemDensityChange')

```TypeScript
off(type: 'systemDensityChange', callback?: Callback<number>): void
```

Unsubscribes from the system density change event.

In the callback function, you are advised to directly use the return value to convert from virtual pixels (vp) to physical pixels (px). For example, if the return value is **density**, the calculation formula is vp * density = px.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'systemDensityChange' | Yes | Event type. The value is fixed at **'systemDensityChange'**, indicating the system density change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;number&gt; | No | Callback invoked when the system's display size scale factor changes. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created. |

**Examples**

```TypeScript
const callback = (density: number) => {
  // ...
}
try {
  // Enable listening through the on API.
  windowClass.on('systemDensityChange', callback);
  // Disable the listening of a specified callback.
  windowClass.off('systemDensityChange', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('systemDensityChange');
} catch (exception) {
  console.error(`Failed to unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('noInteractionDetected')

```TypeScript
off(type: 'noInteractionDetected', callback?: Callback<void>): void
```

Unsubscribes from non-interaction events in a window within the specified period. Interaction events include physical keyboard input events and screen touch/click events, but not soft keyboard input events.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'noInteractionDetected' | Yes | Event type. The value is fixed at **'noInteractionDetected'**, indicating that there is no interaction event in the window within the specified period. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;void&gt; | No | Callback invoked when there is no interaction event in the current window within the specified period. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
const callback = () => {
  // ...
}
try {
  windowClass.on('noInteractionDetected', 60, callback);
  windowClass.off('noInteractionDetected', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('noInteractionDetected');
} catch (exception) {
  console.error(`Failed to register or unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('screenshot')

```TypeScript
off(type: 'screenshot', callback?: Callback<void>): void
```

Unsubscribes from the screenshot event.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'screenshot' | Yes | Event type. The value is fixed at **'screenshot'**, indicating the screenshot event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;void&gt; | No | Callback invoked when a screenshot event occurs. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Incorrect parameter types; 2. Parameter verification failed. |

**Examples**

```TypeScript
let callback = () => {
  console.info('screenshot happened');
};
try {
  windowClass.on('screenshot', callback);
  windowClass.off('screenshot', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('screenshot');
} catch (exception) {
  console.error(`Failed to register or unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('screenshotAppEvent')

```TypeScript
off(type: 'screenshotAppEvent', callback?: Callback<ScreenshotEventType>): void
```

Unsubscribes from the screenshot event.

**Since:** 20

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'screenshotAppEvent' | Yes | Event type. The value is fixed at **'screenshotAppEvent'**, indicating the screenshot event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[ScreenshotEventType](arkts-arkui-window-screenshoteventtype-e.md)&gt; | No | Callback invoked when a screenshot event occurs. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
const callback = (eventType: window.ScreenshotEventType) => {
  // ...
}
try {
  // Enable listening through the on API.
  windowClass.on('screenshotAppEvent', callback);
  // Disable the listening of a specified callback.
  windowClass.off('screenshotAppEvent', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('screenshotAppEvent');
} catch (exception) {
  console.error(`Failed to unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('dialogTargetTouch')

```TypeScript
off(type: 'dialogTargetTouch', callback?: Callback<void>): void
```

Unsubscribes from the touch event of the target window in the modal window mode.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'dialogTargetTouch' | Yes | Event type. The value is fixed at **'dialogTargetTouch'**, indicating the touch event of the target window in the modal window mode. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;void&gt; | No | Callback invoked when the touch event occurs in the target window of the modal window mode. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Incorrect parameter types; 2. Parameter verification failed. |

**Examples**

```TypeScript
const callback = () => {
  // ...
}
try {
  windowClass.on('dialogTargetTouch', callback);
  windowClass.off('dialogTargetTouch', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('dialogTargetTouch');
} catch (exception) {
  console.error(`Failed to register or unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('windowEvent')

```TypeScript
off(type: 'windowEvent', callback?: Callback<WindowEventType>): void
```

Unsubscribes from the window lifecycle change event.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'windowEvent' | Yes | Event type. The value is fixed at **'windowEvent'**, indicating the window lifecycle change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[WindowEventType](arkts-arkui-window-windoweventtype-e.md)&gt; | No | Callback used to return the window lifecycle state. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Incorrect parameter types; 2. Parameter verification failed. |

**Examples**

```TypeScript
const callback = (windowEventType: window.WindowEventType) => {
  // ...
}
try {
  // Enable listening through the on API.
  windowClass.on('windowEvent', callback);
  // Disable the listening of a specified callback.
  windowClass.off('windowEvent', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('windowEvent');
} catch (exception) {
  console.error(`Failed to unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('windowStatusChange')

```TypeScript
off(type: 'windowStatusChange', callback?: Callback<WindowStatusType>): void
```

Disables the listening for window status changes.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'windowStatusChange' | Yes | Event type. The value is fixed at **'windowStatusChange'**, indicating the window status change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[WindowStatusType](arkts-arkui-window-windowstatustype-e.md)&gt; | No | Callback used to return the window status. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

```TypeScript
const callback = (windowStatusType: window.WindowStatusType) => {
    // ...
}
try {
    windowClass.on('windowStatusChange', callback);
    windowClass.off('windowStatusChange', callback);
    // Unregister all the callbacks that have been registered through on().
    windowClass.off('windowStatusChange');
} catch (exception) {
    console.error(`Failed to unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('windowStatusDidChange')

```TypeScript
off(type: 'windowStatusDidChange', callback?: Callback<WindowStatusType>): void
```

Unsubscribes from the event indicating that the window status has changed.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'windowStatusDidChange' | Yes | Event type. The value is fixed at **'windowStatusDidChange'**, indicating that the window status has changed. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[WindowStatusType](arkts-arkui-window-windowstatustype-e.md)&gt; | No | Callback used to return the window status. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created. |

**Examples**

```TypeScript
const callback = (windowStatusType: window.WindowStatusType) => {
    // ...
}
try {
    windowClass.on('windowStatusDidChange', callback);
    windowClass.off('windowStatusDidChange', callback);
    // Unregister all the callbacks that have been registered through on().
    windowClass.off('windowStatusDidChange');
} catch (exception) {
    console.error(`Failed to unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('subWindowClose')

```TypeScript
off(type: 'subWindowClose', callback?: Callback<void>): void
```

Unsubscribes from the event indicating that the child window is closed.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'subWindowClose' | Yes | Event type. The value is fixed at **'subWindowClose'**, indicating the child window close event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;void&gt; | No | Callback invoked when the close button in the top-right corner of the child window is clicked. It does not return any parameter. The return value of the internal logic of the callback function determines whether to continue to close the child window. If **true** of the Boolean type is returned, the child window is not closed. If **false** or other non-Boolean types are returned, the child window is closed. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only subwindows are supported. |

**Examples**

```TypeScript
const callback = () => {
  // ...
  return true;
}
try {
  windowClass.on('subWindowClose', callback);
  windowClass.off('subWindowClose', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('subWindowClose');
} catch (exception) {
  console.error(`Failed to register or unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('windowWillClose')

```TypeScript
off(type: 'windowWillClose', callback?: Callback<void, Promise<boolean>>): void
```

Unsubscribes from the event indicating that the main window or child window will be closed.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'windowWillClose' | Yes | Event type. The value is fixed at **'windowWillClose'**, indicating the window close event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;void, Promise&lt;boolean&gt;&gt; | No | Callback invoked when the close button in the top-right corner of the window is clicked. It does not return any parameter. The internal logic of the callback function requires a return value of the Promise&lt;boolean&gt; type. In the returned Promise function, **resolve(true)** means not to close the window, and **resolve(false)** or **reject** means to continue to close the window. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Not called from mainWindow or subWindow. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    try {
      const callback = () => {
        // ...
        return new Promise<boolean>((resolve, reject) => {
          // Whether to close the window.
          let result: boolean = true;
          resolve(result);
        });
      }
      let windowClass = windowStage.getMainWindowSync();
      windowClass.on('windowWillClose', callback);
      windowClass.off('windowWillClose', callback);
      // Unregister all the callbacks that have been registered through on().
      windowClass.off('windowWillClose');
    } catch (exception) {
      console.error(`Failed to register callback. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

## off('windowHighlightChange')

```TypeScript
off(type: 'windowHighlightChange', callback?: Callback<boolean>): void
```

Unsubscribes from the highlighted state change event of the window.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'windowHighlightChange' | Yes | Event type. The value is fixed at **'windowHighlightChange'**, indicating the window highlighted state change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;boolean&gt; | No | Callback used to return the highlighted state of the window. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
const callback = (data: boolean) => {
  // ...
}
try {
  // Enable listening through the on API.
  windowClass.on('windowHighlightChange', callback);
  // Disable the listening of a specified callback.
  windowClass.off('windowHighlightChange', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('windowHighlightChange');
} catch (exception) {
  console.error(`Failed to unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('windowTitleButtonRectChange')

```TypeScript
off(type: 'windowTitleButtonRectChange', callback?: Callback<TitleButtonRect>): void
```

Unsubscribes from the change event of the rectangle that holds the minimize, maximize, and close buttons on the title bar of the window. This API takes effect for the window that has a title bar or a three-button area. In the stage model, this API must be used after the call of [loadContent](#loadcontent) or [setUIContent()](#setuicontent) takes effect.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'windowTitleButtonRectChange' | Yes | Event type. The value is fixed at **'windowTitleButtonRectChange'**, indicating that the change event of the rectangle that holds the minimize, maximize, and close buttons. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[TitleButtonRect](arkts-arkui-window-titlebuttonrect-i.md)&gt; | No | Callback used to return the new rectangle. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created. |

**Examples**

```TypeScript
windowClass.setUIContent('pages/WindowPage').then(() => {
    const callback = (titleButtonRect: window.TitleButtonRect) => {
        // ...
    }
  try {
    // Enable listening through the on API.
    windowClass?.on('windowTitleButtonRectChange', callback);
    // Disable the listening of a specified callback.
    windowClass?.off('windowTitleButtonRectChange', callback);
    // Unregister all the callbacks that have been registered through on().
    windowClass?.off('windowTitleButtonRectChange');
  } catch (exception) {
    console.error(`Failed to disable the listener for window title buttons area changes. Cause code: ${exception.code}, message: ${exception.message}`);
  }
})
```

## off('windowRectChange')

```TypeScript
off(type: 'windowRectChange', callback?: Callback<RectChangeOptions>): void
```

Unsubscribes from window rectangle (position and size) change events.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'windowRectChange' | Yes | Event type. The value is fixed at **'windowRectChange'**, indicating the window rectangle change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[RectChangeOptions](arkts-arkui-window-rectchangeoptions-i.md)&gt; | No | Callback used to return the value and reason of the window rectangle change. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
const callback = (rectChangeOptions: window.RectChangeOptions) => {
  // ...
}

try {
  windowClass.on('windowRectChange', callback);
  windowClass.off('windowRectChange', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('windowRectChange');
} catch (exception) {
  console.error(`Failed to disable the listener for window rect changes. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('rectChangeInGlobalDisplay')

```TypeScript
off(type: 'rectChangeInGlobalDisplay', callback?: Callback<RectChangeOptions>): void
```

Disables the listening event for changes in the window rectangle (window position and size) in the [global coordinate system](../../../windowmanager/window-terminology.md#global-coordinate-system).

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'rectChangeInGlobalDisplay' | Yes | Event type. The value is fixed at **'rectChangeInGlobalDisplay'**, indicating the window rectangle change event in the global coordinate system. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[RectChangeOptions](arkts-arkui-window-rectchangeoptions-i.md)&gt; | No | Callback used to return the value and reason of the window rectangle change. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
const callback = (rectChangeOptions: window.RectChangeOptions) => {
  // ...
}

try {
  windowClass.on('rectChangeInGlobalDisplay', callback);
  windowClass.off('rectChangeInGlobalDisplay', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('rectChangeInGlobalDisplay');
} catch (exception) {
  console.error(`Failed to disable the listener for window rect changes in global display. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## off('freeWindowModeChange')

```TypeScript
off(type: 'freeWindowModeChange', callback?: Callback<boolean>): void
```

Unsubscribes from the freeform window mode change event.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'freeWindowModeChange' | Yes | Event type. The value is fixed at **'freeWindowModeChange'**, indicating the freeform window mode change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;boolean&gt; | No | Callback used to return the result, indicating whether the window is in freeform window mode. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
const callback = (isInFreeWindowMode: boolean) => {
  // ...
}
try {
  // Enable listening through the on API.
  windowClass.on('freeWindowModeChange', callback);
  // Disable the listening of a specified callback.
  windowClass.off('freeWindowModeChange', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('freeWindowModeChange');
} catch (exception) {
  console.error(`Failed to disable the listener for free window mode change. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## offWindowFocusStateChange

```TypeScript
offWindowFocusStateChange(callback?: Callback<WindowFocusState>): void
```

Unregisters the callback of the window focus state change event.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[WindowFocusState](arkts-arkui-window-windowfocusstate-i.md)&gt; | No | Callback used to return the focus state change information of the window. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

## offWindowPostureModeChange

```TypeScript
offWindowPostureModeChange(mode: WindowPostureMode, callback?: Callback<boolean>): void
```

Unregisters a callback that is invoked when he window changes to the specified window posture mode.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [WindowPostureMode](arkts-arkui-window-windowposturemode-e.md) | Yes | The window posture mode to monitor. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;boolean&gt; | No | Callback function. Callback when the window changes to the specified window pose mode. If a parameter is transferred, the listener is disabled. If no parameter is specified, all callbacks for changing the current window to the specified window posture mode are closed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: The internal services of the window are not started normally. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: Invalid parameter range. |

## on('rotationChange')

```TypeScript
on(type: 'rotationChange', callback: RotationChangeCallback<RotationChangeInfo, RotationChangeResult | void>): void
```

Subscribes to the window rotation change event. If the window rotation event type in [RotationChangeInfo](arkts-arkui-window-rotationchangeinfo-i.md) is **WINDOW_WILL_ROTATE**, [RotationChangeResult](arkts-arkui-window-rotationchangeresult-i.md) must be returned. If the window rotation event type is **WINDOW_DID_ROTATE**, [RotationChangeResult](arkts-arkui-window-rotationchangeresult-i.md) does not take effect.

This API can be registered only on the main thread. If a window registers multiple callbacks of the same type, only the return value of the most recently registered callback will be effective. The system provides a timeout protection mechanism. If the window does not return [RotationChangeResult](arkts-arkui-window-rotationchangeresult-i.md) within 20 ms, the system does not process the return value.

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'rotationChange' | Yes | Event type. The value is fixed at **'rotationChange'**, indicating the window rotation change event. |
| callback | [RotationChangeCallback](arkts-arkui-window-rotationchangecallback-t.md)&lt;[RotationChangeInfo](arkts-arkui-window-rotationchangeinfo-i.md), [RotationChangeResult](arkts-arkui-window-rotationchangeresult-i.md) &#124; void&gt; | Yes | Callback used to return [RotationChangeInfo](arkts-arkui-window-rotationchangeinfo-i.md) and [RotationChangeResult](arkts-arkui-window-rotationchangeresult-i.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

function calculateRect(info: window.RotationChangeInfo): window.Rect {
  // calculate result with info
  let rect: window.Rect = {
    left: 0,
    top: 0,
    width: 500,
    height: 600,
  };
  return rect;
}

function callback(info: window.RotationChangeInfo): window.RotationChangeResult | void {
  let result: window.RotationChangeResult = {
    rectType: window.RectType.RELATIVE_TO_SCREEN,
    windowRect: {
      left: 0,
      top: 0,
      width: 0,
      height: 0,
    }
  };

  if (info.type === window.RotationChangeType.WINDOW_WILL_ROTATE) {
    result.rectType = window.RectType.RELATIVE_TO_SCREEN;
    result.windowRect = calculateRect(info);
    return result;
  } else {
    // do something after rotate
    return;
  }
}

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    let windowClass: window.Window | undefined = undefined;
    let config: window.Configuration = {
      name: 'test',
      windowType: window.WindowType.TYPE_DIALOG,
      ctx: this.context
    };

    try {
      window.createWindow(config, (err: BusinessError, data: window.Window) => {
        const errCode: number = err.code;
        if (errCode) {
          console.error(`Failed to create the window. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        windowClass = data;
        try {
          windowClass.on('rotationChange', callback);
        } catch (exception) {
          console.error(`Failed to register callback. Cause code: ${exception.code}, message: ${exception.message}`);
        }
        windowClass.resize(500, 1000);
      });
    } catch (exception) {
      console.error(`Failed to create the window. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

<a id="on-1"></a>

## on

```TypeScript
on(eventType: 'uiExtensionSecureLimitChange', callback: Callback<boolean>): void
```

Subscribes to the event indicating changes in the security restrictions of the UIExtensionAbility within the window. You are advised to initiate the subscription right after the window is created.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| eventType | 'uiExtensionSecureLimitChange' | Yes | Event type. The value is fixed at **'uiExtensionSecureLimitChange'**, indicating that the UIExtensionAbility security restrictions in the window changes. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** means that at least one UIExtensionAbility within the window has enabled the hiding of unsafe windows, and **false** means that all UIExtensionAbility components within the window have disabled the hiding of unsafe windows. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function on('uiExtensionSecureLimitChange') cannot work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
try {
  windowClass.on('uiExtensionSecureLimitChange', (data: boolean) => {
    console.info(`Window secure limit Change: ${data}`);
  });
} catch (exception) {
  console.error(`Failed to register callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('frameMetricsMeasured')

```TypeScript
on(type: 'frameMetricsMeasured', callback: Callback<FrameMetrics>): void
```

Subscribes to events indicating changes in window frame metrics. This API must be used after the call of [loadContent](#loadcontent) or [setUIContent()](#setuicontent) takes effect.

The callback is triggered only when the client UI content is redrawn (for example, during page transitions, interactions with responsive components, setting background colors, or adjusting opacity).

**Since:** 22

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'frameMetricsMeasured' | Yes | Event type. The value is fixed at **'frameMetricsMeasured'**, indicating the window frame metrics change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[FrameMetrics](arkts-arkui-window-framemetrics-i.md)&gt; | Yes | Callback invoked when the window frame metrics change. For details, see [Frame Rate Metrics](arkts-arkui-window-framemetrics-i.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |

**Examples**

```TypeScript
try {
  let callback: Callback<window.FrameMetrics> = (data: window.FrameMetrics) => {
    console.info(`Window frame metrics changed: ${JSON.stringify(data)}`);
  };
  windowClass.on('frameMetricsMeasured', callback);
} catch (exception) {
  console.error(`Failed to register callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('occlusionStateChanged')

```TypeScript
on(type: 'occlusionStateChanged', callback: Callback<OcclusionState>): void
```

Subscribes to the visibility status change event of the window. The visibility returned by this API may be different from that perceived by human eyes in the following scenarios:

- If the shadow area of a non-main window ([setWindowShadowEnabled](#setwindowshadowenabled) and [setWindowShadowRadius](#setwindowshadowradius) can be used to set whether the shadow area is displayed and the shadow radius,respectively) is blocked, the window will be considered as partially visible even though it is completely visible to human eyes.  
- If the upper-layer window has a transparency effect (including all transparency degrees except the completely  
opaque degree), the lower-layer window will not be blocked and is visible.  
- Most windows with animation effects do not block lower-layer windows. For example, when you drag a floating  
window on a mobile phone, the lower-layer window returned remains visible.

**Since:** 22

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'occlusionStateChanged' | Yes | Event type. The value is fixed at **'occlusionStateChanged'**, indicating the window visibility status change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[OcclusionState](arkts-arkui-window-occlusionstate-e.md)&gt; | Yes | Callback invoked when the window visibility status changes. For details, see [Window Visibility Status](arkts-arkui-window-occlusionstate-e.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
try {
  let callback: Callback<window.OcclusionState> = (data: window.OcclusionState) => {
    console.info(`Window occlusion state changed: ${data}`);
  };
  windowClass.on('occlusionStateChanged', callback);
} catch (exception) {
  console.error(`Failed to register callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('windowSizeChange')

```TypeScript
on(type: 'windowSizeChange', callback: Callback<Size>): void
```

Subscribes to the window size change event. This API can be called only by the main thread.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'windowSizeChange' | Yes | Event type. The value is fixed at **'windowSizeChange'**, indicating the window size change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;Size&gt; | Yes | Callback used to return the window size. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
try {
  windowClass.on('windowSizeChange', (data) => {
    console.info('Succeeded in enabling the listener for window size changes. Data: ' + JSON.stringify(data));
  });
} catch (exception) {
  console.error(`Failed to enable the listener for window size changes. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('systemAvoidAreaChange')

```TypeScript
on(type: 'systemAvoidAreaChange', callback: Callback<AvoidArea>): void
```

Subscribes to the event indicating changes to the area where this window cannot be displayed.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [on](#onavoidareachange)(type: 'avoidAreaChange', callback: Callback&lt;AvoidAreaOptions&gt;)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'systemAvoidAreaChange' | Yes | Event type. The value is fixed at **'systemAvoidAreaChange'**, indicating the event of changes to the area where the window cannot be displayed. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[AvoidArea](arkts-arkui-window-avoidarea-i.md)&gt; | Yes | Callback used to return the area. |

**Examples**

```TypeScript
windowClass.on('systemAvoidAreaChange', (data) => {
  console.info('Succeeded in enabling the listener for system avoid area changes. Data: ' + JSON.stringify(data));
});
```

## on('avoidAreaChange')

```TypeScript
on(type: 'avoidAreaChange', callback: Callback<AvoidAreaOptions>): void
```

Subscribes to the event indicating changes to the area where this window cannot be displayed.

Main window/Child window:

- When the callback is triggered in the free-floating window mode (the window mode is  
**window.WindowStatusType.FLOATING**) under the [freeform window](../../../windowmanager/window-terminology.md#freeform-window) state, only the avoidance area of the fixed soft keyboard type ([AvoidAreaType](arkts-arkui-window-avoidareatype-e.md) is **TYPE_KEYBOARD**) is available.  
- When the callback is triggered in the free-floating window mode of the main window in the non-freeform window  
state, only the avoidance area of the system bar type ([AvoidAreaType](arkts-arkui-window-avoidareatype-e.md) is **TYPE_SYSTEM**) is available.  
- When the callback is triggered in the other scenarios of the main window, the calculated avoidance area can be  
returned only when the window is not in the free-floating window mode or the device type is phone or tablet. Otherwise, an empty avoidance area is returned.  
- When the callback is triggered for the child window in the non-freeform window state or non-free-floating  
window mode, the calculated avoidance area of the child window is returned only when the position and size of the child window are the same as those of the main window. Otherwise, an empty avoidance area is returned.

Global floating window, modal window, or system window:

- The calculated avoidance area is returned only when the callback is triggered after [setSystemAvoidAreaEnabled](#setsystemavoidareaenabled) is called. Otherwise, an empty avoidance area is returned.

&lt;!--RP7--&gt;Common scenarios for triggering this event are as follows: transitions between full-screen mode, floating mode, and split-screen mode of the application window; rotation of the application window; transitions between folded and unfolded states of a foldable device; transfer of the application window between multiple devices.&lt;!--RP7End--&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'avoidAreaChange' | Yes | Event type. The value is fixed at **'avoidAreaChange'**, indicating the event of changes to the area where the window cannot be displayed. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[AvoidAreaOptions](arkts-arkui-window-avoidareaoptions-i.md)&gt; | Yes | Callback used to return the area and area type.<br>**Since:** 12 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
try {
  windowClass.on('avoidAreaChange', (data) => {
    console.info('Succeeded in enabling the listener for system avoid area changes. type:' +
    JSON.stringify(data.type) + ', area: ' + JSON.stringify(data.area));
  });
} catch (exception) {
  console.error(`Failed to enable the listener for system avoid area changes. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('keyboardHeightChange')

```TypeScript
on(type: 'keyboardHeightChange', callback: Callback<number>): void
```

Subscribes to the event indicating soft keyboard height changes in the fixed state. The system notifies the keyboard height change when the soft keyboard is invoked by the window and overlaps with the window. Starting from API version 10, the soft keyboard can be set to the fixed or floating state. For details, see [Input Method Service](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethodengine-panel-i.md#changeflag).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyboardHeightChange' | Yes | Event type. The value is fixed at **'keyboardHeightChange'**, indicating the keyboard height change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;number&gt; | Yes | Callback used to return the current keyboard height, which is an integer, in px. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  windowClass.on('keyboardHeightChange', (data) => {
    console.info('Succeeded in enabling the listener for keyboard height changes. Data: ' + JSON.stringify(data));
  });
} catch (exception) {
  console.error(`Failed to enable the listener for keyboard height changes. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('keyboardWillShow')

```TypeScript
on(type: 'keyboardWillShow', callback: Callback<KeyboardInfo>): void
```

Subscribes to the event indicating that the soft keyboard in the fixed state is about to show, or the soft keyboard is transitioning from the floating state to the fixed state.

For details about the APIs used to set the soft keyboard to the fixed or floating state, see [Input Method Service](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethodengine-panel-i.md#changeflag).

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyboardWillShow' | Yes | Event type. The value is fixed at **'keyboardWillShow'**, indicating the soft keyboard in the fixed state is about to show. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[KeyboardInfo](arkts-arkui-window-keyboardinfo-i.md)&gt; | Yes | Callback used to return the information about the soft keyboard. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function keyboardWillShow can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const callback = (keyboardInfo: window.KeyboardInfo) => {
  console.info(`Keyboard will show animation. keyboardInfo: ` + JSON.stringify(keyboardInfo));
}
try {
  windowClass.on('keyboardWillShow', callback);
  console.info(`Register keyboard will show animation success`);
} catch (exception) {
  console.error(`Failed to register or unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('keyboardDidShow')

```TypeScript
on(type: 'keyboardDidShow', callback: Callback<KeyboardInfo>): void
```

Subscribes to the event indicating that the show animation of the soft keyboard in the fixed state is completed, or when the soft keyboard finishes transitioning from the floating state to the fixed state.

For details about the APIs used to set the soft keyboard to the fixed or floating state, see [Input Method Service](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethodengine-panel-i.md#changeflag).

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyboardDidShow' | Yes | Event type. The value is fixed at **'keyboardDidShow'**, indicating the show animation of the soft keyboard in the fixed state is completed. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[KeyboardInfo](arkts-arkui-window-keyboardinfo-i.md)&gt; | Yes | Callback used to return the information about the soft keyboard. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function keyboardDidShow can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  windowClass.on('keyboardDidShow', (keyboardInfo) => {
    console.info('keyboard show animation completion. keyboardInfo: ' + JSON.stringify(keyboardInfo));
  });
} catch (exception) {
  console.error(`Failed to register callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('keyboardWillHide')

```TypeScript
on(type: 'keyboardWillHide', callback: Callback<KeyboardInfo>): void
```

Subscribes to the event indicating that the soft keyboard in the fixed state is about to hide, or the soft keyboard is transitioning from the fixed state to the floating state.

For details about the APIs used to set the soft keyboard to the fixed or floating state, see [Input Method Service](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethodengine-panel-i.md#changeflag).

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyboardWillHide' | Yes | Event type. The value is fixed at **'keyboardWillHide'**, indicating the soft keyboard in the fixed state is about to hide. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[KeyboardInfo](arkts-arkui-window-keyboardinfo-i.md)&gt; | Yes | Callback used to return the information about the soft keyboard. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function keyboardWillHide can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const callback = (keyboardInfo: window.KeyboardInfo) => {
  console.info(`Keyboard will hide animation. keyboardInfo: ` + JSON.stringify(keyboardInfo));
}
try {
  windowClass.on('keyboardWillHide', callback);
  console.info(`Register keyboard will hide animation success`);
} catch (exception) {
  console.error(`Failed to register or unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('keyboardDidHide')

```TypeScript
on(type: 'keyboardDidHide', callback: Callback<KeyboardInfo>): void
```

Subscribes to the event indicating that the hide animation of the soft keyboard in the fixed state is completed, or when the soft keyboard finishes transitioning from the fixed state to the floating state.

For details about the APIs used to set the soft keyboard to the fixed or floating state, see [Input Method Service](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethodengine-panel-i.md#changeflag).

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyboardDidHide' | Yes | Event type. The value is fixed at **'keyboardDidHide'**, indicating the hide animation of the soft keyboard in the fixed state is completed. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[KeyboardInfo](arkts-arkui-window-keyboardinfo-i.md)&gt; | Yes | Callback used to return the information about the soft keyboard. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function keyboardDidHide can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  windowClass.on('keyboardDidHide', (keyboardInfo) => {
    console.info('keyboard hide animation completion. keyboardInfo: ' + JSON.stringify(keyboardInfo));
  });
} catch (exception) {
  console.error(`Failed to register callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('touchOutside')

```TypeScript
on(type: 'touchOutside', callback: Callback<void>): void
```

Subscribes to the touch event outside this window.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'touchOutside' | Yes | Event type. The value is fixed at **'touchOutside'**, indicating the touch event outside this window. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;void&gt; | Yes | Callback used to return the touch event outside this window. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
try {
  windowClass.on('touchOutside', () => {
    console.info('touch outside');
  });
} catch (exception) {
  console.error(`Failed to register callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('displayIdChange')

```TypeScript
on(type: 'displayIdChange', callback: Callback<number>): void
```

Subscribes to the display change event of this window. For example, this event is triggered when the window is moved to a different display.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'displayIdChange' | Yes | Event type. The value is fixed at **'displayIdChange'**, indicating the display change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;number&gt; | Yes | Callback invoked when the display where the window is located changes. The callback contains a parameter of the number type, indicating the new display ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |

**Examples**

```TypeScript
try {
  windowClass.on('displayIdChange', (data) => {
    console.info('Window displayId changed, displayId=' + JSON.stringify(data));
  });
} catch (exception) {
  console.error(`Failed to register callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('windowVisibilityChange')

```TypeScript
on(type: 'windowVisibilityChange', callback: Callback<boolean>): void
```

Subscribes to the visibility status change event of this window. The visibility returned by this API may be different from that perceived by human eyes in the following scenarios:

- If the shadow area of a non-main window ([setWindowShadowEnabled](#setwindowshadowenabled) and [setWindowShadowRadius](#setwindowshadowradius) can be used to set whether the shadow area is displayed and the shadow radius,respectively) is blocked, the window will be considered as partially visible even though it is completely visible to human eyes.  
- If the upper-layer window has a transparency effect (including all transparency degrees except the completely  
opaque degree), the lower-layer window will not be blocked and is visible.  
- Most windows with animation effects do not block lower-layer windows. For example, when you drag a floating  
window on a mobile phone, the lower-layer window returned remains visible.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'windowVisibilityChange' | Yes | Event type. The value is fixed at **'windowVisibilityChange'**, indicating the visibility status change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;boolean&gt; | Yes | Callback used to return the visibility status of the window, which is a Boolean value. **true** if visible, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
try {
  windowClass.on('windowVisibilityChange', (boolean) => {
    console.info('Window visibility changed, isVisible=' + boolean);
  });
} catch (exception) {
  console.error(`Failed to register callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('systemDensityChange')

```TypeScript
on(type: 'systemDensityChange', callback: Callback<number>): void
```

Subscribes to the system density change event, which is triggered when the system's display size scale factor changes for the screen where the window is located.

In the callback function, you are advised to directly use the return value to convert from virtual pixels (vp) to physical pixels (px). For example, if the return value is **density**, the calculation formula is vp * density = px.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'systemDensityChange' | Yes | Event type. The value is fixed at **'systemDensityChange'**, indicating the system density change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;number&gt; | Yes | Callback invoked when the system's display size scale factor changes. The callback contains a parameter of the number type, indicating the new scale factor. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |

**Examples**

```TypeScript
const callback = (density: number) => {
  console.info('System density changed, density=' + JSON.stringify(density));
  // Calculate px using the return value.
  let vp = 100;
  let px = vp * density;
}
try {
  windowClass.on('systemDensityChange', callback);
} catch (exception) {
  console.error(`Failed to register callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('noInteractionDetected')

```TypeScript
on(type: 'noInteractionDetected', timeout: number, callback: Callback<void>): void
```

Register the callback function that has no interaction for a long time. Interaction events include physical keyboard input events and screen touch/click events, but not soft keyboard input events.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'noInteractionDetected' | Yes | The value is fixed at 'noInteractionDetected', indicating the window has no interaction for a long time. |
| timeout | number | Yes | The timeout(in seconds) of no interaction detection. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;void&gt; | Yes | Callback used to notify the window has no interaction for a long time. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed; |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
try {
  windowClass.on('noInteractionDetected', 60, () => {
    console.info('no interaction in 60s');
  });
} catch (exception) {
  console.error(`Failed to register callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('screenshot')

```TypeScript
on(type: 'screenshot', callback: Callback<void>): void
```

Subscribes to the screenshot event.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'screenshot' | Yes | Event type. The value is fixed at **'screenshot'**, covering screenshot events initiated from the Control Panel, by running hdc commands, or by calling the screenshot interfaces. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;void&gt; | Yes | Callback invoked when a screenshot event occurs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
try {
  windowClass.on('screenshot', () => {
    console.info('screenshot happened');
  });
} catch (exception) {
  console.error(`Failed to register callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('screenshotAppEvent')

```TypeScript
on(type: 'screenshotAppEvent', callback: Callback<ScreenshotEventType>): void
```

Subscribes to the screenshot event.

**Since:** 20

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'screenshotAppEvent' | Yes | Event type. The value is fixed at **'screenshotAppEvent'**, covering screenshot events from the Control Panel, shortcut keys, and scroll capture. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[ScreenshotEventType](arkts-arkui-window-screenshoteventtype-e.md)&gt; | Yes | Callback invoked when a screenshot event occurs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
const callback = (eventType: window.ScreenshotEventType) => {
  console.info(`screenshotAppEvent happened. Event: ${eventType}`);
}
try {
  windowClass.on('screenshotAppEvent', callback);
} catch (exception) {
  console.error(`Failed to register callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('dialogTargetTouch')

```TypeScript
on(type: 'dialogTargetTouch', callback: Callback<void>): void
```

Subscribes to click or touch events in a window covered by a modal window. This API takes effect only when it is called by a modal window.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'dialogTargetTouch' | Yes | Event type. The value is fixed at **'dialogTargetTouch'**, indicating the click or touch event in a window covered by a modal window. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;void&gt; | Yes | Callback invoked when a click or touch event occurs in the window covered by the modal window. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
try {
  windowClass.on('dialogTargetTouch', () => {
    console.info('touch dialog target');
  });
} catch (exception) {
  console.error(`Failed to register callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('windowEvent')

```TypeScript
on(type: 'windowEvent', callback: Callback<WindowEventType>): void
```

Subscribes to the window lifecycle change event.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'windowEvent' | Yes | Event type. The value is fixed at **'windowEvent'**, indicating the window lifecycle change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[WindowEventType](arkts-arkui-window-windoweventtype-e.md)&gt; | Yes | Callback used to return the window lifecycle state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
try {
  windowClass.on('windowEvent', (data) => {
    console.info('Window event happened. Event:' + JSON.stringify(data));
  });
} catch (exception) {
  console.error(`Failed to register callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('windowStatusChange')

```TypeScript
on(type: 'windowStatusChange', callback: Callback<WindowStatusType>): void
```

Enables the listening for window status changes. When the window status changes, a notification is sent. (In this case, the window attributes may not be updated yet. If you need to obtain the changed window size and position immediately after receiving the window status change notification, you are advised to use [on('windowStatusDidChange')](#onwindowstatusdidchange).)

After the listening is enabled using this API, multiple callbacks will be received when the **maximize** or **recover** method is called. To obtain the deduplicated callback, you can use [on('windowStatusDidChange')](#onwindowstatusdidchange).

> **NOTE:** 
> 
> In [freeform window](../../../windowmanager/window-terminology.md#freeform-window) mode, when the window is
> maximized (covering the entire screen, with a dock bar and status bar on 2-in-1 devices, and a status bar on
> tablets), the return value differs based on the
> [targetAPIVersion](../../../quick-start/app-configuration-file.md#tags-in-the-configuration-file) setting. For
> versions below 14, the return value is **WindowStatusType::FULL_SCREEN**. For versions 14 and above, the return
> value is **WindowStatusType::MAXIMIZE**.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'windowStatusChange' | Yes | Event type. The value is fixed at **'windowStatusChange'**, indicating the window status change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[WindowStatusType](arkts-arkui-window-windowstatustype-e.md)&gt; | Yes | Callback used to return the window status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

```TypeScript
try {
    windowClass.on('windowStatusChange', (WindowStatusType) => {
        console.info('Succeeded in enabling the listener for window status changes. Data: ' + JSON.stringify(WindowStatusType));
    });
} catch (exception) {
    console.error(`Failed to unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('windowStatusDidChange')

```TypeScript
on(type: 'windowStatusDidChange', callback: Callback<WindowStatusType>): void
```

Subscribes to the event indicating that the window status has changed (the [Rect](arkts-arkui-window-rect-i.md) property of the window has been updated).

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'windowStatusDidChange' | Yes | Event type. The value is fixed at **'windowStatusDidChange'**, indicating that the window status has changed. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[WindowStatusType](arkts-arkui-window-windowstatustype-e.md)&gt; | Yes | Callback used to return the window status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |

**Examples**

```TypeScript
try {
    windowClass.on('windowStatusDidChange', (WindowStatusType) => {
        console.info(`Succeeded in enabling the listener for window status changes. Data: ${JSON.stringify(WindowStatusType)}`);
    });
} catch (exception) {
    console.error(`Failed to unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('subWindowClose')

```TypeScript
on(type: 'subWindowClose', callback: Callback<void>): void
```

Subscribes to the event indicating that the child window is closed. This event is triggered only when the user clicks the system-provided close button in the top-right corner to close the child window. It is not triggered when the child window is closed in other ways.

If the event is subscribed to multiple times, only the most recently subscribed-to event takes effect.

The callback function in this API is executed synchronously. For asynchronous close events of child windows, refer to [on('windowWillClose')](#onwindowwillclose).

If there is an existing event subscribed to by calling [on('windowWillClose')](#onwindowwillclose), only the [on('windowWillClose')](#onwindowwillclose) API will be responded to.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'subWindowClose' | Yes | Event type. The value is fixed at **'subWindowClose'**, indicating the child window close event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;void&gt; | Yes | Callback invoked when the close button in the top-right corner of the child window is clicked. It does not return any parameter. The return value of the internal logic of the callback function determines whether to continue to close the child window. If **true** of the Boolean type is returned, the child window is not closed. If **false** or other non-Boolean types are returned, the child window is closed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only subwindows are supported. |

**Examples**

```TypeScript
const callback = () => {
  // ...
  return true;
}
try {
  windowClass.on('subWindowClose', callback);
} catch (exception) {
  console.error(`Failed to register callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('windowWillClose')

```TypeScript
on(type: 'windowWillClose', callback: Callback<void, Promise<boolean>>): void
```

Subscribes to the event indicating that the main window or child window will be closed. This event is triggered only when the user clicks the close button in the system-provided title bar to close the window. It is not triggered when the window is closed in other ways.

The callback function in this API is executed asynchronously. For synchronous close events of child windows, refer to [on('subWindowClose')](#onsubwindowclose). For synchronous close events of the main window, refer to on('windowStageClose').

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'windowWillClose' | Yes | Event type. The value is fixed at **'windowWillClose'**, indicating the window close event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;void, Promise&lt;boolean&gt;&gt; | Yes | Callback invoked when the close button in the top-right corner of the window is clicked. It does not return any parameter. The internal logic of the callback function requires a return value of the Promise&lt;boolean&gt; type. In the returned Promise function, **resolve(true)** means not to close the window, and **resolve(false)** or **reject** means to continue to close the window. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Not called from mainWindow or subWindow. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    const callback = () => {
      // ...
      return new Promise<boolean>((resolve, reject) => {
        // Whether to close the window.
        let result: boolean = true;
        resolve(result);
      });
    }
    try {
      let windowClass = windowStage.getMainWindowSync();
      windowClass.on('windowWillClose', callback);
    } catch (exception) {
      console.error(`Failed to register callback. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

## on('windowHighlightChange')

```TypeScript
on(type: 'windowHighlightChange', callback: Callback<boolean>): void
```

Subscribes to the highlighted state change event of the window.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'windowHighlightChange' | Yes | Event type. The value is fixed at **'windowHighlightChange'**, indicating the window highlighted state change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;boolean&gt; | Yes | Callback used to return the highlighted state of the window, which is a Boolean value. **true** if highlighted, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
try {
  windowClass.on('windowHighlightChange', (data: boolean) => {
    console.info(`Window highlight Change: ${data}`);
  });
} catch (exception) {
  console.error(`Failed to register callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('windowTitleButtonRectChange')

```TypeScript
on(type: 'windowTitleButtonRectChange', callback: Callback<TitleButtonRect>): void
```

Subscribes to the change event of the rectangle that holds the minimize, maximize, and close buttons on the title bar of the window. This API takes effect for the window that has a title bar or a three-button area. In the stage model, this API must be used after the call of [loadContent](#loadcontent) or [setUIContent()](#setuicontent) takes effect.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'windowTitleButtonRectChange' | Yes | Event type. The value is fixed at **'windowTitleButtonRectChange'**, indicating that the change event of the rectangle that holds the minimize, maximize, and close buttons. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[TitleButtonRect](arkts-arkui-window-titlebuttonrect-i.md)&gt; | Yes | Callback used to return the new rectangle. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |

**Examples**

```TypeScript
windowClass.setUIContent('pages/WindowPage').then(() => {
  try {
    windowClass?.on('windowTitleButtonRectChange', (titleButtonRect) => {
      console.info('Succeeded in enabling the listener for window title buttons area changes. Data: ' + JSON.stringify(titleButtonRect));
    });
  } catch (exception) {
    console.error(`Failed to enable the listener for window title buttons area changes. Cause code: ${exception.code}, message: ${exception.message}`);
  }
})
```

## on('windowRectChange')

```TypeScript
on(type: 'windowRectChange', callback: Callback<RectChangeOptions>): void
```

Subscribes to window rectangle (position and size) change events.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'windowRectChange' | Yes | Event type. The value is fixed at **'windowRectChange'**, indicating the window rectangle change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[RectChangeOptions](arkts-arkui-window-rectchangeoptions-i.md)&gt; | Yes | Callback used to return the value and reason of the window rectangle change. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
try {
  windowClass.on('windowRectChange', (data: window.RectChangeOptions) => {
      console.info(`Succeeded in enabling the listener for window rect changes. Data: ${JSON.stringify(data)}`);
  });
} catch (exception) {
  console.error(`Failed to disable the listener for window rect changes. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('rectChangeInGlobalDisplay')

```TypeScript
on(type: 'rectChangeInGlobalDisplay', callback: Callback<RectChangeOptions>): void
```

Enables the listening event for changes in the window rectangle (window position and size) in the [global coordinate system](../../../windowmanager/window-terminology.md#global-coordinate-system).

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'rectChangeInGlobalDisplay' | Yes | Event type. The value is fixed at **'rectChangeInGlobalDisplay'**, indicating the window rectangle change event in the global coordinate system. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[RectChangeOptions](arkts-arkui-window-rectchangeoptions-i.md)&gt; | Yes | Callback used to return the value and reason of the window rectangle change. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
const callback = (rectChangeOptions: window.RectChangeOptions) => {
  console.info(`Succeeded in enabling the listener for window rect changes in global display. Data: ` + JSON.stringify(rectChangeOptions));
}

try {
  windowClass.on('rectChangeInGlobalDisplay', callback);
} catch (exception) {
  console.error(`Failed to enable the listener for window rect changes in global display. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('freeWindowModeChange')

```TypeScript
on(type: 'freeWindowModeChange', callback: Callback<boolean>): void
```

Subscribes to the freeform window mode change event.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'freeWindowModeChange' | Yes | Event type. The value is fixed at **'freeWindowModeChange'**, indicating the freeform window mode change event. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result, indicating whether the window is in freeform window mode. **true** if the window is in freeform window mode, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
try {
  windowClass.on('freeWindowModeChange', (data) => {
    console.info('Succeeded in enabling the listener for free window mode changes. Data: ' + JSON.stringify(data));
  });
} catch (exception) {
  console.error(`Failed to enable the listener for free window mode changes. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## onWindowFocusStateChange

```TypeScript
onWindowFocusStateChange(callback: Callback<WindowFocusState>): void
```

Registers the callback of the window focus state change event.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[WindowFocusState](arkts-arkui-window-windowfocusstate-i.md)&gt; | Yes | Callback used to return the focus state change information of the window, including whether the window gains focus, the reason for the change, and the IDs of the adjacent focused windows in the same process. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

## onWindowPostureModeChange

```TypeScript
onWindowPostureModeChange(mode: WindowPostureMode, callback: Callback<boolean>): void
```

Registers a callback that is invoked when the window changes to the specified window posture mode.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [WindowPostureMode](arkts-arkui-window-windowposturemode-e.md) | Yes | The window posture mode to monitor. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;boolean&gt; | Yes | Callback invoked when the window change into the specified window posture mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: The internal services of the window are not started normally. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: Invalid parameter range. |

<a id="raisetoapptop-1"></a>

## raiseToAppTop

```TypeScript
raiseToAppTop(): Promise<void>
```

Brings a child window to the top. This action is limited to child windows of the same type under the same parent window within the current application. For child windows with a custom zLevel property, it only applies to child windows with the same zLevel value under the same parent window within the current application. This API uses a promise to return the result.

Before calling this API, ensure that the child window has been created and [showWindow()](#showwindow) has been successfully executed.

**Since:** 14

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. The window is not shown. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only subwindows are supported. |
| [1300009](../errorcode-window.md#1300009-invalid-parent-window) | The parent window is invalid. Possible cause: The parent window does not exist or has been destroyed. |

**Examples**

```TypeScript
// EntryAbility.ets
import { window } from '@kit.ArkUI';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    // Create a child window.
    windowStage.createSubWindow('testSubWindow').then((subWindow) => {
      if (subWindow == null) {
        console.error('Failed to create the subWindow. Cause: The data is empty');
        return;
      }
      subWindow.showWindow().then(() => {
        subWindow.raiseToAppTop().then(() => {
          console.info('Succeeded in raising window to app top');
        }).catch((err: BusinessError)=>{
          console.error(`Failed to raise window to app top. Cause code: ${err.code}, message: ${err.message}`);
        });
      });
    });
  }
}
```

## recover

```TypeScript
recover(): Promise<void>
```

Restores the main window from the full-screen, maximized, or split-screen mode to a floating window (**window.WindowStatusType.FLOATING** mode), and restores the window size and position to those before the full- screen, maximized, or split-screen mode is entered. If the main window is already in the floating window mode, nothing will happen. This API uses a promise to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300001](../errorcode-window.md#1300001-repeated-operation) | Repeated operation. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. 3. The window does not support floating mode. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    try {
      let windowClass = windowStage.getMainWindowSync();
      if (!windowClass) {
        console.error('Failed to get main window.');
        return;
      }
      let promise = windowClass.recover();
      promise.then(() => {
        console.info('Succeeded in recovering the window.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to recover the window. Cause code: ${err.code}, message: ${err.message}`);
      });
    } catch (exception) {
      console.error(`Failed to recover the window. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

<a id="recover-1"></a>

## recover

```TypeScript
recover(snapshotAnimationConfig: WindowSnapshotAnimationConfig): Promise<void>
```

Restores the main window from full-screen, maximized, or split-screen mode to a floating window, and resets its size and position to their previous values before full-screen, maximized, or split-screen mode was entered.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| snapshotAnimationConfig | [WindowSnapshotAnimationConfig](arkts-arkui-window-windowsnapshotanimationconfig-i.md) | Yes | The configuration of snapshot animation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300001](../errorcode-window.md#1300001-repeated-operation) | Repeated operation. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error; 3. The window does not support floating mode. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: 1. The snapshotAnimationConfig parameter only supports main windows. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: Invalid parameter range. |

**Examples**

See [recover](#recover)

## resetAspectRatio

```TypeScript
resetAspectRatio(callback: AsyncCallback<void>): void
```

Resets the aspect ratio of the window content layout. This API uses an asynchronous callback to return the result.

This API is valid only for the main window. After it is called, the persistently saved aspect ratio is cleared.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows are supported. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {

  // ...
  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    let windowClass: window.Window = windowStage.getMainWindowSync(); // Obtain the main window of the application.
    if (!windowClass) {
      console.info('Failed to load the content. Cause: windowClass is null');
    }
    try {
      windowClass.resetAspectRatio((err: BusinessError) => {
        const errCode: number = err.code;
        if (errCode) {
          console.error(`Failed to reset the aspect ratio of window. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in resetting aspect ratio of window.');
      });
    } catch (exception) {
      console.error(`Failed to reset the aspect ratio of window. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

<a id="resetaspectratio-1"></a>

## resetAspectRatio

```TypeScript
resetAspectRatio(): Promise<void>
```

Resets the aspect ratio of the window content layout. This API uses a promise to return the result.

This API is valid only for the main window. After it is called, the persistently saved aspect ratio is cleared.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows are supported. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {

  // ...
  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    let windowClass: window.Window = windowStage.getMainWindowSync(); // Obtain the main window of the application.
    if (!windowClass) {
      console.info('Failed to load the content. Cause: windowClass is null');
    }
    try {
      let promise = windowClass.resetAspectRatio();
      promise.then(() => {
        console.info('Succeeded in resetting aspect ratio of window.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to reset the aspect ratio of window. Cause code: ${err.code}, message: ${err.message}`);
      });
    } catch (exception) {
      console.error(`Failed to reset the aspect ratio of window. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

## resetSize

```TypeScript
resetSize(width: number, height: number): Promise<void>
```

Changes the size of this window based on the top-left vertex of the window. This API uses a promise to return the result.

The main window and child window have the following default size limits: [320, 1920] in width and [240, 1920] in height, both in units of vp.

The minimum width and height of the main window and child window of the application depends on the configuration on the product side. You can call [getWindowLimits](#getwindowlimits) to obtain size limits.

The system window has the following size limits: (0, 1920] in width and (0, 1920] in height, both in units of vp.

The new window width and height you set must meet the following limits:

If the window width or height is less than the minimum width or height limit, then the minimum width or height limit takes effect.

If the window width or height is greater than the maximum width or height limit, then the maximum width or height limit takes effect.

This operation is not supported in a window in full-screen mode.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [resize](#resize)(width: number, height: number)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | New width of the window, in px. The value must be an integer. If a floating-point number is passed in, the value is rounded down. A negative value is invalid, and error code [401](../../../reference/errorcode-universal.md#401-parameter-check-failed) is thrown. |
| height | number | Yes | New height of the window, in px. The value must be an integer. If a floating-point number is passed in, the value is rounded down. A negative value is invalid, and error code [401](../../../reference/errorcode-universal.md#401-parameter-check-failed) is thrown. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = windowClass.resetSize(500, 1000);
promise.then(() => {
  console.info('Succeeded in changing the window size.');
}).catch((err: BusinessError) => {
  console.error(`Failed to change the window size. Cause code: ${err.code}, message: ${err.message}`);
});
```

<a id="resetsize-1"></a>

## resetSize

```TypeScript
resetSize(width: number, height: number, callback: AsyncCallback<void>): void
```

Changes the size of this window based on the top-left vertex of the window. This API uses an asynchronous callback to return the result.

The main window and child window have the following default size limits: [320, 1920] in width and [240, 1920] in height, both in units of vp.

The minimum width and height of the main window and child window of the application depends on the configuration on the product side. You can call [getWindowLimits](#getwindowlimits) to obtain size limits.

The system window has the following size limits: (0, 1920] in width and (0, 1920] in height, both in units of vp.

The new window width and height you set must meet the following limits:

If the window width or height is less than the minimum width or height limit, then the minimum width or height limit takes effect.

If the window width or height is greater than the maximum width or height limit, then the maximum width or height limit takes effect.

This operation is not supported in a window in full-screen mode.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [resize](#resize)(width: number, height: number, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | New width of the window, in px. The value must be an integer. If a floating-point number is passed in, the value is rounded down. A negative value is invalid, and error code [401](../../../reference/errorcode-universal.md#401-parameter-check-failed) is thrown. |
| height | number | Yes | New height of the window, in px. The value must be an integer. If a floating-point number is passed in, the value is rounded down. A negative value is invalid, and error code [401](../../../reference/errorcode-universal.md#401-parameter-check-failed) is thrown. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

windowClass.resetSize(500, 1000, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to change the window size. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in changing the window size.');
});
```

## resize

```TypeScript
resize(width: number, height: number): Promise<void>
```

Changes the size of this window based on the top-left vertex of the window. This API uses a promise to return the result.

A value is returned once the API is called successfully. However, the final effect cannot be obtained immediately from the return value. To obtain the final effect immediately, call [resizeAsync()](#resizeasync).

The window size is restricted by [WindowLimits](arkts-arkui-window-windowlimits-i.md). You can call [getWindowLimits](#getwindowlimits) to find out the exact limits.

The new window width and height you set must meet the following limits:

If the window width or height is less than the minimum width or height limit, then the minimum width or height limit takes effect. However, the system window and global floating window settings are not subject to these minimum width or height restrictions.

If the window width or height is greater than the maximum width or height limit, then the maximum width or height limit takes effect.

This API takes effect only when the window is in floating window mode (**window.WindowStatusType.FLOATING**). If this API is called when the window is in other window modes, error code 1300002 is reported. (The window mode can be obtained through [getWindowStatus()](#getwindowstatus)).

> **NOTE:** 
> 
> - When the main window is in floating window mode, this API does not take effect or return an error if called in non-[freeform window](../../../windowmanager/window-terminology.md#freeform-window) state.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | New width of the window, in px. The value must be an integer. If a floating-point number is passed in, the value is rounded down. A negative value is invalid, and error code 401 is thrown. |
| height | number | Yes | New height of the window, in px. The value must be an integer. If a floating-point number is passed in, the value is rounded down. A negative value is invalid, and error code 401 is thrown. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error; 3. Invalid window status type. Only supports windows in floating window mode. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let promise = windowClass.resize(500, 1000);
  promise.then(() => {
    console.info('Succeeded in changing the window size.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to change the window size. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to change the window size. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

<a id="resize-1"></a>

## resize

```TypeScript
resize(width: number, height: number, callback: AsyncCallback<void>): void
```

Changes the size of this window based on the top-left vertex of the window. This API uses an asynchronous callback to return the result.

A value is returned once the API is called successfully. However, the final effect cannot be obtained immediately from the return value. To obtain the final effect immediately, call [resizeAsync()](#resizeasync).

The window size is restricted by [WindowLimits](arkts-arkui-window-windowlimits-i.md). You can call [getWindowLimits](#getwindowlimits) to find out the exact limits.

The new window width and height you set must meet the following limits:

If the window width or height is less than the minimum width or height limit, then the minimum width or height limit takes effect. However, the system window and global floating window settings are not subject to these minimum width or height restrictions.

If the window width or height is greater than the maximum width or height limit, then the maximum width or height limit takes effect.

> **NOTE:** 
> 
> - When the main window is in floating window mode, this API does not take effect or return an error if called in non-[freeform window](../../../windowmanager/window-terminology.md#freeform-window) state.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | New width of the window, in px. The value must be an integer. If a floating-point number is passed in, the value is rounded down. A negative value is invalid, and error code 401 is thrown. |
| height | number | Yes | New height of the window, in px. The value must be an integer. If a floating-point number is passed in, the value is rounded down. A negative value is invalid, and error code 401 is thrown. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error; 3. Invalid window status type. Only supports windows in floating window mode. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  windowClass.resize(500, 1000, (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to change the window size. Cause code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in changing the window size.');
  });
} catch (exception) {
  console.error(`Failed to change the window size. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## resizeAsync

```TypeScript
resizeAsync(width: number, height: number): Promise<void>
```

Changes the size of this window based on the top-left vertex of the window. This API uses a promise to return the result.

A value is returned once the call takes effect. You can use [getWindowProperties()](#getwindowproperties) in the callback (see the code snippet below) to obtain the final effect immediately.

The window size is restricted by [WindowLimits](arkts-arkui-window-windowlimits-i.md). You can call [getWindowLimits](#getwindowlimits) to find out the exact limits.

The new window width and height you set must meet the following limits:

If the window width or height is less than the minimum width or height limit, then the minimum width or height limit takes effect. However, the system window and global floating window settings are not subject to these minimum width or height restrictions.

If the window width or height is greater than the maximum width or height limit, then the maximum width or height limit takes effect.

This API takes effect only when the window is in floating window mode (**window.WindowStatusType.FLOATING**). In other scenarios, this API returns error code 1300010. (The window mode can be obtained through [getWindowStatus()](#getwindowstatus)).

> **NOTE:** 
> 
> - In non-[freeform window](../../../windowmanager/window-terminology.md#freeform-window) mode,this API does not work for the main window.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | New width of the window, in px. The value must be an integer. If a floating-point number is passed in, the value is rounded down. A negative value is invalid, and error code 401 is thrown. |
| height | number | Yes | New height of the window, in px. The value must be an integer. If a floating-point number is passed in, the value is rounded down. A negative value is invalid, and error code 401 is thrown. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: Invalid parameter range. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300010](../errorcode-window.md#1300010-unsupported-operation-in-the-current-window-mode) | The operation in the current window status is invalid. Possible cause: The window status is not FLOATING. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let promise = windowClass.resizeAsync(500, 1000);
  promise.then(() => {
    console.info('Succeeded in changing the window size.');
    let rect = windowClass?.getWindowProperties().windowRect;
    console.info(`Get window rect: ` + JSON.stringify(rect));
  }).catch((err: BusinessError) => {
    console.error(`Failed to change the window size. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to change the window size. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## restore

```TypeScript
restore(): Promise<void>
```

Restores the main window from minimization to the foreground, returning it to its size and position before it is minimized. This API takes effect only when the main window is minimized and the UIAbility is in the onForeground state. If the main window is already in the foreground, this API simply raises the window's layer. This API uses a promise to return the result.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows are supported. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    try {
      let windowClass = windowStage.getMainWindowSync();
      // Call minimize() to minimize the main window.
      windowClass.minimize();
      // Set the delay function to restore the main window after 5 seconds.
      setTimeout(()=>{
        // Call restore() to restore the main window.
        let promise = windowClass.restore();
        promise.then(() => {
          console.info('Succeeded in restoring the window.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to restore the window. Cause code: ${err.code}, message: ${err.message}`);
        });
      }, 5000);
    } catch (exception) {
      console.error(`Failed to restore the window. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

## restoreMainWindow

```TypeScript
restoreMainWindow(wantParameters?: Record<string, Object>): Promise<void>
```

Restores the main window of the current window to the foreground. If the main window is already in the foreground, the main window level is raised. This API is applicable only to [TYPE_FLOAT](arkts-arkui-window-windowtype-e.md) windows and can be called only after the DOWN event is triggered in the windows. This API uses a promise to return the result.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| wantParameters | Record&lt;string, Object&gt; | No | Want parameters. Custom want parameter delivered when restoring the main window. Want parameters are used for UIAbility onNewWant. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: 1. The window is not float window. 2. The window is not at foreground or has never been clicked. 3. The window cannot find main window. |
| [1300007](../errorcode-window.md#1300007-application-startup-failure-by-windowextensionability) | Restore parent main window failed. Possible cause: 1. The main window is in PAUSED lifecycle state. 2. The main window is in background during recent. |

**Examples**

```TypeScript
// Float.ets
import { window } from '@kit.ArkUI'
import { BusinessError } from '@kit.BasicServicesKit';
import { JSON } from '@kit.ArkTS';

@Entry
@Component
struct Float {
  build() {
    Button('CreateFloatWindow').onClick(() => {
      this.createFloatWindow();
    })
  }

  private createFloatWindow() {
    let windowClass: window.Window | undefined = undefined;
    let config: window.Configuration = {
      name: 'testFloatWindow',
      title: 'floatWindow',
      windowType: window.WindowType.TYPE_FLOAT,
      ctx: this.getUIContext()?.getHostContext(),
      decorEnabled: true,
    };
    try {
      window.createWindow(config, (err: BusinessError, data) => {
        const errCode: number = err.code;
        if (errCode) {
          console.error(`failed to create the window. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        windowClass = data;
        console.info(`succedded in creating the window. Data: ${JSON.stringify(data)}`);
        windowClass.resize(500, 1600).then(() => {
          console.info('Succeeded in changing the window size.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to change the window size. Cause code: ${err.code}, message: ${err.message}`);
        });
        windowClass.setUIContent("pages/FloatWindowInfo").then(() => {
          console.info('Succeeded in loading the content.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
        });
        windowClass.showWindow().then(() => {
          console.info("showWindow success");
        }).catch((err: BusinessError) => {
          console.error(`showWindow err: ${JSON.stringify(err)}`);
        });
        windowClass.moveWindowToAsync(20, 200).then(() => {
          console.info('Succeeded in moving the window.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to move the window. Cause code: ${err.code}, message: ${err.message}`);
        });
      });
    } catch (exception) {
      console.error(`failed to create the window. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

```TypeScript
// FloatWindowInfo.ets
import { window } from '@kit.ArkUI'
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct FloatWindowInfo {
  @State subWindow: window.Window | undefined = undefined;
  @State windowId: number = -1;
  async aboutToAppear(): Promise<void> {
    this.subWindow = window.findWindow('testFloatWindow');
    this.windowId = this.subWindow?.getWindowProperties()?.id;
  }

  build() {
    Column() {
      Text('Hello')
    }
    .width('100%')
    .height('100%')
    .onTouch((event: TouchEvent) => {
      // Ensure that a Down event is generated. You can determine the actual invoking time.
      if (event.type === TouchType.Down) {
        let param: Record<string, Object> = {
          "info": "helloworld",
        };
        try {
          let promise = this.subWindow?.restoreMainWindow(param);
          promise?.then(() => {
            console.info('Succeeded in restoring the main window.');
          }).catch((err: BusinessError) => {
            console.error(`Failed to restore the main window. Cause code: ${err.code}, message: ${err.message}`);
          });
        } catch (exception) {
          console.error(`Failed to restore the main window. Cause code: ${exception.code}, message: ${exception.message}`);
        }
      }
    })
  }
}
```

## setAspectRatio

```TypeScript
setAspectRatio(ratio: number, callback: AsyncCallback<void>): void
```

Sets the aspect ratio of the window content layout (excluding decorations like borders and title bars). This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> - When the window size is set by using other APIs such as [resize](#resize) and [resizeAsync](#resizeasync), the window size is not restricted by **ratio**.
> 
> - This setting is available only for the main window and takes effect only in floating window mode (
> **window.WindowStatusType.FLOATING** mode). The aspect ratio is saved persistently, which means that the
> setting is valid in floating window mode even after the application is closed or the device is restarted.
> 
> - After the aspect ratio is set for a main window of an application, the aspect ratio is used for subsequent main windows. If you need to set the aspect ratio for just one main window, use [setContentAspectRatio](#setcontentaspectratio) instead.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ratio | number | Yes | Aspect ratio of the window content layout (excluding decorations like borders and title bars). The value is a floating-point number and is restricted by the maximum and minimum sizes of the window. The minimum ratio is the value of minimum width divided by the maximum height, and the maximum ratio is the maximum width divided by the minimum height. The maximum and minimum sizes of the window are determined by the intersection of the setting of [WindowLimits](arkts-arkui-window-windowlimits-i.md) and the system limit. The system limit takes precedence over [WindowLimits](arkts-arkui-window-windowlimits-i.md). The valid range of **ratio** varies with [WindowLimits](arkts-arkui-window-windowlimits-i.md). If [WindowLimits](arkts-arkui-window-windowlimits-i.md) is set prior to **ratio**, any conflict will result in an error code when setting **ratio**. Conversely, if **ratio** is set before and then conflicts arise with the subsequently configured [WindowLimits](arkts-arkui-window-windowlimits-i.md), the window's aspect ratio may not adhere to the initially configured value of **ratio**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: Invalid parameter range. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows are supported. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {

  // ...
  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    let windowClass: window.Window = windowStage.getMainWindowSync(); // Obtain the main window of the application.
    if (!windowClass) {
      console.info('Failed to load the content. Cause: windowClass is null');
    }
    try {
      let ratio = 1.0;
      windowClass.setAspectRatio(ratio, (err: BusinessError) => {
        const errCode: number = err.code;
        if (errCode) {
          console.error(`Failed to set the aspect ratio of window. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in setting the aspect ratio of window.');
      });
    } catch (exception) {
      console.error(`Failed to set the aspect ratio of window. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

<a id="setaspectratio-1"></a>

## setAspectRatio

```TypeScript
setAspectRatio(ratio: number): Promise<void>
```

Sets the aspect ratio of the window content layout (excluding decorations like borders and title bars). This API uses a promise to return the result.

> **NOTE:** 
> 
> - When the window size is set by using other APIs such as [resize](#resize) and [resizeAsync](#resizeasync), the window size is not restricted by **ratio**.
> 
> - This setting is available only for the main window and takes effect only in floating window mode (
> **window.WindowStatusType.FLOATING** mode). The aspect ratio is saved persistently, which means that the
> setting is valid in floating window mode even after the application is closed or the device is restarted.
> 
> - After the aspect ratio is set for a main window of an application, the aspect ratio is used for subsequent main windows. If you need to set the aspect ratio for just one main window, use [setContentAspectRatio](#setcontentaspectratio) instead.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ratio | number | Yes | Aspect ratio of the window content layout (excluding decorations like borders and title bars). The value is a floating-point number and is restricted by the maximum and minimum sizes of the window. The minimum ratio is the value of minimum width divided by the maximum height, and the maximum ratio is the maximum width divided by the minimum height. The maximum and minimum sizes of the window are determined by the intersection of the setting of [WindowLimits](arkts-arkui-window-windowlimits-i.md) and the system limit. The system limit takes precedence over [WindowLimits](arkts-arkui-window-windowlimits-i.md). The valid range of **ratio** varies with [WindowLimits](arkts-arkui-window-windowlimits-i.md). If [WindowLimits](arkts-arkui-window-windowlimits-i.md) is set prior to **ratio**, any conflict will result in an error code when setting **ratio**. Conversely, if **ratio** is set before and then conflicts arise with the subsequently configured [WindowLimits](arkts-arkui-window-windowlimits-i.md), the window's aspect ratio may not adhere to the initially configured value of **ratio**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: Invalid parameter range. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows are supported. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {

  // ...
  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    let windowClass: window.Window = windowStage.getMainWindowSync(); // Obtain the main window of the application.
    if (!windowClass) {
      console.info('windowClass is null');
    }
    try {
      let ratio = 1.0;
      let promise = windowClass.setAspectRatio(ratio);
      promise.then(() => {
        console.info('Succeeded in setting aspect ratio of window.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to set the aspect ratio of window. Cause code: ${err.code}, message: ${err.message}`);
      });
    } catch (exception) {
      console.error(`Failed to set the aspect ratio of window. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

## setBackgroundColor

```TypeScript
setBackgroundColor(color: string): Promise<void>
```

Sets the background color for this window. This API uses a promise to return the result. In the stage model, this API must be used after the call of [loadContent](#loadcontent) or [setUIContent()](#setuicontent) takes effect.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [setWindowBackgroundColor](#setwindowbackgroundcolor)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | string | Yes | Background color to set. The value is a hexadecimal RGB or ARGB color code and is case insensitive, for example, **'#00FF00'** or **'#FF00FF00'**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let color: string = '#00ff33';
let promise = windowClass.setBackgroundColor(color);
promise.then(() => {
  console.info('Succeeded in setting the background color.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set the background color. Cause code: ${err.code}, message: ${err.message}`);
});
```

<a id="setbackgroundcolor-1"></a>

## setBackgroundColor

```TypeScript
setBackgroundColor(color: string, callback: AsyncCallback<void>): void
```

Sets the background color for this window. This API uses an asynchronous callback to return the result. In the stage model, this API must be used after the call of [loadContent](#loadcontent) or [setUIContent()](#setuicontent) takes effect.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [setWindowBackgroundColor](#setwindowbackgroundcolor)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | string | Yes | Background color to set. The value is a hexadecimal RGB or ARGB color code and is case insensitive, for example, **'#00FF00'** or **'#FF00FF00'**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let color: string = '#00ff33';
windowClass.setBackgroundColor(color, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to set the background color. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in setting the background color.');
});
```

## setBrightness

```TypeScript
setBrightness(brightness: number): Promise<void>
```

Sets the screen brightness for this window. This API uses a promise to return the result.

When the screen brightness setting for the window takes effect, Control Panel cannot adjust the system screen brightness. It can do so only after the window screen brightness is restored to the default value.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [setWindowBrightness](#setwindowbrightness)(brightness: number)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| brightness | number | Yes | Brightness to set. The value is a floating-point number in the range [0.0, 1.0] or is set to **-1.0**. The value **1.0** means the brightest, and **-1.0** means that the window brightness resets to the original brightness set through Control Panel. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let brightness: number = 1;
let promise = windowClass.setBrightness(brightness);
promise.then(() => {
  console.info('Succeeded in setting the brightness.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set the brightness. Cause code: ${err.code}, message: ${err.message}`);
});
```

<a id="setbrightness-1"></a>

## setBrightness

```TypeScript
setBrightness(brightness: number, callback: AsyncCallback<void>): void
```

Sets the screen brightness for this window. This API uses an asynchronous callback to return the result.

When the screen brightness setting for the window takes effect, Control Panel cannot adjust the system screen brightness. It can do so only after the window screen brightness is restored to the default value.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [setWindowBrightness](#setwindowbrightness)(brightness: number, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| brightness | number | Yes | Brightness to set. The value is a floating-point number in the range [0.0, 1.0] or is set to **-1.0**. The value **1.0** means the brightest, and **-1.0** means that the window brightness resets to the original brightness set through Control Panel. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let brightness: number = 1;
windowClass.setBrightness(brightness, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to set the brightness. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in setting the brightness.');
});
```

## setColorSpace

```TypeScript
setColorSpace(colorSpace: ColorSpace): Promise<void>
```

Sets a color space for this window. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setWindowColorSpace](#setwindowcolorspace)(colorSpace:ColorSpace)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| colorSpace | [ColorSpace](arkts-arkui-window-colorspace-e.md) | Yes | Color space to set. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = windowClass.setColorSpace(window.ColorSpace.WIDE_GAMUT);
promise.then(() => {
  console.info('Succeeded in setting window colorspace.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set window colorspace. Cause code: ${err.code}, message: ${err.message}`);
});
```

<a id="setcolorspace-1"></a>

## setColorSpace

```TypeScript
setColorSpace(colorSpace: ColorSpace, callback: AsyncCallback<void>): void
```

Sets a color space for this window. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setWindowColorSpace](#setwindowcolorspace-1)(colorSpace:ColorSpace, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| colorSpace | [ColorSpace](arkts-arkui-window-colorspace-e.md) | Yes | Color space to set. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

windowClass.setColorSpace(window.ColorSpace.WIDE_GAMUT, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to set window colorspace. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in setting window colorspace.');
});
```

## setContentAspectRatio

```TypeScript
setContentAspectRatio(ratio: number, isPersistent?: boolean, needUpdateRect?: boolean): Promise<void>
```

Sets the aspect ratio of the window content layout (excluding decorations like borders and title bars). This API uses a promise to return the result.

> **NOTE:** 
> 
> - When you adjust the window width and height using the same **ratio** parameter, the window size adapts to changes in the border decoration size or visibility.
> 
> - When the window title bar is set to invisible by using [setWindowDecorVisible](#setwindowdecorvisible), the window content area takes over the space that was previously used by the title bar.
> 
> - When the window size is set by using other APIs such as [resize](#resize) and [resizeAsync](#resizeasync), the window size is not restricted by **ratio**.
> 
> - This setting is available only for the main window and takes effect only in floating window mode (
> **window.WindowStatusType.FLOATING** mode).

**Since:** 21

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ratio | number | Yes | Aspect ratio of the window content layout (excluding decorations like borders and title bars). The value is a floating-point number and is restricted by the maximum and minimum sizes of the window. The minimum ratio is the value of minimum width divided by the maximum height, and the maximum ratio is the maximum width divided by the minimum height. The maximum and minimum sizes of the window are determined by the intersection of the setting of [WindowLimits](arkts-arkui-window-windowlimits-i.md) and the system limit. The system limit takes precedence over [WindowLimits](arkts-arkui-window-windowlimits-i.md). The valid range of **ratio** varies with [WindowLimits](arkts-arkui-window-windowlimits-i.md). If [WindowLimits](arkts-arkui-window-windowlimits-i.md) is set prior to **ratio**, any conflict will result in an error code when setting **ratio**. Conversely, if **ratio** is set before and then conflicts arise with the subsequently configured [WindowLimits](arkts-arkui-window-windowlimits-i.md), the window's aspect ratio may not adhere to the initially configured value of **ratio**. |
| isPersistent | boolean | No | Whether the aspect ratio should be saved persistently.<br>If this parameter is set to **true**, the aspect ratio is saved persistently. This means that the setting is valid in floating window mode even after the window is destroyed, the application is closed, or the device is restarted. You can call [resetAspectRatio](#resetaspectratio) to clear the persistently saved aspect ratio.<br>If this parameter is set to **false**, the aspect ratio applies only to the current window and is cleared once the window is destroyed.<br>The default value is **true**. |
| needUpdateRect | boolean | No | Whether the window size should be immediately updated based on the current aspect ratio.<br>If this parameter is set to **true**, the window size is updated immediately based on the current aspect ratio.<br>If this parameter is set to **false**, the window size is updated based on the current aspect ratio when the window is dragged and resized. You can manually trigger an update by calling [resize](#resize) or [resizeAsync](#resizeasync).<br>The default value is **true**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows are supported. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: 1. Invalid parameter range. 2. Invalid parameter length. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    try {
      let windowClass = windowStage.getMainWindowSync();
      let ratio = 1.0;
      let promise = windowClass.setContentAspectRatio(ratio, true, true);
      promise.then(() => {
        console.info('Succeeded in setting aspect ratio of window.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to set the aspect ratio of window. Cause code: ${err.code}, message: ${err.message}`);
      });
    } catch (exception) {
      console.error(`Failed to set the aspect ratio of window. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

## setDecorButtonStyle

```TypeScript
setDecorButtonStyle(dectorStyle: DecorButtonStyle): void
```

Sets the button style of the decoration bar. The setting takes effect only for the main window and child windows. In the stage model, this API must be used after the call of [loadContent](#loadcontent) or [setUIContent()](#setuicontent) takes effect.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dectorStyle | [DecorButtonStyle](arkts-arkui-window-decorbuttonstyle-i.md) | Yes | Button style of the decoration bar. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows and subwindows are supported. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { ConfigurationConstant } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    try {
      windowStage.loadContent("pages/Index").then(() =>{
        let windowClass = windowStage.getMainWindowSync();
        let colorMode : ConfigurationConstant.ColorMode = ConfigurationConstant.ColorMode.COLOR_MODE_LIGHT;
        let style: window.DecorButtonStyle = {
          colorMode: colorMode,
          buttonBackgroundSize: 28,
          spacingBetweenButtons: 12,
          closeButtonRightMargin: 20,
          buttonIconSize: 20,
          buttonBackgroundCornerRadius: 4
        };
        windowClass.setDecorButtonStyle(style);
        console.info(`Succeeded in setting the style of button. Data: ${JSON.stringify(style)}`);
      });
    } catch (exception) {
      console.error(`Failed to set the style of button. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

## setDialogBackGestureEnabled

```TypeScript
setDialogBackGestureEnabled(enabled: boolean): Promise<void>
```

Sets whether the modal window responds to the back gesture event. An error code is returned if this API is called for a non-modal window.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to respond to the back gesture event.<br>**true** means to respond to the back gesture event and trigger the **onBackPress** callback, **false** otherwise.<br> |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only dialog windows are supported. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    let config: window.Configuration = {
      name: "test",
      windowType: window.WindowType.TYPE_DIALOG,
      ctx: this.context
    };
    try {
      window.createWindow(config, (err: BusinessError, data) => {
        const errCode: number = err.code;
        if (errCode) {
          console.error(`Failed to create the window. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        windowClass = data;
        windowClass.setUIContent("pages/Index");
        let enabled = true;
        let promise = windowClass.setDialogBackGestureEnabled(enabled);
        promise.then(() => {
          console.info('Succeeded in setting dialog window to respond back gesture.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to set dialog window to respond back gesture. Cause code: ${err.code}, message: ${err.message}`);
        });
      });
    } catch (exception) {
      console.error(`Failed to create the window. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

```TypeScript
// ets/pages/Index.ets
@Entry
@Component
struct Index {
  @State message: string = 'Hello World'
  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
    }
    .height('100%')
    .width('100%')
  }

  onBackPress(): boolean | void {
    console.info('Succeeded in setting dialog window to respond back gesture.');
    return true;
  }
}
```

## setDimBehind

```TypeScript
setDimBehind(dimBehindValue: number, callback: AsyncCallback<void>): void
```

Sets the dimness of the window that is not on top. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dimBehindValue | number | Yes | Dimness of the window to set. The value range is [0.0, 1.0], and the value **1.0** means the dimmest. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

windowClass.setDimBehind(0.5, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to set the dimness. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in setting the dimness.');
});
```

<a id="setdimbehind-1"></a>

## setDimBehind

```TypeScript
setDimBehind(dimBehindValue: number): Promise<void>
```

Sets the dimness of the window that is not on top. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dimBehindValue | number | Yes | Dimness of the window to set. The value ranges from 0 to 1. The value **1** indicates the dimmest. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = windowClass.setDimBehind(0.5);
promise.then(() => {
  console.info('Succeeded in setting the dimness.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set the dimness. Cause code: ${err.code}, message: ${err.message}`);
});
```

## setDragKeyFramePolicy

```TypeScript
setDragKeyFramePolicy(keyFramePolicy: KeyFramePolicy): Promise<KeyFramePolicy>
```

Sets the keyframe policy for dragging the main window. This API uses a promise to return the result.

If this API is called by a non-main window, error code 1300004 is returned.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyFramePolicy | [KeyFramePolicy](arkts-arkui-window-keyframepolicy-i.md) | Yes | The policy of keyframe to set. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[KeyFramePolicy](arkts-arkui-window-keyframepolicy-i.md)&gt; | Promise used to return the keyframe policy that takes effect. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: 1. Invalid parameter range; 2. The parameter format is incorrect. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let keyFramePolicy: window.KeyFramePolicy = {
        enable: true
      }
      try {
        let promise = windowClass.setDragKeyFramePolicy(keyFramePolicy);
        promise.then((ret: window.KeyFramePolicy) => {
          console.info(`Succeeded in setting key frame: ${JSON.stringify(ret)}`);
        }).catch((err: BusinessError) => {
          console.error(`Failed to set key frame. Cause code: ${err.code}, message: ${err.message}`);
        });
      } catch (exception) {
        console.error(`Failed to set key frame. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

## setExclusivelyHighlighted

```TypeScript
setExclusivelyHighlighted(exclusivelyHighlighted: boolean): Promise<void>
```

Sets the exclusive highlight property for the window. When a window set to exclusive highlight gains focus, other windows in the current parent-child window chain that are in the highlighted state will lose their highlighted state. This API uses a promise to return the result.

This API does not take effect for the main window or modal window.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| exclusivelyHighlighted | boolean | Yes | Whether the window can become highlight exclusively when it gain focus. The value true means that the window can cause the window outside the current window link to lose its highlight state, and false means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Main window, dialog window and the subwindow with modal attributes are not supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let exclusivelyHighlighted: boolean = true;
try {
  let promise = windowClass.setExclusivelyHighlighted(exclusivelyHighlighted);
  promise.then(() => {
    console.info('Succeeded in setting the window to be exclusively highlight.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the window to be exclusively highlight. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set the window to be exclusively highlight. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setFloatNavigationAvoidAreaEnabled

```TypeScript
setFloatNavigationAvoidAreaEnabled(enabled: boolean): Promise<void>
```

Specifies whether to enable the avoid area for the float navigation type. When enabled, the actual value of the avoid area can be obtained by calling getWindowAvoidArea(AvoidAreaType.TYPE_FLOAT_NAVIGATION) or listening for AvoidAreaType of TYPE_FLOAT_NAVIGATION via on('avoidAreaChange') or declaring environment variables. When disabled, the float avoid area obtained through the above methods will always be 0.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | The value true means to enable float navigation avoid area, and false means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Create js value failed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
try {
  let enabled = false;
  windowClass.setFloatNavigationAvoidAreaEnabled(enabled);
} catch (exception) {
  console.error(`Failed to set the window float navigation avoid area enabled status. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setFocusable

```TypeScript
setFocusable(isFocusable: boolean): Promise<void>
```

Sets whether this window is focusable, that is, whether the window can gain focus after it is being clicked or using other methods. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setWindowFocusable](#setwindowfocusable)(isFocusable: boolean)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isFocusable | boolean | Yes | Whether the window is focusable. **true** if focusable, **false** otherwise. If this parameter is set to **false**, the window does not support binding to an input method or receiving keyboard events. If input logic needs to be processed, follow the instructions provided in [Input Box and Input Method Interaction in Non-Focus Windows](../../../inputmethod/use-inputmethod-in-not-focusable-window.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isFocusable: boolean = true;
let promise = windowClass.setFocusable(isFocusable);
promise.then(() => {
  console.info('Succeeded in setting the window to be focusable.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set the window to be focusable. Cause code: ${err.code}, message: ${err.message}`);
});
```

<a id="setfocusable-1"></a>

## setFocusable

```TypeScript
setFocusable(isFocusable: boolean, callback: AsyncCallback<void>): void
```

Sets whether this window is focusable, that is, whether the window can gain focus after it is being operated or using other methods. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setWindowFocusable](#setwindowfocusable-1)(isFocusable: boolean, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isFocusable | boolean | Yes | Whether the window is focusable. **true** if focusable, **false** otherwise. If this parameter is set to **false**, the window does not support binding to an input method or receiving keyboard events. If input logic needs to be processed, follow the instructions provided in [Input Box and Input Method Interaction in Non-Focus Windows](../../../inputmethod/use-inputmethod-in-not-focusable-window.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isFocusable: boolean = true;
windowClass.setFocusable(isFocusable, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to set the window to be focusable. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in setting the window to be focusable.');
});
```

## setFollowParentMultiScreenPolicy

```TypeScript
setFollowParentMultiScreenPolicy(enabled: boolean): Promise<void>
```

Sets whether a child window can span multiple screens and be simultaneously displayed while its parent window is being dragged or resized. This API uses a promise to return the result.

By default, when a child window follows its parent window's layout changes (by using [moveWindowTo()](#movewindowto)), it does not support spanning multiple screens and being simultaneously displayed.

However, calling this API on the child window enables it to span multiple screens and be simultaneously displayed during the layout adjustment process.

**Since:** 17

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | The value true means sub window supports simultaneous display on multiple screens when the parent window is dragged to move or dragged to zoom, and false means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.Function setFollowParentMultiScreenPolicy can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only subwindows are supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let windowClass: window.Window = window.findWindow("subWindow");
  let enabled: boolean = true;
  let promise = windowClass?.setFollowParentMultiScreenPolicy(enabled);
  promise.then(() => {
    console.info('Succeeded in setting the sub window supports multi-screen simultaneous display')
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the sub window supports multi-screen simultaneous display. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set the sub window supports multi-screen simultaneous display. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setFollowParentWindowLayoutEnabled

```TypeScript
setFollowParentWindowLayoutEnabled(enabled: boolean): Promise<void>
```

Sets whether the layout information (position and size) of a child window or modal window (a window with **WindowType** set to **TYPE_DIALOG**) follows the main window. This API uses a promise to return the result.

1. This API applies only to first-level child windows or modal windows of the main window.
2. Once this API is called on a child window or modal window, its layout information will immediately match the main window and remain synchronized. This effect will persist until this API is called again with **false**.
3. If this API is called on a child window or modal window, subsequent calls to APIs like **moveTo** or **resize** to modify the layout information will not take effect.
4. When a child window or modal window stops using this functionality, its layout information (position and size) may not be a specific value. The application needs to reset it.

Once this API is successfully called, the [setRelativePositionToParentWindowEnabled()](#setrelativepositiontoparentwindowenabled) API will no longer take effect.

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to follow the layout of the main window. **true** to follow, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. Internal task error. 3. The subwindow level is more than one. 4. The subwindow is following its parent window's position. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only subwindows and dialog windows are supported. |

**Examples**

```TypeScript
// EntryAbility.ets
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    windowStage.loadContent('pages/Index', (loadError) => {
      if (loadError.code) {
        console.error(`Failed to load the content. Cause code: ${loadError.code}, message: ${loadError.message}`);
        return;
      }
      console.info("Succeeded in loading the content.");
      windowStage.createSubWindow("subWindow").then((subWindow: window.Window) => {
        if (subWindow == null) {
          console.error("Failed to create the subWindow. Cause: The data is empty");
          return;
        }
        subWindow.setFollowParentWindowLayoutEnabled(true).then(() => {
          console.info("after set follow parent window layout")
        }).catch((error: BusinessError) => {
          console.error(`setFollowParentWindowLayoutEnabled failed. ${error.code} ${error.message}`);
        })
      }).catch((error: BusinessError) => {
        console.error(`createSubWindow failed. ${error.code} ${error.message}`);
      })
    });
  }
}
```

## setFullScreen

```TypeScript
setFullScreen(isFullScreen: boolean, callback: AsyncCallback<void>): void
```

Sets whether the main window or the child window is in full-screen mode. This API uses an asynchronous callback to return the result.

Full-screen mode means that the layout does not avoid the status bar or &lt;!--RP15--&gt;three-button navigation bar&lt;!- -RP15End--&gt;, and components may overlap with them.

Non-full-screen mode means that the layout avoids the status bar and &lt;!--RP15--&gt;three-button navigation bar<!--RP 15End-->, and components do not overlap with them.

> **NOTE:** 
> 
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use
> [setWindowSystemBarEnable()](#setwindowsystembarenable-1)
> and [setWindowLayoutFullScreen()](#setwindowlayoutfullscreen-1)
> to implement the full-screen mode.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [setWindowSystemBarEnable](#setwindowsystembarenable-1)(names: Array&lt;'status' | 'navigation'&gt;), [setWindowLayoutFullScreen](#setwindowlayoutfullscreen-1)(isLayoutFullScreen: boolean)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isFullScreen | boolean | Yes | Whether to set full-screen mode (full-screen mode affects the display of the status bar and &lt;!--RP15--&gt;three-button navigation bar&lt;!--RP15End--&gt;). **true** to set full-screen mode, **false** otherwise. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let isFullScreen: boolean = true;
      windowClass.setFullScreen(isFullScreen, (err: BusinessError) => {
        const errCode: number = err.code;
        if (errCode) {
          console.error(`Failed to enable the full-screen mode. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in enabling the full-screen mode.');
      });
    });
  }
}
```

<a id="setfullscreen-1"></a>

## setFullScreen

```TypeScript
setFullScreen(isFullScreen: boolean): Promise<void>
```

Sets whether the main window or the child window is in full-screen mode. This API uses a promise to return the result.

Full-screen mode means that the layout does not avoid the status bar or &lt;!--RP15--&gt;three-button navigation bar&lt;!- -RP15End--&gt;, and components may overlap with them.

Non-full-screen mode means that the layout avoids the status bar and &lt;!--RP15--&gt;three-button navigation bar<!--RP 15End-->, and components do not overlap with them.

> **NOTE:** 
> 
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use
> [setWindowSystemBarEnable()](#setwindowsystembarenable-1)
> and [setWindowLayoutFullScreen()](#setwindowlayoutfullscreen-1)
> to implement the full-screen mode.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [setWindowSystemBarEnable](#setwindowsystembarenable-1)(names: Array&lt;'status' | 'navigation'&gt;), [setWindowLayoutFullScreen](#setwindowlayoutfullscreen-1)(isLayoutFullScreen: boolean)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isFullScreen | boolean | Yes | Whether to set full-screen mode (full-screen mode affects the display of the status bar and &lt;!--RP15--&gt;three-button navigation bar&lt;!--RP15End--&gt;). **true** to set full-screen mode, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let isFullScreen: boolean = true;
      let promise = windowClass.setFullScreen(isFullScreen);
      promise.then(() => {
        console.info('Succeeded in enabling the full-screen mode.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to enable the full-screen mode. Cause code: ${err.code}, message: ${err.message}`);
      });
    });
  }
}
```

## setGestureBackEnabled

```TypeScript
setGestureBackEnabled(enabled: boolean): Promise<void>
```

Sets whether to enable the side-swipe gesture for back redirection in the current window. This API can be successfully called only for the main window, and error code 1300004 is returned on other windows.

After being enabled, this function takes effect only when the window is in full-screen mode and in the foreground with the focus gained.

After this function is disabled, the gesture hot zone of the current application is disabled, and the side-swipe for back redirection becomes invalid. After the user switches to another application or returns to the home screen, the gesture hot zone is restored, and the side-swipe for back redirection becomes normal.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable the back gesture feature. **true** to enable, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows are supported. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;

      // Disable the back gesture feature in the current window.
      try {
        let gestureBackEnabled: boolean = false;
        let promise = windowClass.setGestureBackEnabled(gestureBackEnabled);
        promise.then(() => {
          console.info(`Succeeded in setting gesture back disabled`);
        }).catch((err: BusinessError) => {
          console.error(`Failed to set gesture back disabled, Cause code: ${err.code}, message: ${err.message}`);
        });
      } catch(exception) {
        console.error(`Failed to set gesture back disabled, Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

## setImmersiveModeEnabledState

```TypeScript
setImmersiveModeEnabledState(enabled: boolean): void
```

Sets whether to enable the immersive layout for the main window. This API does not change the window mode or size. It can be called only by the main window and child windows.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable the immersive layout.<br>**true** to enable, **false** otherwise.<br> |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: Internal IPC error. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows and subwindows are supported. |

**Examples**

```TypeScript
try {
  let enabled = false;
  windowClass.setImmersiveModeEnabledState(enabled);
} catch (exception) {
  console.error(`Failed to set the window immersive mode enabled status. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setKeepScreenOn

```TypeScript
setKeepScreenOn(isKeepScreenOn: boolean): Promise<void>
```

Sets whether to keep the screen always on. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [setWindowKeepScreenOn](#setwindowkeepscreenon)(isKeepScreenOn: boolean)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isKeepScreenOn | boolean | Yes | Whether to keep the screen always on. **true** to keep the screen always on, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isKeepScreenOn: boolean = true;
let promise = windowClass.setKeepScreenOn(isKeepScreenOn);
promise.then(() => {
  console.info('Succeeded in setting the screen to be always on.');
}).catch((err: BusinessError) => {
  console.info(`Failed to set the screen to be always on. Cause code: ${err.code}, message: ${err.message}`);
});
```

<a id="setkeepscreenon-1"></a>

## setKeepScreenOn

```TypeScript
setKeepScreenOn(isKeepScreenOn: boolean, callback: AsyncCallback<void>): void
```

Sets whether to keep the screen always on. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [setWindowKeepScreenOn](#setwindowkeepscreenon-1)(isKeepScreenOn: boolean, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isKeepScreenOn | boolean | Yes | Whether to keep the screen always on. **true** to keep the screen always on, **false** otherwise. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isKeepScreenOn: boolean = true;
windowClass.setKeepScreenOn(isKeepScreenOn, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to set the screen to be always on. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in setting the screen to be always on.');
});
```

## setLayoutFullScreen

```TypeScript
setLayoutFullScreen(isLayoutFullScreen: boolean, callback: AsyncCallback<void>): void
```

Sets whether the main window layout or the child window layout is immersive. This API uses an asynchronous callback to return the result.

An immersive layout means that the layout does not avoid the status bar or &lt;!--RP15--&gt;three-button navigation bar &lt;!--RP15End--&gt;, and components may overlap with them.

A non-immersive layout means that the layout avoids the status bar and &lt;!--RP15--&gt;three-button navigation bar<!-- RP15End-->, and components do not overlap with them.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setWindowLayoutFullScreen](#setwindowlayoutfullscreen-1)(isLayoutFullScreen: boolean)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isLayoutFullScreen | boolean | Yes | Whether the layout of the window is immersive. (Immersive layout mode does not affect the display of the status bar and &lt;!--RP15--&gt;three-button navigation bar&lt;!--RP15End--&gt;.) **true** if immersive, **false** otherwise. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let isLayoutFullScreen: boolean = true;
      windowClass.setLayoutFullScreen(isLayoutFullScreen, (err: BusinessError) => {
        const errCode: number = err.code;
        if (errCode) {
          console.error(`Failed to set the window layout to full-screen mode. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in setting the window layout to full-screen mode.');
      });
    });
  }
}
```

<a id="setlayoutfullscreen-1"></a>

## setLayoutFullScreen

```TypeScript
setLayoutFullScreen(isLayoutFullScreen: boolean): Promise<void>
```

Sets whether the main window layout or the child window layout is immersive. This API uses a promise to return the result.

An immersive layout means that the layout does not avoid the status bar or &lt;!--RP15--&gt;three-button navigation bar &lt;!--RP15End--&gt;, and components may overlap with them.

A non-immersive layout means that the layout avoids the status bar and &lt;!--RP15--&gt;three-button navigation bar<!-- RP15End-->, and components do not overlap with them.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setWindowLayoutFullScreen](#setwindowlayoutfullscreen-1)(isLayoutFullScreen: boolean)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isLayoutFullScreen | boolean | Yes | Whether the layout of the window is immersive. (Immersive layout mode does not affect the display of the status bar and &lt;!--RP15--&gt;three-button navigation bar&lt;!--RP15End--&gt;.) **true** if immersive, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let isLayoutFullScreen: boolean = true;
      let promise = windowClass.setLayoutFullScreen(isLayoutFullScreen);
      promise.then(() => {
        console.info('Succeeded in setting the window layout to full-screen mode.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to set the window layout to full-screen mode. Cause code: ${err.code}, message: ${err.message}`);
      });
    });
  }
}
```

## setOutsideTouchable

```TypeScript
setOutsideTouchable(touchable: boolean): Promise<void>
```

Sets whether the area outside the child window is touchable. This API uses a promise to return the result.

> Starting from API version 9, the area outside the child window is touchable by default. This API is no longer
> supported and no substitute API is provided.

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| touchable | boolean | Yes | Whether the area outside the child window is touchable. **true** if touchable, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = windowClass.setOutsideTouchable(true);
promise.then(() => {
  console.info('Succeeded in setting the area to be touchable.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set the area to be touchable. Cause code: ${err.code}, message: ${err.message}`);
});
```

<a id="setoutsidetouchable-1"></a>

## setOutsideTouchable

```TypeScript
setOutsideTouchable(touchable: boolean, callback: AsyncCallback<void>): void
```

Sets whether the area outside the child window is touchable. This API uses an asynchronous callback to return the result.

> Starting from API version 9, the area outside the child window is touchable by default. This API is no longer
> supported and no substitute API is provided.

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| touchable | boolean | Yes | Whether the area outside the child window is touchable. **true** if touchable, **false** otherwise. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

windowClass.setOutsideTouchable(true, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to set the area to be touchable. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in setting the area to be touchable.');
});
```

## setParentWindow

```TypeScript
setParentWindow(windowId: number): Promise<void>
```

Sets a new parent window for this child window. The new parent window can be a main window, another child window, or a floating window in the same process. This API uses a promise to return the result.

If the child window is focused and the new parent window is in the foreground, the new parent window will be raised.

If the child window is focused and the new parent window has a modal child window with a higher level, the focus will be transferred to that modal child window.

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| windowId | number | Yes | Parent window ID, which must be an integer. You are advised to call [getWindowProperties()](#getwindowproperties) to obtain the parent window ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only subwindows are supported. |
| [1300009](../errorcode-window.md#1300009-invalid-parent-window) | The parent window is invalid. Possible cause: The parent window does not exist or has been destroyed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let windowClass: window.Window = window.findWindow("subWindow");
  let newParentWindow: window.Window = window.findWindow("newParentWindow");
  let newParentWindowId: number = newParentWindow.getWindowProperties().id;
  let promise = windowClass.setParentWindow(newParentWindowId);
  promise.then(() => {
    console.info('Succeeded in setting the new parent window.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the new parent window. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set the new parent window. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setPreferredOrientation

```TypeScript
setPreferredOrientation(orientation: Orientation): Promise<void>
```

Sets the preferred orientation for the main window. This API uses a promise to return the result. This API does not take effect when it is called by a child window.

Before &lt;!--RP1--&gt;OpenHarmony 6.1&lt;!--RP1End--&gt;, this API can be called only by and takes effect for the main window. If it is called for other window types, it does not take effect.

Starting from &lt;!--RP1--&gt;OpenHarmony 6.1&lt;!--RP1End--&gt;, this API can be called by the main window and the system window with **WindowType** set to **TYPE_WALLET_SWIPE_CARD**. If it is called for other window types, it does not take effect. When the system window calls the **setPreferredOrientation** API, if there is a higher-level window for which the display orientation has been set, the call will not take effect immediately. In this case, the set display orientation will be recorded. When there is a no higher-level window with the display orientation set, the last orientation request will be restored. When the display orientation is set for the system window whose **WindowType** is **TYPE_WALLET_SWIPE_CARD** and takes effect, the foreground application will transition to the background.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| orientation | [Orientation](arkts-arkui-window-orientation-e.md) | Yes | Display orientation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: Invalid parameter value range. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let orientation = window.Orientation.AUTO_ROTATION;
      try {
        let promise = windowClass.setPreferredOrientation(orientation);
        promise.then(() => {
          console.info('Succeeded in setting the window orientation.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to set the window orientation. Cause code: ${err.code}, message: ${err.message}`);
        });
      } catch (exception) {
        console.error(`Failed to set window orientation. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

<a id="setpreferredorientation-1"></a>

## setPreferredOrientation

```TypeScript
setPreferredOrientation(orientation: Orientation, callback: AsyncCallback<void>): void
```

Sets the preferred orientation for this window. This API uses an asynchronous callback to return the result. For details about the development practices of orientation, see [Display Orientation Switching](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-landscape-and-portrait-development).

Before &lt;!--RP1--&gt;OpenHarmony 6.1&lt;!--RP1End--&gt;, this API can be called only by and takes effect for the main window. If it is called for other window types, it does not take effect.

Starting from &lt;!--RP1--&gt;OpenHarmony 6.1&lt;!--RP1End--&gt;, this API can be called by the main window and the system window with **WindowType** set to **TYPE_WALLET_SWIPE_CARD**. If it is called for other window types, it does not take effect. When the system window calls the **setPreferredOrientation** API, if there is a higher-level window for which the display orientation has been set, the call will not take effect immediately. In this case, the set display orientation will be recorded. When there is a no higher-level window with the display orientation set, the last orientation request will be restored. When the display orientation is set for the system window whose **WindowType** is **TYPE_WALLET_SWIPE_CARD** and takes effect, the foreground application will transition to the background.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| orientation | [Orientation](arkts-arkui-window-orientation-e.md) | Yes | Display orientation. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. The callback indicates the API call result. It does not mean that the application rotation animation ends. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: Invalid parameter value range. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let orientation = window.Orientation.AUTO_ROTATION;
      try {
        windowClass.setPreferredOrientation(orientation, (err: BusinessError) => {
          const errCode: number = err.code;
          if (errCode) {
            console.error(`Failed to set window orientation. Cause code: ${err.code}, message: ${err.message}`);
            return;
          }
          console.info('Succeeded in setting window orientation.');
        });
      } catch (exception) {
        console.error(`Failed to set window orientation. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

## setPreferredOrientationWithResult

```TypeScript
setPreferredOrientationWithResult(orientation: Orientation): Promise<OrientationResult>
```

Sets the preferred orientation for the main window. This API uses a promise to return the result. It does not take effect on devices that do not support rotation with the sensor, on 2-in-1 devices or for the child window.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| orientation | [Orientation](arkts-arkui-window-orientation-e.md) | Yes | The orientation config of the window |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[OrientationResult](arkts-arkui-window-orientationresult-i.md)&gt; | Promise used to return the OrientationResult. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let orientation = window.Orientation.LANDSCAPE;
      try {
        windowClass.setPreferredOrientationWithResult(orientation).then((result: window.OrientationResult) => {
          console.info(`Succeeded in setting the window orientation. Result: ${JSON.stringify(result)}`);
        }).catch((err: BusinessError) => {
          console.error(`Failed to set the window orientation. Cause code: ${err.code}, message: ${err.message}`);
        });
      } catch (exception) {
        console.error(`Failed to set window orientation. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

## setPrivacyMode

```TypeScript
setPrivacyMode(isPrivacyMode: boolean): Promise<void>
```

Sets whether this window is in privacy mode. This API uses a promise to return the result. A window in privacy mode cannot be captured or recorded. This API can be used in scenarios where screen capture or recording is disabled.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setWindowPrivacyMode](#setwindowprivacymode)(isPrivacyMode: boolean)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isPrivacyMode | boolean | Yes | Whether the window is in privacy mode. **true** if in privacy mode, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isPrivacyMode: boolean = true;
let promise = windowClass.setPrivacyMode(isPrivacyMode);
promise.then(() => {
  console.info('Succeeded in setting the window to privacy mode.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set the window to privacy mode. Cause code: ${err.code}, message: ${err.message}`);
});
```

<a id="setprivacymode-1"></a>

## setPrivacyMode

```TypeScript
setPrivacyMode(isPrivacyMode: boolean, callback: AsyncCallback<void>): void
```

Sets whether this window is in privacy mode. This API uses an asynchronous callback to return the result. A window in privacy mode cannot be captured or recorded. This API can be used in scenarios where screen capture or recording is disabled.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setWindowPrivacyMode](#setwindowprivacymode-1)(isPrivacyMode: boolean, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isPrivacyMode | boolean | Yes | Whether the window is in privacy mode. **true** if in privacy mode, **false** otherwise. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isPrivacyMode: boolean = true;
windowClass.setPrivacyMode(isPrivacyMode, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to set the window to privacy mode. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in setting the window to privacy mode.');
});
```

<a id="setraisebyclickenabled-1"></a>

## setRaiseByClickEnabled

```TypeScript
setRaiseByClickEnabled(enable: boolean): Promise<void>
```

Sets whether to enable a child window to raise itself by click. This API uses a promise to return the result.

Generally, when a child window is clicked, it is brought to the forefront among sibling child windows of the same type that share the same parent window within the application. If the **enable** parameter is set to **false**, when the child window is clicked, it still stays in its existing position.

Before calling this API, ensure that the child window has been created and [showWindow()](#showwindow) has been successfully executed.

**Since:** 14

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether a child window can be raised by clicking. **true** if the child window can be raised by clicking, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. The window is not shown. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only subwindows are supported. |
| [1300009](../errorcode-window.md#1300009-invalid-parent-window) | The parent window is invalid. Possible cause: The parent window does not exist or has been destroyed. |

**Examples**

```TypeScript
// EntryAbility.ets
import { window } from '@kit.ArkUI';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    // Create a child window.
    windowStage.createSubWindow("testSubWindow").then((subWindow) => {
      if (subWindow == null) {
        console.error('Failed to create the subWindow. Cause: The data is empty');
        return;
      }
      subWindow.showWindow().then(() => {
        try {
          let enabled = false;
          subWindow.setRaiseByClickEnabled(enabled).then(() => {
            console.info('Succeeded in disabling the raise-by-click function.');
          }).catch((err: BusinessError) => {
            console.error(`Failed to disable the raise-by-click function. Cause code: ${err.code}, message: ${err.message}`);
          });
        } catch (err) {
          console.error(`Failed to disable the raise-by-click function. Cause code: ${err.code}, message: ${err.message}`);
        }
      });
    });
  }
}
```

## setReceiveDragEventEnabled

```TypeScript
setReceiveDragEventEnabled(enabled: boolean): Promise<void>
```

Sets whether the current window can receive [drag events](../arkts-components/arkts-arkui-common-comp-dragevent-i.md). This API uses a promise to return the result.

By default, the value of **enabled** is **true**, indicating that the window can receive drag events.

If the value of **enabled** is **false**, the current window cannot receive drag events.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether the window can receive drag events. **true** if the window can receive drag events; **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function cannot work because the current device does not support this ability. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: Internal IPC error |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let enabled = false;
try {
  let promise = windowClass.setReceiveDragEventEnabled(enabled);
  promise.then(() => {
    console.info('Succeeded in setting the window to be WindowReceiveDragEventEnabled.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the window to be the window ReceiveDragEventEnabled. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set the window ReceiveDragEventEnabled. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setRelativePositionToParentWindowEnabled

```TypeScript
setRelativePositionToParentWindowEnabled(enabled: boolean, anchor?: WindowAnchor,
        offsetX?: number, offsetY?: number): Promise<void>
```

Sets whether a first-level child window can maintain a fixed relative position to the main window. This API works only in [freeform window](../../../windowmanager/window-terminology.md#freeform-window) mode. This API uses a promise to return the result.

The relative position is defined by the offset between the anchor points of the child window and the main window. Both the child window and the main window use the same type of anchor point.

1. This API applies only to level-1 child windows that are not maximized.
2. Once this API is called on a child window, its display position will immediately follow the main window and maintain a fixed relative position. This effect will persist until this API is called again with **false**.
3. If this API is called on a child window, subsequent calls to [moveWindowTo()](#movewindowto) or [maximize()](#maximize) to modify the window's position or size will not take effect.

Once this API is successfully called, the [setFollowParentWindowLayoutEnabled()](#setfollowparentwindowlayoutenabled) API will no longer take effect.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | The value true means the first level sub window supports maintaining the same relative position with the main window, and false means the opposite. |
| anchor | [WindowAnchor](arkts-arkui-window-windowanchor-e.md) | No | Window anchor point that setting when the relative position between the primary sub window and the main window remains unchanged. The default value is window.WindowAnchor.TopStart, meaning the default anchor point is the top-left corner of the window. |
| offsetX | number | No | The x-axis offset, measured in px. between the anchor point of the first level sub window and the anchor point of the main window. The default value is 0. |
| offsetY | number | No | The y-axis offset, measured in px. between the anchor point of the first level sub window and the anchor point of the main window. The default value is 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function setRelativePositionToParentWindowEnabled can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only subwindows are supported. |

**Examples**

```TypeScript
// EntryAbility.ets
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    windowStage.loadContent('pages/Index', (loadError: BusinessError) => {
      if (loadError.code) {
        console.error(`Failed to load the content. Cause code: ${loadError.code}, message: ${loadError.message}`);
        return;
      }
      console.info("Succeeded in loading the content.");
      windowStage.createSubWindow("subWindow").then((subWindow: window.Window) => {
        if (subWindow == null) {
          console.error("Failed to create the subWindow. Cause: The data is empty");
          return;
        }
        subWindow.setRelativePositionToParentWindowEnabled(true).then(() => {
          console.info("after set relative position to parent window enabled");
        }).catch((error: BusinessError) => {
          console.error(`setRelativePositionToParentWindowEnabled failed. ${error.code} ${error.message}`);
        })
      }).catch((error: BusinessError) => {
        console.error(`createSubWindow failed. ${error.code} ${error.message}`);
      })
    });
  }
}
```

## setResizeByDragEnabled

```TypeScript
setResizeByDragEnabled(enable: boolean, callback: AsyncCallback<void>): void
```

Sets whether to enable the main window or child window with decorations to resize itself by dragging. This API uses an asynchronous callback to return the result.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Disable window to resize by drag if false. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The callback of setResizeByDragEnabled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. Invalid window type. Only main windows and child windows with decorations are supported. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
try {
  let enabled = false;
  windowClass.setResizeByDragEnabled(enabled, (err) => {
    if (err.code) {
      console.error(`Failed to set the function of disabling the resize by drag window. Cause code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in setting the function of disabling the resize by drag window.`);
  });
} catch (exception) {
  console.error(`Failed to set the function of disabling the resize by drag window. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

<a id="setresizebydragenabled-1"></a>

## setResizeByDragEnabled

```TypeScript
setResizeByDragEnabled(enable: boolean): Promise<void>
```

Sets whether to enable the main window or child window with decorations to resize itself by dragging. This API uses a promise to return the result.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Disable window to resize by drag if false. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. Invalid window type. Only main windows and child windows with decorations are supported. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let enabled = false;
  let promise = windowClass.setResizeByDragEnabled(enabled);
  promise.then(() => {
    console.info(`Succeeded in setting the function of disabling the resize by drag window.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the function of disabling the resize by drag window. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set the function of disabling the resize by drag window. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setSeparationTouchEnabled

```TypeScript
setSeparationTouchEnabled(enabled: boolean): Promise<void>
```

Sets whether the current window supports the event separation state. This API uses a promise to return the result. In the default scenario, the value of **enabled** is **true**, indicating that the event separation state is supported.

When the event separation state is supported:

- All events generated by finger taps are sent to the window that the finger taps hit.

When the event separation state is not supported (the value of **enabled** is **false**):

- If the first finger taps the window, keeps hitting the window, and does not lift up, the events generated by  
subsequent taps of other fingers are distributed to the window, regardless of whether the taps of other fingers hit the window.  
- If the first finger taps the window and does not keep hitting the window, the events generated by subsequent  
taps of other fingers are not distributed to the window and are discarded by the system, even if the taps of other fingers hit the window.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether the window supports the event separation state. **true** if supported; **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function cannot work because the current device does not support this ability. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: Internal IPC error |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let enabled = false;
try {
  let promise = windowClass.setSeparationTouchEnabled(enabled);
  promise.then(() => {
    console.info('Succeeded in setting the window to be separationTouchEnabled.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the window to be separationTouchEnabled. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set the separationTouchEnabled. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setSpecificSystemBarEnabled

```TypeScript
setSpecificSystemBarEnabled(name: SpecificSystemBar, enable: boolean, enableAnimation?: boolean): Promise<void>
```

Sets whether to show or hide the status bar and &lt;!--RP15--&gt;three-button navigation bar&lt;!--RP15End--&gt; of the main window. This API uses a promise to return the result.

The return value does not indicate that the status bar and &lt;!--RP15--&gt;three-button navigation bar&lt;!--RP15End--&gt; are shown or hidden. This API does not take effect when it is called by a child window. The setting does not take effect when the main window is in non-full-screen or non-maximized mode (such as floating windows or split-screen mode). It takes effect once the main window enters full-screen or maximized mode.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | [SpecificSystemBar](arkts-arkui-window-specificsystembar-t.md) | Yes | the set of system bar |
| enable | boolean | Yes | Show specific system bar if true, or hide specific system bar if false. |
| enableAnimation | boolean | No | Whether using animation during this setting, using animation if true or not using animation if false.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
// Here, the status bar is hidden.
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';


export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      try {
        let promise = windowClass.setSpecificSystemBarEnabled('status', false);
        promise.then(() => {
          console.info('Succeeded in setting the system bar to be invisible.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to set the system bar to be invisible. Cause code: ${err.code}, message: ${err.message}`);
        });
      } catch (exception) {
        console.error(`Failed to set the system bar to be invisible. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

## setStatusBarColor

```TypeScript
setStatusBarColor(color: ColorMetrics): Promise<void>
```

Sets the text color of the status bar in the main window. This API uses a promise to return the result.

Setting the status bar text color is not supported for child windows. Calling this API on a child window will have no effect. The setting does not take effect when the main window is in non-full-screen or non-maximized mode (such as floating windows or split-screen mode). It takes effect once the main window enters full-screen or maximized mode.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | Yes | Text color of the status bar. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported on this device. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: Internal task error. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { ColorMetrics, window } from '@kit.ArkUI';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      try {
        let promise = windowClass.setStatusBarColor(ColorMetrics.numeric(0x112233));
        promise.then(() => {
          console.info('Succeeded in setting the status bar color.');
        }).catch((err: BusinessError) => {
          console.error(`Set the status bar color failed. Cause code: ${err.code}, message: ${err.message}`);
        });
      } catch (exception) {
        console.error(`Failed to set the status bar color. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

## setSubWindowModal

```TypeScript
setSubWindowModal(isModal: boolean): Promise<void>
```

Enables the modal property of the child window. This API uses a promise to return the result.

This API must be called by a child window and the setting takes effect for the child window. After the modal property is enabled, the parent window does not respond to user interactions until the child window is closed or the child window's modal property is disabled.

If this API is called by a main window, an error is reported.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isModal | boolean | Yes | Whether to enable the modal property of the child window. **true** to enable, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally.<br>**Applicable version:** 20 and later |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only subwindows are supported. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    // Create a child window.
    try {
      let subWindow = windowStage.createSubWindow("testSubWindow");
      subWindow.then((data) => {
        if (data == null) {
          console.error("Failed to create the subWindow. Cause: The data is empty");
          return;
        }
        windowClass = data;
        let promise = windowClass.setSubWindowModal(true);
        promise.then(() => {
          console.info('Succeeded in setting subwindow modal');
        }).catch((err: BusinessError) => {
          console.error(`Failed to set subwindow modal. Cause code: ${err.code}, message: ${err.message}`);
        });
      });
    } catch (exception) {
      console.error(`Failed to create the subWindow. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

<a id="setsubwindowmodal-1"></a>

## setSubWindowModal

```TypeScript
setSubWindowModal(isModal: boolean, modalityType: ModalityType): Promise<void>
```

Sets the modality type of the child window. This API uses a promise to return the result.

When the child window is of the window-modal type, its parent window does not respond to user interactions until the child window is closed or the child window's modal property is disabled.

When the child window is of the application-modal type, its parent window and the windows from other instances of the application do not respond to user interactions until the child window is closed or the child window's modal property is disabled.

This API is used to set the modality type. To disable the modal property, you are advised to use [setSubWindowModal&lt;sup&gt;12+&lt;/sup&gt;](#setsubwindowmodal).

If this API is called by a window other than the child window, an error is reported.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isModal | boolean | Yes | Whether to enable the modal property of the child window. **true** to enable, **false** otherwise. Currently, this parameter can only be set to **true**. |
| modalityType | [ModalityType](arkts-arkui-window-modalitytype-e.md) | Yes | Modality type of the child window. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally.<br>**Applicable version:** 20 and later |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only subwindows are supported. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    // Create a child window.
    try {
      let subWindow = windowStage.createSubWindow("testSubWindow");
      subWindow.then((data) => {
        if (!data) {
          console.error("Failed to create the subWindow. Cause: The data is empty");
          return;
        }
        windowClass = data;
        let promise = windowClass.setSubWindowModal(true, window.ModalityType.WINDOW_MODALITY);
        promise.then(() => {
          console.info('Succeeded in setting subwindow modal');
        }).catch((err: BusinessError) => {
          console.error(`Failed to set subwindow modal. Cause code: ${err.code}, message: ${err.message}`);
        });
      });
    } catch (exception) {
      console.error(`Failed to create the subWindow. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

## setSubWindowZLevel

```TypeScript
setSubWindowZLevel(zLevel: number): Promise<void>
```

Sets the z-level of the current child window. Child windows with modal properties are not supported. This API uses a promise to return the result.

Changing the z-level of a child window using this API will not cause a focus switch. You are advised to use [shiftAppWindowFocus()](arkts-arkui-window-shiftappwindowfocus-f.md) for focus switching.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| zLevel | number | Yes | Z-level of the child window. The default value is **0**, and the value range is [-10000, 10000]. Only integers are supported, and floating-point numbers will be rounded down. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function setSubWindowZLevel can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only non-modal subwindows are supported. |
| [1300009](../errorcode-window.md#1300009-invalid-parent-window) | The parent window is invalid. Possible cause: The parent window does not exist or has been destroyed. |

**Examples**

```TypeScript
// EntryAbility.ets
import { window } from '@kit.ArkUI';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let zLevel: number = 1;
    // Create a child window.
    try {
      windowStage.createSubWindow('testSubWindow').then((subWindow) => {
        if (subWindow == null) {
          console.error('Failed to create the sub window. Cause: The sub window is null');
          return;
        }
        subWindow.setSubWindowZLevel(zLevel).then(() => {
          console.info('Succeeded in setting sub window zLevel.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to set sub window zLevel. Cause code: ${err.code}, message: ${err.message}`);
        });
      });
    } catch (err) {
      console.error(`Failed to create the sub window or set zLevel. Cause code: ${err.code}, message: ${err.message}`);
    }
  }
}
```

## setSupportedWindowModes

```TypeScript
setSupportedWindowModes(supportedWindowModes: Array<bundleManager.SupportWindowMode>): Promise<void>
```

Sets the supported window modes of the app window.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| supportedWindowModes | Array&lt;[bundleManager.SupportWindowMode](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-supportwindowmode-e.md)&gt; | Yes | The supported modes of the window. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: 1. Only main windows and subwindows are supported. 2. Not supported when subwindows are set to follow the main window. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: 1. When called on a main window, the parameter should not only contain SPLIT. 2. When called on a sub window, the parameter should not contain SPLIT. |

## setSystemAvoidAreaEnabled

```TypeScript
setSystemAvoidAreaEnabled(enabled: boolean): Promise<void>
```

Enables the capability to obtain the window avoidance area information using [getWindowAvoidArea()](#getwindowavoidarea) or listen for window avoidance area changes using [on('avoidAreaChange')](#onavoidareachange) after a global floating window, modal window, or system window is created.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | If true, the system window type can obtain avoid area. If false, the avoid area obtained by the system window type will always be empty. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. Possible cause: The device does not support the API itself. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only global floating windows, dialog windows, or Window Type as system windows are supported. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        console.error('Failed to load the content. Cause: %{public}s', JSON.stringify(err));
        return;
      }
      console.info('Succeeded in loading the content.');
      let windowClass: window.Window | undefined = undefined;
      let config: window.Configuration = {
        name: "test",
        windowType: window.WindowType.TYPE_DIALOG,
        decorEnabled: true,
        ctx: this.context
      };
      try {
        window.createWindow(config, (err: BusinessError, data) => {
          const errCode: number = err.code;
          if (errCode) {
            console.error(`Failed to create the system window. Cause code: ${err.code}, message: ${err.message}`);
            return;
          }
          windowClass = data;
          windowClass.setUIContent("pages/Test");
          let enabled = true;
          let promise = windowClass.setSystemAvoidAreaEnabled(enabled);
          promise.then(() => {
            let type = window.AvoidAreaType.TYPE_SYSTEM;
            let avoidArea = windowClass?.getWindowAvoidArea(type);
          }).catch((err: BusinessError) => {
            console.error(`Failed to obtain the system window avoid area. Cause code: ${err.code}, message: ${err.message}`);
          });
        });
      } catch (exception) {
        console.error(`Failed to create the system window. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

## setSystemBarEnable

```TypeScript
setSystemBarEnable(names: Array<'status' | 'navigation'>, callback: AsyncCallback<void>): void
```

&lt;!--RP14--&gt;Sets whether to show the status bar and three-button navigation bar in the main window. The visibility of the status bar and three-button navigation bar is controlled by **status** and **navigation**, respectively.&lt;!--RP14End--&gt; This API uses an asynchronous callback to return the result.

From API version 12, &lt;!--RP5--&gt;this API does not take effect on 2-in-1 devices.&lt;!--RP5End--&gt;

The return value does not indicate that the status bar and &lt;!--RP15--&gt;three-button navigation bar&lt;!--RP15End--&gt; are shown or hidden. This API does not take effect when it is called by a child window. The configuration does not take effect in non-full-screen mode (such as floating window or split-screen mode).

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setWindowSystemBarEnable](#setwindowsystembarenable-1)(names: Array&lt;'status'|'navigation'&gt;)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| names | Array&lt;'status' &#124; 'navigation'&gt; | Yes | Whether to show the status bar and &lt;!--RP15--&gt;three-button navigation bar&lt;!--RP15End--&gt; in full-screen mode.<br>For example, to show all of them, set this parameter to **['status','navigation']**. If this parameter is set to [], they are hidden. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
// The following assumes that all of them are hidden.
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let names: Array<'status' | 'navigation'> = [];
      windowClass.setSystemBarEnable(names, (err: BusinessError) => {
        const errCode: number = err.code;
        if (errCode) {
          console.error(`Failed to set the system bar to be invisible. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in setting the system bar to be invisible.');
      });
    });
  }
}
```

<a id="setsystembarenable-1"></a>

## setSystemBarEnable

```TypeScript
setSystemBarEnable(names: Array<'status' | 'navigation'>): Promise<void>
```

&lt;!--RP14--&gt;Sets whether to show the status bar and three-button navigation bar in the main window. The visibility of the status bar and three-button navigation bar is controlled by **status** and **navigation**, respectively.&lt;!--RP14End--&gt; This API uses a promise to return the result.

From API version 12, &lt;!--RP5--&gt;this API does not take effect on 2-in-1 devices.&lt;!--RP5End--&gt;

The return value does not indicate that the status bar and &lt;!--RP15--&gt;three-button navigation bar&lt;!--RP15End--&gt; are shown or hidden. This API does not take effect when it is called by a child window. The configuration does not take effect in non-full-screen mode (such as floating window or split-screen mode).

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setWindowSystemBarEnable](#setwindowsystembarenable-1)(names: Array&lt;'status'|'navigation'&gt;)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| names | Array&lt;'status' &#124; 'navigation'&gt; | Yes | Whether to show the status bar and &lt;!--RP15--&gt;three-button navigation bar&lt;!--RP15End--&gt; in full-screen mode.<br>For example, to show all of them, set this parameter to **['status','navigation']**. If this parameter is set to [], they are hidden. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
// The following assumes that all of them are hidden.
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let names: Array<'status' | 'navigation'> = [];
      let promise = windowClass.setSystemBarEnable(names);
      promise.then(() => {
        console.info('Succeeded in setting the system bar to be invisible.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to set the system bar to be invisible. Cause code: ${err.code}, message: ${err.message}`);
      });
    });
  }
}
```

## setSystemBarProperties

```TypeScript
setSystemBarProperties(systemBarProperties: SystemBarProperties, callback: AsyncCallback<void>): void
```

Sets the properties of the <!--Del-->three-button navigation bar and <!--DelEnd-->status bar of the main window. This API uses an asynchronous callback to return the result. &lt;!--RP5--&gt;This API does not take effect on 2-in-1 devices.&lt;!--RP5End--&gt;

This API does not take effect when it is called by a child window. The configuration does not take effect in non- full-screen mode (such as floating window or split-screen mode).

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [setWindowSystemBarProperties](#setwindowsystembarproperties-1)(systemBarProperties: SystemBarProperties)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| systemBarProperties | [SystemBarProperties](arkts-arkui-window-systembarproperties-i.md) | Yes | <!--Del-->Properties of the <!--Del-->three-button navigation bar and <!--DelEnd-->status bar. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let SystemBarProperties: window.SystemBarProperties = {
        statusBarColor: '#ff00ff',
        navigationBarColor: '#00ff00',
        // The following properties are supported since API version 8.
        statusBarContentColor: '#ffffff',
        navigationBarContentColor: '#00ffff'
      };
      windowClass.setSystemBarProperties(SystemBarProperties, (err) => {
        const errCode: number = err.code;
        if (errCode) {
          console.error(`Failed to set the system bar properties. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in setting the system bar properties.');
      });
    });
  }
}
```

<a id="setsystembarproperties-1"></a>

## setSystemBarProperties

```TypeScript
setSystemBarProperties(systemBarProperties: SystemBarProperties): Promise<void>
```

Sets the properties of the <!--Del-->three-button navigation bar and <!--DelEnd-->status bar of the main window. This API uses a promise to return the result. &lt;!--RP5--&gt;This API does not take effect on 2-in-1 devices.<!--RP5 End-->

This API does not take effect when it is called by a child window.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [setWindowSystemBarProperties](#setwindowsystembarproperties-1)(systemBarProperties: SystemBarProperties)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| systemBarProperties | [SystemBarProperties](arkts-arkui-window-systembarproperties-i.md) | Yes | <!--Del-->Properties of the <!--Del-->three-button navigation bar and <!--DelEnd-->status bar. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let SystemBarProperties: window.SystemBarProperties = {
        statusBarColor: '#ff00ff',
        navigationBarColor: '#00ff00',
        // The following properties are supported since API version 8.
        statusBarContentColor: '#ffffff',
        navigationBarContentColor: '#00ffff'
      };
      let promise = windowClass.setSystemBarProperties(SystemBarProperties);
      promise.then(() => {
        console.info('Succeeded in setting the system bar properties.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to set the system bar properties. Cause code: ${err.code}, message: ${err.message}`);
      });
    });
  }
}
```

## setTitleAndDockHoverShown

```TypeScript
setTitleAndDockHoverShown(isTitleHoverShown?: boolean, isDockHoverShown?: boolean): Promise<void>
```

Sets whether to show the window title bar and dock bar when the cursor hovers over the hot zone while the main window is in full-screen mode. This API uses a promise to return the result.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isTitleHoverShown | boolean | No | Whether to show the window title bar.<br>**true** to show, **false** otherwise. The default value is **true**.<br> |
| isDockHoverShown | boolean | No | Whether to show the dock bar.<br>**true** to show, **false** otherwise. The default value is **true**.<br> |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows are supported. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    // Load the page corresponding to the main window.
    windowStage.loadContent('pages/Index', (err) => {
      let mainWindow: window.Window | undefined = undefined;
      // Obtain the main window.
      windowStage.getMainWindow().then(
        data => {
          if (!data) {
            console.error('Failed to get main window. Cause: The data is undefined.');
            return;
          }
          mainWindow = data;
          console.info(`Succeeded in obtaining the main window. Data: ${JSON.stringify(data)}`);
          // Call maximize to enable the full-screen mode for the window.
          mainWindow.maximize(window.MaximizePresentation.ENTER_IMMERSIVE);
          // Call setTitleAndDockHoverShown to hide the window title bar and dock bar.
          mainWindow.setTitleAndDockHoverShown(false, false);
        }
      ).catch((err: BusinessError) => {
          if(err.code){
            console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
          }
      });
    });
  }
}
```

## setTouchable

```TypeScript
setTouchable(isTouchable: boolean): Promise<void>
```

Sets whether this window is touchable. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setWindowTouchable](#setwindowtouchable)(isTouchable: boolean)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isTouchable | boolean | Yes | Whether the window is touchable. **true** if touchable, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isTouchable = true;
let promise = windowClass.setTouchable(isTouchable);
promise.then(() => {
  console.info('Succeeded in setting the window to be touchable.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set the window to be touchable. Cause code: ${err.code}, message: ${err.message}`);
});
```

<a id="settouchable-1"></a>

## setTouchable

```TypeScript
setTouchable(isTouchable: boolean, callback: AsyncCallback<void>): void
```

Sets whether this window is touchable. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setWindowTouchable](#setwindowtouchable-1)(isTouchable: boolean, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isTouchable | boolean | Yes | Whether the window is touchable. **true** if touchable, **false** otherwise. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isTouchable = true;
windowClass.setTouchable(isTouchable, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to set the window to be touchable. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in setting the window to be touchable.');
});
```

## setTouchableAreas

```TypeScript
setTouchableAreas(rects: Array<Rect>): Promise<void>
```

Sets the touchable areas for this window. By default, the entire window is touchable. If a touchable area is set, touch events outside this area are transparently transmitted. The setting becomes invalid after the window rectangle changes.

**Since:** 26.0.0

**Required permissions:** 
- API version 26 and later: ohos.permission.SET_WINDOW_TOUCH_AREAS
- API versions 12 to 25: N/A

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rects | Array&lt;[Rect](arkts-arkui-window-rect-i.md)&gt; | Yes | Touchable areas. The maximum number of touchable areas cannot exceed 10, and each touchable area cannot exceed the window area. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value.<br>**Since:** 26.0.0 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required or a non-system application calls the API.<br>**Applicable version:** 26.0.0 and later |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 - 24 |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: Invalid parameter range. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const touchableRects: Array<window.Rect> = [
  { left: 100, top: 100, width: 200, height: 200 },
  { left: 0, top: 50, width: 150, height: 200 }
];
try {
  windowClass.setTouchableAreas(touchableRects).then(() => {
    console.info('Succeeded in setting the touchable areas.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the touchable areas. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set touchable areas. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setUIContent

```TypeScript
setUIContent(path: string, callback: AsyncCallback<void>): void
```

Loads the content of a page, with its path in the current project specified, to this window. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the page to which the content will be loaded |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally.<br>**Applicable version:** 9 |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  windowClass.setUIContent('pages/page2/page3', (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in loading the content.');
  });
} catch (exception) {
  console.error(`Failed to load the content. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

<a id="setuicontent-1"></a>

## setUIContent

```TypeScript
setUIContent(path: string): Promise<void>
```

Loads the content of a page, with its path in the current project specified, to this window. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the page to which the content will be loaded |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally.<br>**Applicable version:** 9 |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let promise = windowClass.setUIContent('pages/page2/page3');
  promise.then(() => {
    console.info('Succeeded in loading the content.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to load the content. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setWindowBackgroundColor

```TypeScript
setWindowBackgroundColor(color: string | ColorMetrics): void
```

Sets the background color for this window.

If this API is not called, the default background color of the window is **'#FFF0F0F0'** in light mode and **'#FF1A1A1A'** in dark mode.

In the stage model, this API must be used after the call of [loadContent](#loadcontent) or [setUIContent()](#setuicontent) takes effect.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | string &#124; [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | Yes | the specified color.<br>**Since:** 18 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed; |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { ColorMetrics } from '@kit.ArkUI';

let storage: LocalStorage = new LocalStorage();
storage.setOrCreate('storageSimpleProp', 121);
windowClass.loadContent("pages/page2", storage, (err: BusinessError) => {
  let errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in loading the content.');
  let color1: string = '#00FF33';
  let color2: ColorMetrics = ColorMetrics.numeric(0xff112233);
  try {
    windowClass?.setWindowBackgroundColor(color1);
    windowClass?.setWindowBackgroundColor(color2);
  } catch (exception) {
    console.error(`Failed to set the background color. Cause code: ${exception.code}, message: ${exception.message}`);
  };
});
```

## setWindowBrightness

```TypeScript
setWindowBrightness(brightness: number): Promise<void>
```

Sets the window brightness for the main window. The window brightness takes effect only when the window is in the foreground and has focus. This API uses a promise to return the result.

When the setting is valid, it affects only the physical screen where the window is displayed. It does not apply to virtual displays (for example, casting/mirroring screens).

If the input parameter is **-1**, the window brightness reverts to the system brightness (which can be adjusted through Control Panel or shortcut keys).

When the window moves to the background, the setting becomes invalid, and brightness can be adjusted through Control Panel or shortcut keys. You are advised not to call this API consecutively or when the window transitions to the background. Otherwise, timing issues may occur.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| brightness | number | Yes | the specified brightness value. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    windowStage.loadContent('pages/Index', (loadError: BusinessError) => {
      if (loadError.code) {
        console.error(`Failed to load the content. Cause code: ${loadError.code}, message: ${loadError.message}`);
        return;
      }
      let windowClass: window.Window | undefined = undefined;
      windowStage.getMainWindow((err: BusinessError, data) => {
        const errCode: number = err.code;
        if (errCode) {
          console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        windowClass = data;
        let brightness: number = 1.0;
        try {
          let promise = windowClass.setWindowBrightness(brightness);
          promise.then(() => {
            console.info('Succeeded in setting the brightness.');
          }).catch((err: BusinessError) => {
            console.error(`Failed to set the brightness. Cause code: ${err.code}, message: ${err.message}`);
          });
        } catch (exception) {
          console.error(`Failed to set the brightness. Cause code: ${exception.code}, message: ${exception.message}`);
        }
      });
    });
  }
}
```

<a id="setwindowbrightness-1"></a>

## setWindowBrightness

```TypeScript
setWindowBrightness(brightness: number, callback: AsyncCallback<void>): void
```

Sets the window brightness for the main window. The window brightness takes effect only when the window is in the foreground and has focus. This API uses an asynchronous callback to return the result.

When the setting is valid, it affects only the physical screen where the window is displayed. It does not apply to virtual displays (for example, casting/mirroring screens).

If the input parameter is **-1**, the window brightness reverts to the system brightness (which can be adjusted through Control Panel or shortcut keys).

When the window moves to the background, the setting becomes invalid, and brightness can be adjusted through Control Panel or shortcut keys. You are advised not to call this API consecutively or when the window transitions to the background. Otherwise, timing issues may occur.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| brightness | number | Yes | the specified brightness value. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    windowStage.loadContent('pages/Index', (loadError: BusinessError) => {
      if (loadError.code) {
        console.error(`Failed to load the content. Cause code: ${loadError.code}, message: ${loadError.message}`);
        return;
      }
      let windowClass: window.Window | undefined = undefined;
      windowStage.getMainWindow((err: BusinessError, data) => {
        const errCode: number = err.code;
        if (errCode) {
          console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        windowClass = data;
        let brightness: number = 1.0;
        try {
          windowClass.setWindowBrightness(brightness, (err: BusinessError) => {
            const errCode: number = err.code;
            if (errCode) {
              console.error(`Failed to set the brightness. Cause code: ${err.code}, message: ${err.message}`);
              return;
            }
            console.info('Succeeded in setting the brightness.');
          });
        } catch (exception) {
          console.error(`Failed to set the brightness. Cause code: ${exception.code}, message: ${exception.message}`);
        }
      });
    });
  }
}
```

## setWindowColorSpace

```TypeScript
setWindowColorSpace(colorSpace:ColorSpace): Promise<void>
```

Sets a color space for this window. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| colorSpace | [ColorSpace](arkts-arkui-window-colorspace-e.md) | Yes | the specified color space. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let promise = windowClass.setWindowColorSpace(window.ColorSpace.WIDE_GAMUT);
  promise.then(() => {
    console.info('Succeeded in setting window colorspace.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set window colorspace. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set window colorspace. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

<a id="setwindowcolorspace-1"></a>

## setWindowColorSpace

```TypeScript
setWindowColorSpace(colorSpace:ColorSpace, callback: AsyncCallback<void>): void
```

Sets a color space for this window. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| colorSpace | [ColorSpace](arkts-arkui-window-colorspace-e.md) | Yes | the specified color space. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  windowClass.setWindowColorSpace(window.ColorSpace.WIDE_GAMUT, (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to set window colorspace. Cause code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in setting window colorspace.');
  });
} catch (exception) {
  console.error(`Failed to set window colorspace. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setWindowContainerColor

```TypeScript
setWindowContainerColor(activeColor: string, inactiveColor: string): void
```

Sets the background color of the main window container for both when it has focus and when it does not. In the stage model, you need to call this API after [loadContent()](#loadcontent) or [setUIContent()](#setuicontent).

The background color you set here covers the entire window, including both the title bar and the content area. If you also use [setWindowBackgroundColor()](#setwindowbackgroundcolor), the content area shows the window background color, whereas the title bar shows the container background color.

**Since:** 20

**Required permissions:** ohos.permission.SET_WINDOW_TRANSPARENT

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| activeColor | string | Yes | window container color in active. |
| inactiveColor | string | Yes | window container color in inactive. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows are supported. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    windowStage.loadContent("pages/page2", (err: BusinessError) => {
      let errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('Succeeded in loading the content.');
      // Obtain the main window.
      let windowClass: window.Window | undefined = undefined;
      windowStage.getMainWindow((err: BusinessError, data) => {
        let errCode: number = err.code;
        if (errCode) {
          console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        windowClass = data;
        let activeColor: string = '#00000000';
        let inactiveColor: string = '#FF000000';
        try {
          windowClass.setWindowContainerColor(activeColor, inactiveColor);
          console.info('Succeeded in setting window container color.');
        } catch (exception) {
          console.error(`Failed to set the window container color. Cause code: ${exception.code}, message: ${exception.message}`);
        };
      });
    });
  }
}
```

## setWindowContainerModalColor

```TypeScript
setWindowContainerModalColor(activeColor: string, inactiveColor: string): void
```

Sets the background color of the main window container for both when it has focus and when it does not. In the stage model, you need to call this API after [loadContent()](#loadcontent) or [setUIContent()](#setuicontent).

The background color you set here covers the entire window, including both the title bar and the content area. If you also use [setWindowBackgroundColor()](#setwindowbackgroundcolor), the content area shows the window background color, whereas the title bar shows the container background color.

**Since:** 26.0.0

**Required permissions:** 
- API version 26 and later: ohos.permission.SET_WINDOW_ALPHA
- API versions 20 to 25: N/A

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| activeColor | string | Yes | window container color in active. |
| inactiveColor | string | Yes | window container color in inactive. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required or a non-system application calls the API.<br>**Applicable version:** 26.0.0 and later |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 20 - 24 |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows are supported. |

## setWindowCornerRadius

```TypeScript
setWindowCornerRadius(cornerRadius: number): Promise<void>
```

Sets the radius of the rounded corners for a child window or floating window. This API uses a promise to return the result.

If the radius of the rounded corner is too large, it may cause the three buttons (maximize, minimize, and close) to be clipped and make their hotspots less recognizable. Set an appropriate radius based on the window size.

Before calling this API, you can call [getWindowCornerRadius()](#getwindowcornerradius) to obtain the default radius of rounded corners of the window.

**Since:** 17

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cornerRadius | number | Yes | Radius of the rounded corners, measured in vp. The value is a floating-point number greater than or equal to 0.0. The value **0.0** means that the window does not use rounded corners. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: The corner radius is less than zero. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only subwindows and float windows are supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let promise = windowClass.setWindowCornerRadius(1.0);
  promise.then(() => {
    console.info('Succeeded in setting window corner radius.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set window corner radius. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set corner radius. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setWindowDecorHeight

```TypeScript
setWindowDecorHeight(height: number): void
```

Sets the height of the title bar of this window. This API takes effect for the window that has a title bar and a three-button area. In the stage model, this API must be used after the call of [loadContent](#loadcontent) or [setUIContent()](#setuicontent) takes effect.

For tablets, if this API is called outside of [free windows](../../../windowmanager/window-terminology.md#free-windows) mode, the change applies once the device switches to free windows mode. If this API is called in free windows mode, the change takes effect immediately.

When the main window transitions into full-screen mode, hovering the mouse over the hot zone of the window's title bar region will cause a floating title bar to appear, with a fixed height of 37 vp.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| height | number | Yes | Height of the title bar. It takes effect only for the window with the title bar. The value is an integer in the range [37,112]. The unit is vp. If a floating-point number is passed in, the value is rounded down. A value outside the range is invalid. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: Invalid parameter range. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |

**Examples**

```TypeScript
windowClass.setUIContent('pages/WindowPage').then(() => {
  let height: number = 50;
  try {
    windowClass?.setWindowDecorHeight(height);
    console.info(`Succeeded in setting the height of window decor: ${height}`);
  } catch (exception) {
    console.error(`Failed to set the height of window decor. Cause code: ${exception.code}, message: ${exception.message}`);
  }
})
```

## setWindowDecorVisible

```TypeScript
setWindowDecorVisible(isVisible: boolean): void
```

Sets whether the title bar is visible in the window. This API takes effect for the window that has a title bar or a three-button area. In the stage model, this API must be used after the call of [loadContent](#loadcontent) or [setUIContent()](#setuicontent) takes effect.

When the window title bar is hidden and the main window transitions into full-screen mode, hovering the cursor over the hot zone of the top window's title bar will cause a floating title bar to appear. To prevent the floating title bar from appearing, call [setTitleAndDockHoverShown()](#settitleanddockhovershown).

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isVisible | boolean | Yes | Whether the title bar is visible. **true** if visible, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation.<br>**Applicable version:** 11 - 19 |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let storage: LocalStorage = new LocalStorage();
storage.setOrCreate('storageSimpleProp', 121);
windowClass.loadContent("pages/page2", storage, (err: BusinessError) => {
  let errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in loading the content.');
  let isVisible = false;
  // Call setWindowDecorVisible.
  try {
      windowClass?.setWindowDecorVisible(isVisible);
  } catch (exception) {
      console.error(`Failed to set the visibility of window decor. Cause code: ${exception.code}, message: ${exception.message}`);
  }
});
```

## setWindowDelayRaiseOnDrag

```TypeScript
setWindowDelayRaiseOnDrag(isEnabled: boolean): void
```

Sets whether to enable delayed raising for the window. This API takes effect only for the main window and child windows.

If this API is not called or **false** is passed, the main window and child windows are raised immediately upon a left mouse button press by default.

When this API is called to enable delayed raising, in cross-window drag-and-drop situations, the window that contains the draggable component does not raise until the left mouse button is released, rather than raising immediately when the button is pressed.

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEnabled | boolean | Yes | Whether to enable delayed raising.<br>**true** to enable, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.function setWindowDelayRaiseOnDrag can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |

**Examples**

```TypeScript
try {
  windowClass.setWindowDelayRaiseOnDrag(true);
} catch (exception) {
  console.error(`Failed to set window delay raise. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setWindowFocusable

```TypeScript
setWindowFocusable(isFocusable: boolean): Promise<void>
```

Sets whether this window is focusable. This API uses a promise to return the result.

Starting from API version 22, if a virtual screen is created by calling [createVirtualScreen](arkts-arkui-display-createvirtualscreen-f.md) with **supportsFocus** set to **false**, windows on that virtual screen cannot call the current API to change their focusability. Attempting to do so will result in error code 1300002.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isFocusable | boolean | Yes | can be focus if true, or can not be focus if false. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. The screen of the window is not allowed to be focused. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isFocusable: boolean = true;
try {
  let promise = windowClass.setWindowFocusable(isFocusable);
  promise.then(() => {
    console.info('Succeeded in setting the window to be focusable.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the window to be focusable. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set the window to be focusable. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

<a id="setwindowfocusable-1"></a>

## setWindowFocusable

```TypeScript
setWindowFocusable(isFocusable: boolean, callback: AsyncCallback<void>): void
```

Sets whether this window is focusable. This API uses an asynchronous callback to return the result.

Starting from API version 22, if a virtual screen is created by calling [createVirtualScreen](arkts-arkui-display-createvirtualscreen-f.md) with **supportsFocus** set to **false**, windows on that virtual screen cannot call the current API to change their focusability. Attempting to do so will result in error code 1300002.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isFocusable | boolean | Yes | can be focus if true, or can not be focus if false. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. The screen of the window is not allowed to be focused. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isFocusable: boolean = true;
try {
  windowClass.setWindowFocusable(isFocusable, (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to set the window to be focusable. Cause code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in setting the window to be focusable.');
  });
} catch (exception) {
  console.error(`Failed to set the window to be focusable. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setWindowGrayScale

```TypeScript
setWindowGrayScale(grayScale: number): Promise<void>
```

Sets the grayscale effect for this window. This API uses a promise to return the result. This API can be called only after [loadContent()](#loadcontent) or [setUIContent()](#setuicontent) is called.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| grayScale | number | Yes | The value of gray scale. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

windowClass?.setUIContent('pages/Index', (error: BusinessError) => {
  if (error.code) {
    console.error(`Failed to set the content. Cause code: ${error.code}`);
    return;
  }
  console.info('Succeeded in setting the content.');
  let grayScale: number = 0.5;
  try {
    if (canIUse("SystemCapability.Window.SessionManager")) {
      let promise = windowClass?.setWindowGrayScale(grayScale);
      promise?.then(() => {
        console.info('Succeeded in setting the grayScale.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to set the grayScale. Cause code: ${err.code}, message: ${err.message}`);
      });
    }
  } catch (exception) {
    console.error(`Failed to set the grayScale. Cause code: ${exception.code}, message: ${exception.message}`);
  }
});
```

## setWindowKeepScreenOn

```TypeScript
setWindowKeepScreenOn(isKeepScreenOn: boolean): Promise<void>
```

Sets whether to keep the screen always on. This API uses a promise to return the result.

Set **isKeepScreenOn** to **true** only in necessary scenarios (such as navigation, video playback, drawing, and gaming scenarios). After exiting these scenarios, set the parameter to **false**. Do not use this API in other scenarios (such as no screen interaction or audio playback). When the system detects that the API is used in a non-standard manner, automatic screen-off may be invoked.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isKeepScreenOn | boolean | Yes | keep screen on if true, or not if false. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isKeepScreenOn: boolean = true;
try {
  let promise = windowClass.setWindowKeepScreenOn(isKeepScreenOn);
  promise.then(() => {
    console.info('Succeeded in setting the screen to be always on.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the screen to be always on. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set the screen to be always on. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

<a id="setwindowkeepscreenon-1"></a>

## setWindowKeepScreenOn

```TypeScript
setWindowKeepScreenOn(isKeepScreenOn: boolean, callback: AsyncCallback<void>): void
```

Sets whether to keep the screen always on. This API uses an asynchronous callback to return the result.

Set **isKeepScreenOn** to **true** only in necessary scenarios (such as navigation, video playback, drawing, and gaming scenarios). After exiting these scenarios, set the parameter to **false**. Do not use this API in other scenarios (such as no screen interaction or audio playback). When the system detects that the API is used in a non-standard manner, automatic screen-off may be invoked.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isKeepScreenOn | boolean | Yes | keep screen on if true, or not if false. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isKeepScreenOn: boolean = true;
try {
  windowClass.setWindowKeepScreenOn(isKeepScreenOn, (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to set the screen to be always on. Cause code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in setting the screen to be always on.');
  });
} catch (exception) {
  console.error(`Failed to set the screen to be always on. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setWindowLayoutFullScreen

```TypeScript
setWindowLayoutFullScreen(isLayoutFullScreen: boolean, callback: AsyncCallback<void>): void
```

Sets whether the main window layout or the child window layout is immersive. This API uses an asynchronous callback to return the result. It does not work when called by a system window.

An immersive layout means that the layout does not avoid the status bar or &lt;!--RP15--&gt;three-button navigation bar &lt;!--RP15End--&gt;, and components may overlap with them.

A non-immersive layout means that the layout avoids the status bar and &lt;!--RP15--&gt;three-button navigation bar<!-- RP15End-->, and components do not overlap with them.

**Since:** 9

**Deprecated since:** 12

**Substitutes:** [setWindowLayoutFullScreen](#setwindowlayoutfullscreen-1)(isLayoutFullScreen: boolean)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isLayoutFullScreen | boolean | Yes | Whether the layout of the window is immersive. (In immersive layout mode, the status bar and &lt;!--RP15--&gt;three-button navigation bar&lt;!--RP15End--&gt; remain visible.) **true** if immersive, **false** otherwise. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let isLayoutFullScreen = true;
      try {
        windowClass.setWindowLayoutFullScreen(isLayoutFullScreen, (err: BusinessError) => {
          const errCode: number = err.code;
          if (errCode) {
            console.error(`Failed to set the window layout to full-screen mode. Cause code: ${err.code}, message: ${err.message}`);
            return;
          }
          console.info('Succeeded in setting the window layout to full-screen mode.');
        });
      } catch (exception) {
        console.error(`Failed to set the window layout to full-screen mode. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

<a id="setwindowlayoutfullscreen-1"></a>

## setWindowLayoutFullScreen

```TypeScript
setWindowLayoutFullScreen(isLayoutFullScreen: boolean): Promise<void>
```

Sets whether the application main window layout or the application child window layout is immersive. This API uses a promise to return the result. It does not work when called by other windows, and no error is reported.

An immersive layout means that the layout does not avoid the status bar or &lt;!--RP15--&gt;three-button navigation bar &lt;!--RP15End--&gt;, and components may overlap with them.

A non-immersive layout means that the layout avoids the status bar and &lt;!--RP15--&gt;three-button navigation bar<!-- RP15End-->, and components do not overlap with them.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isLayoutFullScreen | boolean | Yes | The window can layout in full screen |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let isLayoutFullScreen = true;
      try {
        let promise = windowClass.setWindowLayoutFullScreen(isLayoutFullScreen);
        promise.then(() => {
          console.info('Succeeded in setting the window layout to full-screen mode.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to set the window layout to full-screen mode. Cause code: ${err.code}, message: ${err.message}`);
        });
      } catch (exception) {
        console.error(`Failed to set the window layout to full-screen mode. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

## setWindowLimits

```TypeScript
setWindowLimits(windowLimits: WindowLimits): Promise<WindowLimits>
```

Sets the size limits for this window. This API uses a promise to return the result.

By default, system size limits are provided. They are determined by the product configuration and cannot be modified.

If **setWindowLimits** has not been called, you can call [getWindowLimits](#getwindowlimits) or [getWindowLimitsVP](#getwindowlimitsvp) to obtain the system size limits.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| windowLimits | [WindowLimits](arkts-arkui-window-windowlimits-i.md) | Yes | Target size limits, in px or vp. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[WindowLimits](arkts-arkui-window-windowlimits-i.md)&gt; | Promise used to return the final size limits, which are the intersection between the passed-in size limits and the system size limits. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
  let windowLimits: window.WindowLimits = {
    maxWidth: 1500,
    maxHeight: 1000,
    minWidth: 500,
    minHeight: 400
  };
  let promise = windowClass.setWindowLimits(windowLimits);
    promise.then((data) => {
    console.info('Succeeded in changing the window limits. Cause:' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error(`Failed to change the window limits. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to change the window limits. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

<a id="setwindowlimits-1"></a>

## setWindowLimits

```TypeScript
setWindowLimits(windowLimits: WindowLimits, isForcible: boolean): Promise<WindowLimits>
```

Sets the size limits for this window. This API uses a promise to return the result.

By default, system size limits are provided. They are determined by the product configuration and cannot be modified.

If **setWindowLimits** has not been called, you can call [getWindowLimits](#getwindowlimits) or [getWindowLimitsVP](#getwindowlimitsvp) to obtain the system size limits.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| windowLimits | [WindowLimits](arkts-arkui-window-windowlimits-i.md) | Yes | Target size limits, in px or vp. |
| isForcible | boolean | Yes | Whether to forcibly set the window size limits.<br>When the unit of the input parameter [windowLimits](arkts-arkui-window-windowlimits-i.md) is vp, the process is performed based on value **false** regardless of whether **isForcible** is set to **true** or **false**. The minimum and maximum values of the window width and height depend on the system limit.<br>When the unit of the input parameter [windowLimits](arkts-arkui-window-windowlimits-i.md) is px: If **isForcible** is set to **true**, the minimum width and height of the window are subject to the smaller value between the system limit and 40 vp, and the maximum width and height of the window are subject to the system limit. If **isForcible** is set to **false**, the minimum and maximum widths and heights of the window are subject to the system limit. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[WindowLimits](arkts-arkui-window-windowlimits-i.md)&gt; | Promise used to return the new window size limits. <br>If the unit of the input parameter [windowLimits](arkts-arkui-window-windowlimits-i.md) is vp, the intersection of the input parameter and the default window size limit of the system is returned. <br>If the unit of the input parameter [windowLimits](arkts-arkui-window-windowlimits-i.md) is px: The intersection of the input parameter and the default window size limit of the system is returned when **isForcible** is set to **false**. The intersection of the input parameter and [the smaller value between the system limit and 40 vp, the maximum value of the system limit] is returned when **isForcible** is set to **true**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
  let windowLimits: window.WindowLimits = {
    maxWidth: 1500,
    maxHeight: 1000,
    minWidth: 100,
    minHeight: 100
  };
  let promise = windowClass.setWindowLimits(windowLimits, true);
  promise.then((data) => {
    console.info(`Succeeded in changing the window limits. Cause: ${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to change the window limits. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to change the window limits. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setWindowMask

```TypeScript
setWindowMask(windowMask: Array<Array<number>>): Promise<void>
```

Sets a mask for this window to get an irregularly shaped window. This API uses a promise to return the result. The mask is used to describe the shape of the irregularly shaped window. This API is available only for child windows and global floating windows.

When the size of an irregularly shaped window changes, the actual display content is the intersection of the mask size and the window size.

Error code 1300002 may be returned only when multiple threads operate the same window. Error code 401 is returned when the window is destroyed.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| windowMask | Array&lt;Array&lt;number&gt;&gt; | Yes | Mask. The value can only be a two-dimensional array containing the window size in pixels, with each element in the array set to either **0** or **1**. The value **0** indicates that the pixel is transparent, and **1** indicates that the pixel is opaque. If the passed-in pixel array does not match the window size or the value of any element in the array is not **0** or **1**, the value is invalid. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only subwindows and float windows are supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
  let maskWidth = windowClass.getWindowProperties().windowRect.width;
  let maskHeight = windowClass.getWindowProperties().windowRect.height;
  let windowMask = Array<Array<number>>(maskHeight).fill([]).map((_, row) => {
    let array = Array<number>(maskWidth);
    for (let i = 0 ; i < maskWidth; i++) {
      array[i] = (i + row) > (maskWidth + maskHeight) / 2 ? 1 : 0;
    }
    return array;
  });
  let promise = windowClass.setWindowMask(windowMask);
  promise.then(() => {
    console.info('Succeeded in setting the window mask.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the window mask. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set the window mask. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setWindowMaskWithAlpha

```TypeScript
setWindowMaskWithAlpha(windowMask: Uint8Array, maskWidth: number, maskHeight: number): Promise<void>
```

Set the window mask using a per-pixel alpha array

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| windowMask | Uint8Array | Yes | The windowMask contains only per-pixel alpha transparency values. Valid range: 0(full transparent) to 255(full opaque), size must equal (maskWidth * maskHeight). |
| maskWidth | number | Yes | Mask width in pixels. Must equal the target window width. |
| maskHeight | number | Yes | Mask height in pixels. Must equal the target window height. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only subwindows and float windows are supported. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: 1. The maskWidth is not equal to the window width or the maskHeight is not equal to the window height. 2. The length of windowMask is not equal to maskWidth multiplied by maskHeight. |

## setWindowPrivacyMode

```TypeScript
setWindowPrivacyMode(isPrivacyMode: boolean): Promise<void>
```

Sets whether this window is in privacy mode. This API uses a promise to return the result.

A window in privacy mode cannot be captured or recorded.

When a window in privacy mode is moved to the background, it displays as a white overlay or privacy mask in the multi-tasking view.

If this API is not called, the privacy mode is disabled by default, and the window can be captured or recorded.

**Since:** 9

**Required permissions:** ohos.permission.PRIVACY_WINDOW

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isPrivacyMode | boolean | Yes | in private mode if true, or not if false. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. Possible cause: Need ohos.permission.PRIVACY_WINDOW permission. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isPrivacyMode: boolean = true;
try {
  let promise = windowClass.setWindowPrivacyMode(isPrivacyMode);
  promise.then(() => {
    console.info('Succeeded in setting the window to privacy mode.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the window to privacy mode. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set the window to privacy mode. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

<a id="setwindowprivacymode-1"></a>

## setWindowPrivacyMode

```TypeScript
setWindowPrivacyMode(isPrivacyMode: boolean, callback: AsyncCallback<void>): void
```

Sets whether this window is in privacy mode. This API uses an asynchronous callback to return the result.

A window in privacy mode cannot be captured or recorded.

When a window in privacy mode is moved to the background, it displays as a white overlay or privacy mask in the multi-tasking view.

If this API is not called, the privacy mode is disabled by default, and the window can be captured or recorded.

**Since:** 9

**Required permissions:** ohos.permission.PRIVACY_WINDOW

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isPrivacyMode | boolean | Yes | in private mode if true, or not if false. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. Possible cause: Need ohos.permission.PRIVACY_WINDOW permission. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isPrivacyMode: boolean = true;
try {
  windowClass.setWindowPrivacyMode(isPrivacyMode, (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to set the window to privacy mode. Cause code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in setting the window to privacy mode.');
  });
} catch (exception) {
  console.error(`Failed to set the window to privacy mode. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setWindowShadowEnabled

```TypeScript
setWindowShadowEnabled(enable: boolean): Promise<void>
```

Sets whether the main window displays a shadow. This API uses a promise to return the result. By default, the main window displays a shadow unless you explicitly change it with this API.

**Since:** 20

**Required permissions:** ohos.permission.SET_WINDOW_TRANSPARENT

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Enable or disable window shadow. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows are supported. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    windowStage.loadContent("pages/page2", (err: BusinessError) => {
      let errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('Succeeded in loading the content.');
      // Obtain the main window.
      let windowClass: window.Window | undefined = undefined;
      windowStage.getMainWindow((err: BusinessError, data) => {
        let errCode: number = err.code;
        if (errCode) {
          console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        windowClass = data;
        let enable = true;
        let promise = windowClass.setWindowShadowEnabled(enable);
        promise.then(() => {
          console.info('Succeeded in setting window shadow.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to set the window shadow. Cause code: ${err.code}, message: ${err.message}`);
        });
      });
    });
  }
}
```

## setWindowShadowRadius

```TypeScript
setWindowShadowRadius(radius: number): void
```

Sets the blur radius of the shadow on the edges of a child window or floating window.

**Since:** 17

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| radius | number | Yes | Radius of the shadow, measured in px. The value is a floating-point number greater than or equal to 0.0, and the value **0.0** means that the shadow is disabled for the window borders. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: The shadow radius is less than zero. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only subwindows and float windows are supported. |

**Examples**

```TypeScript
try {
  windowClass.setWindowShadowRadius(4.0);
} catch (exception) {
  console.error(`Failed to set shadow. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setWindowSystemBarEnable

```TypeScript
setWindowSystemBarEnable(names: Array<'status' | 'navigation'>, callback: AsyncCallback<void>): void
```

&lt;!--RP14--&gt;Sets whether to show the status bar and three-button navigation bar in the main window. The visibility of the status bar and three-button navigation bar is controlled by **status** and **navigation**, respectively.&lt;!--RP14End--&gt; This API uses an asynchronous callback to return the result.

From API version 12, &lt;!--RP5--&gt;this API does not take effect on 2-in-1 devices.&lt;!--RP5End--&gt;

The return value does not indicate that the status bar and &lt;!--RP15--&gt;three-button navigation bar&lt;!--RP15End--&gt; are shown or hidden. This API does not take effect when it is called by a child window. The configuration does not take effect in non-full-screen mode (such as floating window or split-screen mode).

**Since:** 9

**Deprecated since:** 12

**Substitutes:** [setWindowSystemBarEnable](#setwindowsystembarenable-1)(names: Array&lt;'status' | 'navigation'&gt;)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| names | Array&lt;'status' &#124; 'navigation'&gt; | Yes | Whether to show the status bar and &lt;!--RP15--&gt;three-button navigation bar&lt;!--RP15End--&gt; in full-screen mode.<br>For example, to show all of them, set this parameter to **['status','navigation']**. If this parameter is set to [], they are hidden. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
// The following assumes that all of them are hidden.
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let names: Array<'status' | 'navigation'> = [];
      try {
        windowClass.setWindowSystemBarEnable(names, (err: BusinessError) => {
          const errCode: number = err.code;
          if (errCode) {
            console.error(`Failed to set the system bar to be invisible. Cause code: ${err.code}, message: ${err.message}`);
            return;
          }
          console.info('Succeeded in setting the system bar to be invisible.');
        });
      } catch (exception) {
        console.error(`Failed to set the system bar to be invisible. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

<a id="setwindowsystembarenable-1"></a>

## setWindowSystemBarEnable

```TypeScript
setWindowSystemBarEnable(names: Array<'status'|'navigation'>): Promise<void>
```

&lt;!--RP14--&gt;Sets whether to show the status bar and three-button navigation bar in the main window. The visibility of the status bar and three-button navigation bar is controlled by **status** and **navigation**, respectively.&lt;!--RP14End--&gt; This API uses a promise to return the result.

The return value does not indicate that the status bar and &lt;!--RP15--&gt;three-button navigation bar&lt;!--RP15End--&gt; are shown or hidden. The setting does not take effect when the main window is in non-full-screen or non-maximized mode (such as floating windows or split-screen mode). It takes effect once the main window enters full-screen or maximized mode.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| names | Array&lt;'status' &#124; 'navigation'&gt; | Yes | The set of system bar |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
// The following assumes that all of them are hidden.
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let names: Array<'status' | 'navigation'> = [];
      try {
        let promise = windowClass.setWindowSystemBarEnable(names);
        promise.then(() => {
          console.info('Succeeded in setting the system bar to be invisible.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to set the system bar to be invisible. Cause code: ${err.code}, message: ${err.message}`);
        });
      } catch (exception) {
        console.error(`Failed to set the system bar to be invisible. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

## setWindowSystemBarProperties

```TypeScript
setWindowSystemBarProperties(systemBarProperties: SystemBarProperties, callback: AsyncCallback<void>): void
```

Sets the properties of the <!--Del-->three-button navigation bar and <!--DelEnd-->status bar of the main window. This API uses an asynchronous callback to return the result. &lt;!--RP5--&gt;This API does not take effect on 2-in-1 devices.&lt;!--RP5End--&gt;

This API does not take effect when it is called by a child window.

**Since:** 9

**Deprecated since:** 12

**Substitutes:** [setWindowSystemBarProperties](#setwindowsystembarproperties-1)(systemBarProperties: SystemBarProperties)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| systemBarProperties | [SystemBarProperties](arkts-arkui-window-systembarproperties-i.md) | Yes | <!--Del-->Properties of the <!--Del-->three-button navigation bar and <!--DelEnd-->status bar. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let SystemBarProperties: window.SystemBarProperties = {
        statusBarColor: '#ff00ff',
        navigationBarColor: '#00ff00',
        // The following properties are supported since API version 8.
        statusBarContentColor: '#ffffff',
        navigationBarContentColor: '#00ffff'
      };
      try {
        windowClass.setWindowSystemBarProperties(SystemBarProperties, (err: BusinessError) => {
          const errCode: number = err.code;
          if (errCode) {
            console.error(`Failed to set the system bar properties. Cause code: ${err.code}, message: ${err.message}`);
            return;
          }
          console.info('Succeeded in setting the system bar properties.');
        });
      } catch (exception) {
        console.error(`Failed to set the system bar properties. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

<a id="setwindowsystembarproperties-1"></a>

## setWindowSystemBarProperties

```TypeScript
setWindowSystemBarProperties(systemBarProperties: SystemBarProperties): Promise<void>
```

Sets the properties of the <!--Del-->three-button navigation bar and <!--DelEnd-->status bar of the main window. This API uses a promise to return the result.

This API does not take effect when it is called by a child window. The setting does not take effect when the main window is in non-full-screen or non-maximized mode (such as floating windows or split-screen mode). It takes effect once the main window enters full-screen or maximized mode.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| systemBarProperties | [SystemBarProperties](arkts-arkui-window-systembarproperties-i.md) | Yes | <!--Del-->Properties of the <!--Del-->three-button navigation bar and <!--DelEnd-->status bar. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let SystemBarProperties: window.SystemBarProperties = {
        statusBarColor: '#ff00ff',
        navigationBarColor: '#00ff00',
        // The following properties are supported since API version 8.
        statusBarContentColor: '#ffffff',
        navigationBarContentColor: '#00ffff'
      };
      try {
        let promise = windowClass.setWindowSystemBarProperties(SystemBarProperties);
        promise.then(() => {
          console.info('Succeeded in setting the system bar properties.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to set the system bar properties. Cause code: ${err.code}, message: ${err.message}`);
        });
      } catch (exception) {
        console.error(`Failed to set the system bar properties. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

## setWindowTitle

```TypeScript
setWindowTitle(titleName: string): Promise<void>
```

Sets the window title. This API uses a promise to return the result. In the stage model, this API must be used after the call of [loadContent](#loadcontent) or [setUIContent()](#setuicontent) takes effect.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| titleName | string | Yes | Window title. The title display area should not go past the left side of the three- button area of the system. Any part that goes beyond will show as an ellipsis. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let title = "title";
  windowClass.setWindowTitle(title).then(() => {
    console.info('Succeeded in setting the window title.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the window title. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set the window title. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setWindowTitleButtonVisible

```TypeScript
setWindowTitleButtonVisible(isMaximizeButtonVisible: boolean, isMinimizeButtonVisible: boolean, isCloseButtonVisible?: boolean): void
```

Shows or hides the maximize, minimize, and close buttons on the title bar of the main window.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isMaximizeButtonVisible | boolean | Yes | Whether to show the maximize button. **true** to show, **false** otherwise. If the maximize button is hidden, the corresponding restore button is also hidden in the maximize scenario. |
| isMinimizeButtonVisible | boolean | Yes | Whether to show the minimize button. **true** to show, **false** otherwise. |
| isCloseButtonVisible | boolean | No | Whether to show the close button. **true** to show, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Only main windows and subwindows with subwindowoptions.zlevelaboveparentloosened set to true are supported. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    // Load the page corresponding to the main window.
    windowStage.loadContent('pages/Index', (err) => {
      let mainWindow: window.Window | undefined = undefined;
      // Obtain the main window.
      windowStage.getMainWindow().then(
        data => {
          if (!data) {
            console.error('Failed to get main window. Cause: The data is undefined.');
            return;
          }
          mainWindow = data;
          console.info('Succeeded in obtaining the main window. Data: ' + JSON.stringify(data));
          // Call setWindowTitleButtonVisible to hide the maximize, minimize, and close buttons on the title bar of the main window.
          mainWindow.setWindowTitleButtonVisible(false, false, false);
        }
      ).catch((err: BusinessError) => {
          if(err.code){
            console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
          }
      });
    });
  }
}
```

## setWindowTitleMoveEnabled

```TypeScript
setWindowTitleMoveEnabled(enabled: boolean): void
```

Enables or disables the capability to move the window (either main window or child window) by dragging its title bar and to maximize the window with a double-click. When this capability is disabled, you can use [startMoving()](#startmoving) to move the window by dragging in the application's hot zone and use [maximize()](#maximize) to maximize the window. In the stage model, this API must be used after the call of [loadContent](#loadcontent) or [setUIContent()](#setuicontent) takes effect.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable the capability to move the window by dragging the title bar and to maximize the window with a double-click. **true** to enable, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows and subwindows are supported. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    try {
      windowStage.loadContent("pages/Index").then(() =>{
        let windowClass = windowStage.getMainWindowSync();
        let enabled = false;
        windowClass.setWindowTitleMoveEnabled(enabled);
        console.info(`Succeeded in setting the the window title move enabled: ${enabled}`);
      });
    } catch (exception) {
      console.error(`Failed to set the window title move enabled. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

## setWindowTopmost

```TypeScript
setWindowTopmost(isWindowTopmost: boolean): Promise<void>
```

Places the main window above all the other windows of the application. This API uses a promise to return the result.

Applications use custom shortcut keys to pin or unpin the main window.

**Since:** 14

**Required permissions:** ohos.permission.WINDOW_TOPMOST

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isWindowTopmost | boolean | Yes | Whether to pin the main window on top. **true** to pin, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows are supported. |

**Examples**

```TypeScript
// Index.ets
import { window } from '@kit.ArkUI';
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let windowClass: window.Window | undefined;
let keyUpEventAry: string[] = [];

@Entry
@Component
struct Index {
  private context = (this.getUIContext()?.getHostContext() as common.UIAbilityContext);
  private windowStage = this.context.windowStage;

  build() {
    RelativeContainer() {
      Button("Pin")
        .onClick(() => {
          try {
            windowClass = this.windowStage.getMainWindowSync();
            // The value true indicates to pin the window on top, and value false indicates to unpin the window.
            let isWindowTopmost: boolean = true;
            let promiseTopmost = windowClass.setWindowTopmost(isWindowTopmost);
            promiseTopmost.then(() => {
              console.info('Succeeded in setting the main window to be topmost.');
            }).catch((err: BusinessError) => {
              console.error(`Failed to set the main window to be topmost. Cause code: ${err.code}, message: ${err.message}`);
            });
          } catch (exception) {
            console.error(`Failed to obtain the top window. Cause code: ${exception.code}, message: ${exception.message}`)
          }
        })
    }
    .height('100%')
    .width('100%')
    .onKeyEvent((event) => {
      if(event) {
        if(event.type === KeyType.Down) {
          keyUpEventAry = [];
        }
        if(event.type === KeyType.Up) {
          keyUpEventAry.push(event.keyText);
          // Press Ctrl+T to pin or unpin the main window.
          if(windowClass && keyUpEventAry.includes('KEYCODE_CTRL_LEFT') && keyUpEventAry.includes('KEYCODE_T')) {
            let isWindowTopmost: boolean = false;
            windowClass.setWindowTopmost(isWindowTopmost);
          }
        }
      }
    })
  }
}
```

## setWindowTouchable

```TypeScript
setWindowTouchable(isTouchable: boolean): Promise<void>
```

Sets whether this window is touchable. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isTouchable | boolean | Yes | is touchable if true, or not if false. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isTouchable: boolean = true;
try {
  let promise = windowClass.setWindowTouchable(isTouchable);
  promise.then(() => {
    console.info('Succeeded in setting the window to be touchable.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the window to be touchable. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set the window to be touchable. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

<a id="setwindowtouchable-1"></a>

## setWindowTouchable

```TypeScript
setWindowTouchable(isTouchable: boolean, callback: AsyncCallback<void>): void
```

Sets whether this window is touchable. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isTouchable | boolean | Yes | is touchable if true, or not if false. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isTouchable = true;
try {
  windowClass.setWindowTouchable(isTouchable, (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to set the window to be touchable. Cause code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in setting the window to be touchable.');
  });
} catch (exception) {
  console.error(`Failed to set the window to be touchable. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setWindowTransitionAnimation

```TypeScript
setWindowTransitionAnimation(transitionType: WindowTransitionType, animation: TransitionAnimation): Promise<void>
```

Adds a transition animation to windows in specific scenarios.

Currently, this API can be used only on the main window of an application.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transitionType | [WindowTransitionType](arkts-arkui-window-windowtransitiontype-e.md) | Yes | Scene of the transition animation. Currently, only the destruction scene is supported. |
| animation | [TransitionAnimation](arkts-arkui-window-transitionanimation-i.md) | Yes | Configuration of the transition animation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: 1. Invalid parameter range; 2. Invalid parameter length. |

**Examples**

```TypeScript
// EntryAbility.ets
import { BusinessError } from '@kit.BasicServicesKit';
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      try {
        const animationConfig: window.WindowAnimationConfig = {
          duration: 1000,
          curve: window.WindowAnimationCurve.LINEAR,
        };
        const transitionAnimation: window.TransitionAnimation = {
          opacity: 0.5,
          config: animationConfig
        };
        let promise = windowClass.setWindowTransitionAnimation(window.WindowTransitionType.DESTROY, transitionAnimation);
        promise.then((data) => {
          console.info('Succeeded in setting window transition animation. Cause:' + JSON.stringify(data));
        }).catch((err: BusinessError) => {
          console.error(`Failed to set window transition animation. Cause code: ${err.code}, message: ${err.message}`);
        });
      } catch (exception) {
        console.error(`Failed to obtain the window status of window. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    })
  }
}
```

## show

```TypeScript
show(callback: AsyncCallback<void>): void
```

Shows this window. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [showWindow](#showwindow)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

windowClass.show((err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to show the window. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in showing the window.');
});
```

<a id="show-1"></a>

## show

```TypeScript
show(): Promise<void>
```

Shows this window. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [showWindow](#showwindow)()

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = windowClass.show();
promise.then(() => {
  console.info('Succeeded in showing the window.');
}).catch((err: BusinessError) => {
  console.error(`Failed to show the window. Cause code: ${err.code}, message: ${err.message}`);
});
```

## showWindow

```TypeScript
showWindow(callback: AsyncCallback<void>): void
```

Shows this window. This API uses an asynchronous callback to return the result. This API takes effect only for a system window, application child window, modal window, or global floating window. For the main window of an application, this API moves it at the top when the main window is already displayed.

> **NOTE:** 
> 
> Before calling this API, you are advised to load the page by using
> [loadContent](#loadcontent) or
> [setUIContent](#setuicontent-1). If the main window has not
> finished loading and you call this API directly, the starting window keeps showing. Similarly, if the system
> window, application child window, modal window, or global floating window has finished loading and you call
> this API directly, the window is in the foreground but is not visible.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        console.error('Failed to load the content. Cause: %{public}s', JSON.stringify(err));
        return;
      }
      console.info('Succeeded in loading the content.');
      try {
        // Create a child window.
        windowStage.createSubWindow("testSubWindow").then((subWindow) => {
          if (subWindow == null) {
            console.error('Failed to create the subWindow. Cause: The data is empty');
            return;
          }
          subWindow.setUIContent('pages/Index', (err) => {
            if (err.code) {
              console.error('Failed to load the subWindow content. Cause: %{public}s', JSON.stringify(err));
              return;
            }
            console.info('Succeeded in loading the subWindow content.');
            try {
              subWindow.showWindow((err: BusinessError) => {
                const errCode: number = err.code;
                if (errCode) {
                  console.error(`Failed to show the window. Error code: ${err.code}, message: ${err.message}`);
                  return;
                }
                console.info('Succeeded in showing the window.');
              });
            } catch (exception) {
              console.error(`Failed to show the window. Cause code: ${exception.code}, message: ${exception.message}`);
            }
          })
        });
      } catch (exception) {
        console.error(`Failed to create the sub window. Cause code: ${exception.code}, message: ${exception.message}`);
      }
  });
  }
}
```

<a id="showwindow-1"></a>

## showWindow

```TypeScript
showWindow(): Promise<void>
```

Shows this window. This API uses a promise to return the result. This API takes effect only for a system window, application child window, modal window, or global floating window. For the main window of an application, this API moves it at the top when the main window is already displayed.

> **NOTE:** 
> 
> Before calling this API, you are advised to load the page by using
> [loadContent](#loadcontent) or
> [setUIContent](#setuicontent-1). If the main window has not
> finished loading and you call this API directly, the starting window keeps showing. Similarly, if the system
> window, application child window, modal window, or global floating window has finished loading and you call
> this API directly, the window is in the foreground but is not visible.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |

**Examples**

```TypeScript
// EntryAbility.ets

import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        console.error('Failed to load the content. Cause: %{public}s', JSON.stringify(err));
        return;
      }
      console.info('Succeeded in loading the content.');
      try {
        // Create a child window.
        windowStage.createSubWindow("testSubWindow").then((subWindow) => {
          if (subWindow == null) {
            console.error('Failed to create the subWindow. Cause: The data is empty');
            return;
          }
          subWindow.setUIContent('pages/Index', (err) => {
            if (err.code) {
              console.error('Failed to load the subWindow content. Cause: %{public}s', JSON.stringify(err));
              return;
            }
            console.info('Succeeded in loading the subWindow content.');
            try {
              let promise = subWindow.showWindow();
              promise.then(() => {
                console.info('Succeeded in showing the window.');
              }).catch((err: BusinessError) => {
                console.error(`Failed to show the window. Error code: ${err.code}, message: ${err.message}`);
              });
            } catch (exception) {
              console.error(`Failed to show window. Cause code: ${exception.code}, message: ${exception.message}`);
            }
          });
        });
      } catch (exception) {
        console.error(`Failed to create the sub window. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

<a id="showwindow-2"></a>

## showWindow

```TypeScript
showWindow(options: ShowWindowOptions): Promise<void>
```

Shows this window or moves an already visible application main window to the top of the stack. You can pass options to control the window display behavior. This API uses a promise to return the result.

This API can be used only for application child windows, application main windows, global floating windows, and system windows, excluding windows of the TYPE_DIALOG type and modal child windows (windows that have the modal property enabled via **setSubWindowModal**).

> **NOTE:** 
> 
> Before calling this API, you are advised to load the page by using
> [loadContent](#loadcontent) or
> [setUIContent](#setuicontent-1). If the main window has not
> finished loading and you call this API directly, the starting window keeps showing. Similarly, if the system
> window, application child window, or global floating window has finished loading and you call this API directly
> , the window is in the foreground but is not visible.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ShowWindowOptions](arkts-arkui-window-showwindowoptions-i.md) | Yes | options of window shown |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function showWindow cannot work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Modal subwindow and dialog window cannot set focusOnShow. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter validation error. Possible cause: 1. The value of the parameter is out of the allowed range; 2. The length of the parameter exceeds the allowed length; 3. The parameter format is incorrect. |

**Examples**

```TypeScript
// EntryAbility.ets
import { window } from '@kit.ArkUI';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        console.error('Failed to load the content. Cause: %{public}s', JSON.stringify(err));
        return;
      }
      console.info('Succeeded in loading the content.');
      // Create a child window.
      try {
        windowStage.createSubWindow('subWindow').then((data) => {
          if (data == null) {
            console.error('Failed to create the subWindow. Cause: The data is empty');
            return;
          }
          data.setUIContent('pages/Index', (err) => {
            if (err.code) {
              console.error('Failed to load the subWindow content. Cause: %{public}s', JSON.stringify(err));
              return;
            }
            console.info('Succeeded in loading the subWindow content.');
            let options: window.ShowWindowOptions = {
              focusOnShow: false
            };
            try {
              data.showWindow(options).then(() => {
                console.info('Succeeded in showing window');
              }).catch((err: BusinessError) => {
                console.error(`Failed to show window. Error code: ${err.code}, message: ${err.message}`);
              });
            } catch (exception) {
              console.error(`Failed to show window. Cause code: ${exception.code}, message: ${exception.message}`);
            }
          });
        });
      } catch (exception) {
        console.error(`Failed to create the sub window. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

## snapshot

```TypeScript
snapshot(callback: AsyncCallback<image.PixelMap>): void
```

Captures this window. This API uses an asynchronous callback to return the result. If privacy mode is enabled for the current window (using [setWindowPrivacyMode](#setwindowprivacymode-1)), taking a screenshot will result in a blank screen.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Get pixelMap failed; 3. Internal task error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

windowClass.snapshot((err: BusinessError, pixelMap: image.PixelMap) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to snapshot window. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in snapshotting window. Pixel bytes number: ' + pixelMap.getPixelBytesNumber());
  pixelMap.release(); // Release the memory in time after the PixelMap is used.
});
```

<a id="snapshot-1"></a>

## snapshot

```TypeScript
snapshot(): Promise<image.PixelMap>
```

Captures this window. If privacy mode is enabled for the current window (using [setWindowPrivacyMode](#setwindowprivacymode-1)), taking a screenshot will result in a blank screen.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Promise used to return the window screenshot. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Get pixelMap failed; 3. Internal task error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

let promise = windowClass.snapshot();
promise.then((pixelMap: image.PixelMap) => {
  console.info('Succeeded in snapshotting window. Pixel bytes number: ' + pixelMap.getPixelBytesNumber());
  pixelMap.release(); // Release the memory in time after the PixelMap is used.
}).catch((err: BusinessError) => {
  console.error(`Failed to snapshot window. Cause code: ${err.code}, message: ${err.message}`);
});
```

## snapshotIgnorePrivacy

```TypeScript
snapshotIgnorePrivacy(): Promise<image.PixelMap>
```

Captures this window. This API can be called to obtain the screenshot of the current window even if privacy mode is enabled for the current window (using [setWindowPrivacyMode](#setwindowprivacymode-1)).

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Promise used to return the window screenshot. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function snapshotIgnorePrivacy can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Create pixelMap failed; 3. Internal task error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

let promise = windowClass.snapshotIgnorePrivacy();
promise.then((pixelMap: image.PixelMap) => {
  console.info('Succeeded in snapshotting window. Pixel bytes number: ' + pixelMap.getPixelBytesNumber());
  pixelMap.release(); // Release the memory in time after the PixelMap is used.
}).catch((err: BusinessError) => {
  console.error(`Failed to snapshot window. Cause code: ${err.code}, message: ${err.message}`);
});
```

## snapshotSync

```TypeScript
snapshotSync(): image.PixelMap
```

Captures this window. This API returns the result synchronously. If privacy mode is enabled for the current window (using [setWindowPrivacyMode](#setwindowprivacymode-1)), taking a screenshot will result in a blank screen.

In the stage model, this API must be used after the call of [loadContent](#loadcontent) or [setUIContent()](#setuicontent) takes effect.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | Window screenshot. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Create pixelMap failed. |
| [1300018](../errorcode-window.md#1300018-api-call-timeout) | Timeout. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

try {
  let pixelMap = windowClass.snapshotSync();
  console.info(`Succeeded in snapshotting window`);
  pixelMap.release(); // Release the memory in time after the PixelMap is used.
} catch (exception) {
  console.error(`Failed to snapshot window. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## startMoving

```TypeScript
startMoving(): Promise<void>
```

In [freeform window](../../../windowmanager/window-terminology.md#freeform-window) mode, this API takes effect for system windows, application main windows, application child windows, global floating windows, and modal windows. In non-freeform window mode, this API takes effect only for system windows, application child windows, global floating windows, and modal windows. Starts moving this window. This API uses a promise to return the result.

The window moves along with the cursor or touch point only when this API is called in the callback function of onTouch, where the event type is **TouchType.Down**.

In click-and-drag scenarios, if you do not want the drag to start as soon as you press down, you can call this API when the event type is [TouchType.Move](arkts-arkui-touchtype-e.md) (as long as **TouchType.Down** has already been triggered) to start the moving effect.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300001](../errorcode-window.md#1300001-repeated-operation) | Repeated operation. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type, main windows are not supported in non-free window mode. |

**Examples**

```TypeScript
// Index.ets
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private isTouchDown: boolean = false;
  build() {
    Row() {
      Column() {
        Blank('160')
          .color(Color.Red)
          .onTouch((event: TouchEvent) => {
            if(event.type == TouchType.Down){
              this.isTouchDown = true;
            } else if (event.type === TouchType.Move && this.isTouchDown) {
              try {
                let context = this.getUIContext()?.getHostContext();
                if (!context) {
                  console.error('Failed to get host context.');
                  return;
                }
                window.getLastWindow(context).then((data)=>{
                  if (!data) {
                    console.error('Failed to get last window.');
                    return;
                  }
                  let windowClass: window.Window = data;
                  windowClass.startMoving().then(() => {
                    console.info('Succeeded in starting moving window.')
                  }).catch((err: BusinessError) => {
                    console.error(`Failed to start moving. Cause code: ${err.code}, message: ${err.message}`);
                  });
                });
              } catch (exception) {
                console.error(`Failed to start moving window. Cause code: ${exception.code}, message: ${exception.message}`);
              }
            } else {
              this.isTouchDown = false;
            }
          })
      }.width('100%')
    }.height('100%').width('100%')
  }
}
```

<a id="startmoving-1"></a>

## startMoving

```TypeScript
startMoving(offsetX: number, offsetY: number): Promise<void>
```

Specifies the cursor position within the window and moves the window. This API uses a promise to return the result.

When windows within the same application are split or merged, and the mouse is pressed down to move the new window directly, the cursor may move outside the window if it moves too quickly. This API allows you to set the cursor position within the window during movement. It first adjusts the window to the cursor position before starting to move the window.

The window moves along with the cursor only when this API is called in the callback function of onTouch, where the event type is **TouchType.Down**.

In click-and-drag scenarios, if you do not want the drag to start as soon as you press down, you can call this API when the event type is [TouchType.Move](arkts-arkui-touchtype-e.md) (as long as **TouchType.Down** has already been triggered) to start the moving effect.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offsetX | number | Yes | X-axis offset of the cursor position relative to the top-left corner of the window during movement, measured in px. This parameter only accepts integer values; any floating-point input will be rounded down. Negative values or values exceeding the window width are invalid. The window width can be obtained from [WindowProperties](arkts-arkui-window-windowproperties-i.md). |
| offsetY | number | Yes | Y-axis offset of the cursor position relative to the top-left corner of the window during movement, measured in px. This parameter only accepts integer values; any floating-point input will be rounded down. Negative values or values exceeding the window height are invalid. The window height can be obtained from [WindowProperties](arkts-arkui-window-windowproperties-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300001](../errorcode-window.md#1300001-repeated-operation) | Repeated operation. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. |

**Examples**

```TypeScript
// Index.ets
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private isTouchDown: boolean = false;
  build() {
    Row() {
      Column() {
        Blank('160')
          .color(Color.Red)
          .onTouch((event: TouchEvent) => {
            if(event.type == TouchType.Down){
              this.isTouchDown = true;
            } else if (event.type === TouchType.Move && this.isTouchDown) {
              try {
                let context = this.getUIContext()?.getHostContext();
                if (!context) {
                  console.error('Failed to get host context.');
                  return;
                }
                window.getLastWindow(context).then((data)=>{
                  let windowClass: window.Window = data;
                  windowClass.startMoving(100, 50).then(() => {
                    console.info('Succeeded in starting moving window.')
                  }).catch((err: BusinessError) => {
                    console.error(`Failed to start moving. Cause code: ${err.code}, message: ${err.message}`);
                  });
                });
              } catch (exception) {
                console.error(`Failed to start moving window. Cause code: ${exception.code}, message: ${exception.message}`);
              }
            } else {
              this.isTouchDown = false;
            }
          })
      }.width('100%')
    }.height('100%').width('100%')
  }
}
```

## stopMoving

```TypeScript
stopMoving(): Promise<void>
```

Stops window movement when a window is being dragged. This API uses a promise to return the result.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {

  onWindowStageCreate(windowStage: window.WindowStage) {
    try {
      let windowClass = windowStage.getMainWindowSync();
      windowClass.on('windowRectChange', (data: window.RectChangeOptions) => {
        if (data.reason === window.RectChangeReason.MOVE) {
          windowClass.stopMoving().then(() => {
            console.info('Succeeded in stopping moving window.')
          }).catch((err: BusinessError) => {
            console.error(`Failed to stop moving. Cause code: ${err.code}, message: ${err.message}`);
          });
        }
      });
    } catch (exception) {
      console.error(`Failed to stop moving window. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```
