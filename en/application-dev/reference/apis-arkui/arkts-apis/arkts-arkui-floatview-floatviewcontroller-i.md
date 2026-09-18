# FloatViewController

Defines a float view controller instance, which is used to start and stop the float view and register callbacks.

Before calling the following APIs, you must use [floatView.create()](arkts-arkui-floatview-create-f.md) to create a float view controller instance (that is, **floatViewController**).

**Since:** 26.0.0

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { floatView } from '@kit.ArkUI';
```

## getWindowProperties

```TypeScript
getWindowProperties(): FloatViewProperties
```

Obtains the properties of the float view.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| [FloatViewProperties](arkts-arkui-floatview-floatviewproperties-i.md) | Properties of the float view. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The float view controller object is null. |
| [1300031](../errorcode-window.md#1300031-operation-not-supported-in-the-current-float-view-state) | This operation is not supported on the float view in the current state. Possible cause: The float view window has not started, has stopped, or is in an error state. |

**Examples**

```TypeScript
try {
  // Obtain the properties of the float view.
  let properties: floatView.FloatViewProperties | undefined = this.floatViewController?.getWindowProperties();
  console.info('Float view properties: ' + JSON.stringify(properties));
} catch (e) {
  console.error(`Failed to get window properties. Cause:${e.code}, message:${e.message}`);
}
```

## offLimitsChange

```TypeScript
offLimitsChange(callback?: Callback<FloatViewLimits>): void
```

Unregisters the callback for listening to limit changes of the float view.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[FloatViewLimits](arkts-arkui-floatview-floatviewlimits-i.md)&gt; | No | Callback used to return the limit change information of the current float view. If a value is passed in, the corresponding callback is unregistered. If no value is passed in, all callbacks associated with the limit change event of the float view are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The float view controller object is null. |

**Examples**

```TypeScript
// Define the callback function for limit changes.
let onLimitsChange = (limits: floatView.FloatViewLimits) => {
  console.info('Float view limitsChange: ' + JSON.stringify(limits));
};
try {
  // Unregister the callback for listening to limit changes of the float view.
  this.floatViewController?.offLimitsChange(onLimitsChange);
} catch (e) {
  console.error(`Failed to off limitsChange float view. Cause:${e.code}, message:${e.message}`);
}
```

## offRectChange

```TypeScript
offRectChange(callback?: Callback<FloatViewRectChangeInfo>): void
```

Unregisters the callback for listening to changes in the rectangular area of the float view.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[FloatViewRectChangeInfo](arkts-arkui-floatview-floatviewrectchangeinfo-i.md)&gt; | No | Callback used to return the rectangle area change information of the current float view. If a value is passed in, the corresponding callback is unregistered. If no value is passed in, all callbacks associated with the rectangle area change event of the float view are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The float view controller object is null. |

**Examples**

```TypeScript
// Define the callback function for rectangular area changes.
let onRectChange = (info: floatView.FloatViewRectChangeInfo) => {
  console.info('Float view rectChange: ' + JSON.stringify(info));
};
try {
  // Unregister the callback for listening to changes in the rectangle area of the float view.
  this.floatViewController?.offRectChange(onRectChange);
} catch (e) {
  console.error(`Failed to off rectChange float view. Cause:${e.code}, message:${e.message}`);
}
```

## offStateChange

```TypeScript
offStateChange(callback?: Callback<FloatViewStateChangeInfo>): void
```

Unregisters the callback for listening to float view state changes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[FloatViewStateChangeInfo](arkts-arkui-floatview-floatviewstatechangeinfo-i.md)&gt; | No | Callback used to return the status change information of the current float view. If a value is passed in, the corresponding callback is unregistered. If no value is passed in, all callbacks associated with the status change event of the float view are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The float view controller object is null. |

**Examples**

```TypeScript
// Define the callback function for status changes.
let onStateChange = (info: floatView.FloatViewStateChangeInfo) => {
  console.info('Float view stateChange: ' + JSON.stringify(info));
};
try {
  // Unregister the callback for listening to float view state changes.
  this.floatViewController?.offStateChange(onStateChange);
} catch (e) {
  console.error(`Failed to off stateChange float view. Cause:${e.code}, message:${e.message}`);
}
```

## onLimitsChange

```TypeScript
onLimitsChange(callback: Callback<FloatViewLimits>): void
```

Registers a callback for listening to limit changes of the float view. When the limit changes, for example, when the device is folded or unfolded, the callback is triggered. To prevent memory leaks, remember to unregister the callback when it is no longer needed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[FloatViewLimits](arkts-arkui-floatview-floatviewlimits-i.md)&gt; | Yes | Callback used to return the limit change information of the current float view. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The float view controller object is null. |
| [1300030](../errorcode-window.md#1300030-repeated-operations-on-the-float-view) | Repeated operations on the float view. Possible cause: The callback has already registered. |

**Examples**

```TypeScript
// Define the callback function for limit changes.
let onLimitsChange = (limits: floatView.FloatViewLimits) => {
  console.info('Float view limitsChange: ' + JSON.stringify(limits));
};
try {
  // Register the callback for listening to limit changes of the float view.
  this.floatViewController?.onLimitsChange(onLimitsChange);
} catch (e) {
  console.error(`Failed to on limitsChange float view. Cause:${e.code}, message:${e.message}`);
}
```

## onRectChange

```TypeScript
onRectChange(callback: Callback<FloatViewRectChangeInfo>): void
```

Registers a callback for listening to changes in the rectangular area (position and size) of the float view. To prevent memory leaks, remember to unregister the callback when it is no longer needed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[FloatViewRectChangeInfo](arkts-arkui-floatview-floatviewrectchangeinfo-i.md)&gt; | Yes | Callback used to return the rectangle area change information of the current float view. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The float view controller object is null. |
| [1300030](../errorcode-window.md#1300030-repeated-operations-on-the-float-view) | Repeated operations on the float view. Possible cause: The callback has already registered. |

**Examples**

```TypeScript
// Define the callback function for rectangular area changes.
let onRectChange = (info: floatView.FloatViewRectChangeInfo) => {
  console.info('Float view rectChange: ' + JSON.stringify(info));
};
try {
  // Register the callback for listening to changes in the rectangle area of the float view.
  this.floatViewController?.onRectChange(onRectChange);
} catch (e) {
  console.error(`Failed to on rectChange float view. Cause:${e.code}, message:${e.message}`);
}
```

## onStateChange

```TypeScript
onStateChange(callback: Callback<FloatViewStateChangeInfo>): void
```

Registers a callback for listening to float view state changes. To prevent memory leaks, remember to unregister the callback when it is no longer needed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[FloatViewStateChangeInfo](arkts-arkui-floatview-floatviewstatechangeinfo-i.md)&gt; | Yes | Callback used to return the status change information of the current float view. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The float view controller object is null. |
| [1300030](../errorcode-window.md#1300030-repeated-operations-on-the-float-view) | Repeated operations on the float view. Possible cause: The callback has already registered. |

**Examples**

```TypeScript
// Define the callback function for status changes.
let onStateChange = (info: floatView.FloatViewStateChangeInfo) => {
  console.info('Float view stateChange: ' + JSON.stringify(info));
};
try {
  // Register the callback for listening to float view state changes.
  this.floatViewController?.onStateChange(onStateChange);
} catch (e) {
  console.error(`Failed to on stateChange float view. Cause:${e.code}, message:${e.message}`);
}
```

## restoreMainWindow

```TypeScript
restoreMainWindow(wantParameters?: Record<string, Object>): Promise<void>
```

Restores the main window of the float view to display in the foreground. If this API is called when the main window is already in the foreground, the main window level will be raised. This API can be used only after the float view is clicked. If the main window is in the **PAUSED** state or in the multitasking state, error code 130 0032 will be returned if this API is called. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| wantParameters | Record&lt;string, Object&gt; | No | Custom parameters passed to the main window when the main window of the float view is restored. The main window will receive the parameters when the onNewWant callback is triggered. The default value is empty, indicating that no custom parameters are passed to the main window. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The float view controller object is null. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: Internal IPC error. |
| [1300031](../errorcode-window.md#1300031-operation-not-supported-in-the-current-float-view-state) | This operation is not supported on the float view in the current state. Possible cause: The float view window is not started when restoring. |
| [1300032](../errorcode-window.md#1300032-failed-to-restore-the-main-window) | Failed to restore the main window. Possible cause: 1. User has never clicked the float view window before restore. 2. The float view window is not in the foreground. 3. The main window is in PAUSED lifecycle state. 4. The main window is in background during recent. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { floatView } from '@kit.ArkUI';

// Define the parameter for restoring the main window.
let param: Record<string, Object> = {
  'info': 'helloworld',
};
// The float view must be in the STARTED state.
try {
  // Restore the main window of the float view to display in the foreground.
  this.floatViewController?.restoreMainWindow(param).then(() => {
    console.info('Succeeded in restoring main window.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to restore main window. Cause:${err.code}, message:${err.message}`);
  });
} catch (e) {
  console.error(`Failed to restore main window. Cause:${e.code}, message:${e.message}`);
}
```

## setFloatViewVisibilityInApp

```TypeScript
setFloatViewVisibilityInApp(isVisible: boolean): Promise<void>
```

Sets whether the float view is visible when the application is running in the foreground. This API uses a promise to return the result.

After the float view is created and before this API is called, the float view is visible by default when the application is running in the foreground.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isVisible | boolean | Yes | Whether the float view is visible when the application is running in the foreground. The value **true** indicates that the window is visible, and **false** indicates the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The float view controller object is null. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: Internal IPC error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { floatView } from '@kit.ArkUI';

try {
  // Set whether the float view is visible when the application is running in the foreground.
  this.floatViewController?.setFloatViewVisibilityInApp(true).then(() => {
    console.info('Succeeded in setting float view visibility in app.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to set float view visibility in app. Cause:${err.code}, message:${err.message}`);
  });
} catch (e) {
  console.error(`Failed to set float view visibility in app. Cause:${e.code}, message:${e.message}`);
}
```

## setUIContext

```TypeScript
setUIContext(path: string, storage?: LocalStorage): Promise<void>
```

Loads the content of a page, with its path specified in the current project, for the float view, and transfers the state attribute to the page through **LocalStorage**. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the page content which needs to be loaded to the window. The path needs to be configured in the **main_pages.json** file of the project. The path cannot be a relative path and must be the same as the value of **src** in the **main_pages.json** file. |
| storage | LocalStorage | No | Page-level UI state storage unit, which is used to transfer the state attribute for the page. By default, the value is empty. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The float view controller object is null. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible causes: Invalid path. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { floatView } from '@kit.ArkUI';

try {
  // Obtain floatViewController using floatView.create(). For details, see the floatView.create() sample.
  // Set the page content path of the float view.
  this.floatViewController?.setUIContext('pages/Index').then(() => {
    console.info('Succeeded in setting UI context.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to set UI context. Cause:${err.code}, message:${err.message}`);
  });
} catch (e) {
  console.error(`Failed to set UI context. Cause:${e.code}, message:${e.message}`);
}
```

## setUIContextByName

```TypeScript
setUIContextByName(name: string, storage?: LocalStorage): Promise<void>
```

Sets the UI content of a [named route](../../../ui/arkts-routing.md#named-route) page to this float view window.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the named route page. |
| storage | LocalStorage | No | The data object shared within the content instance loaded by the window. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The float view controller object is null. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible causes: Invalid name. |

**Examples**

```TypeScript
// Index.ets
import { BusinessError } from '@kit.BasicServicesKit';
import { entryName } from './Hello'; // Import the named route page.
import { floatView } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private floatViewController: floatView.FloatViewController | undefined = undefined;
  // Create a controller.
  // ...
  public setUIContextByName(): void {
    try {
      // Set the page content of the float view based on the named route page.
      this.floatViewController?.setUIContextByName(entryName).then(() => {
        console.info('Succeeded in loading the content.');
      }).catch((err: BusinessError): void => {
        console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
      });
    } catch (e) {
      console.error(`Failed to load the content. Cause code: ${e.code}, message: ${e.message}`);
    }
  }
}
```

```TypeScript
// Hello.ets
export const entryName : string = 'Hello';
@Entry({routeName: entryName, useSharedStorage: true})
@Component
export struct Hello {
  @State message: string = 'Hello World'
  build() {
    Row() {
      Column() {
        Text(this.message)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## setWindowSize

```TypeScript
setWindowSize(size: window.Size): Promise<void>
```

Sets the size of the float view. You are advised to call the [getFloatViewLimits](arkts-arkui-floatview-getfloatviewlimits-f.md) API to obtain the recommended width and height ranges and aspect ratio range, and then call this API based on the recommended values. The actual window size change can be listened to through the [onRectChange](#onrectchange) API. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | [window.Size](arkts-arkui-window-size-i.md) | Yes | Window size. It is recommended that the size meet the limits returned by the [getFloatViewLimits](arkts-arkui-floatview-getfloatviewlimits-f.md) API. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The float view controller object is null. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: Internal IPC error. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: The value of the size is less than or equal to 0. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { floatView, window } from '@kit.ArkUI';

// Set the window size.
let size: window.Size = {
  width: 400,
  height: 600
};
try {
  // Set the size of the float view.
  this.floatViewController?.setWindowSize(size).then(() => {
    console.info('Succeeded in setting window size.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to set window size. Cause:${err.code}, message:${err.message}`);
  });
} catch (e) {
  console.error(`Failed to set window size. Cause:${e.code}, message:${e.message}`);
}
```

## start

```TypeScript
start(): Promise<void>
```

Starts the float view. The return value of this API does not indicate that the start process is complete. You need to use the [onStateChange](#onstatechange) API to listen for the **STARTED** callback to determine whether the start is successful. You are advised to call **start ()** after calling [setUIContext()](#setuicontext). This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.FLOAT_VIEW

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. Possible cause: The application does not have the permission required to call the API. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The float view controller object is null. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: Internal IPC error. |
| [1300030](../errorcode-window.md#1300030-repeated-operations-on-the-float-view) | Repeated operations on the float view. Possible cause: The float view is starting or has already started. |
| [1300031](../errorcode-window.md#1300031-operation-not-supported-in-the-current-float-view-state) | The float view state does not support this operation. Possible cause: The float view is stopping. |
| [1300033](../errorcode-window.md#1300033-failed-to-start-the-float-view) | Failed to start float view. Possible causes: 1. Start multiple float views. 2. The main window of context is not foreground. |
| [1300034](../errorcode-window.md#1300034-operation-of-the-float-view-conflicts-with-those-of-other-floating-windows) | This operation conflicts with other floating windows. Possible cause: App has already started floating ball or pip window. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { floatView } from '@kit.ArkUI';

try {
  // Start the float view.
  this.floatViewController?.start().then(() => {
    console.info('Succeeded in starting float view.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to start float view. Cause:${err.code}, message:${err.message}`);
  });
} catch (e) {
  console.error(`Failed to start float view. Cause:${e.code}, message:${e.message}`);
}
```

## stop

```TypeScript
stop(): Promise<void>
```

Stops the float view. The return value of this API does not indicate that the stop process is complete. You need to use the [onStateChange](#onstatechange) API to listen for the **STOPPED** callback to determine whether the stop is successful. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The float view controller object is null. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: Internal IPC error. |
| [1300030](../errorcode-window.md#1300030-repeated-operations-on-the-float-view) | Repeated operations on the float view. Possible cause: The float view is stopping or has already stopped. |
| [1300031](../errorcode-window.md#1300031-operation-not-supported-in-the-current-float-view-state) | This operation is not supported on the float view in the current state. Possible cause: The float view window is not started. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { floatView } from '@kit.ArkUI';

try {
  // Stop the float view.
  this.floatViewController?.stop().then(() => {
    console.info('Succeeded in stopping float view.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to stop float view. Cause:${err.code}, message:${err.message}`);
  });
} catch (e) {
  console.error(`Failed to stop float view. Cause:${e.code}, message:${e.message}`);
}
```

## switchTemplate

```TypeScript
switchTemplate(templateProperty: TemplateProperty): Promise<void>
```

Switches the template of the flow view and changes the window size. You are advised to call the [getFloatViewLimits](arkts-arkui-floatview-getfloatviewlimits-f.md) API to obtain the recommended width and height ranges and aspect ratio range of the target template, and then call this API based on the recommended values. The actual window size change can be listened to through the [onRectChange](#onrectchange) API. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| templateProperty | [TemplateProperty](arkts-arkui-floatview-templateproperty-i.md) | Yes | Target flow view template and window size. It is recommended that the size meet the limits returned by the [getFloatViewLimits](arkts-arkui-floatview-getfloatviewlimits-f.md) API. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The float view controller object is null. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: Internal IPC error. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: 1. Invalid template type. 2. The value of the size is less than or equal to 0. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { floatView, window } from '@kit.ArkUI';

// Set the size of the new window.
let newSize: window.Size = {
  width: 800,
  height: 100
};
// Set the template property.
let templateProperty: floatView.TemplateProperty = {
  templateType: floatView.FloatViewTemplateType.HORIZONTAL_BAR,
  size: newSize
};
try {
  // Switch the template of the float view and change the window size.
  this.floatViewController?.switchTemplate(templateProperty).then(() => {
    console.info('Succeeded in switching window type and size.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to switch window type and size. Cause:${err.code}, message:${err.message}`);
  });
} catch (e) {
  console.error(`Failed to switch window type and size. Cause:${e.code}, message:${e.message}`);
}
```
