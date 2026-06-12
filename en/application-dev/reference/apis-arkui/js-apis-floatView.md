# @ohos.window.floatView (Float View)
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @betafringe007-->
<!--Designer: @zhoulin_-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

A float view is a small window that floats on a desktop or an application screen, providing flexible window management capabilities.

This module provides capabilities about the float view, including determining whether a device supports a float view, and creating a float view controller to start, update, or stop a float view.

**Application scenarios**:

A float view is applicable to scenarios where application content needs to be continuously displayed in an independent small window or shortcut operations need to be provided. Examples:
- Application for stock market tracking: When browsing other applications, users can use a float view to view real-time stock market changes without frequently switching between applications.
- Live streaming application on a mobile phone: During live streaming, hosts can use a float view to display a custom interaction panel or control UI, facilitating real-time operations and interactions.

**Linkage with the floating ball**:

This module can be used together with [@ohos.window.floatingBall](js-apis-floatingBall.md). After the float view controller is bound to the floating ball controller using the [floatView.bind](#floatviewbind) API, users can tap the floating ball to expand it as a float view, and click the minimize button in the upper left corner of the float view to collapse it back as a floating ball. This allows for seamless switching between the two window forms.

**Comparison between the global floating window and float view**:

- Similarities: Both the global floating window and float view are special types of application auxiliary windows that can remain displayed on the foreground even after the application's main window and corresponding ability transition to the background. They can be used to continue displaying the UI after the application transitions to the background.
- Differences:
  - The global floating window is managed and its UI is drawn by developers, without a unified UI or animation effect.
  - The float view is managed by the system and its UI is drawn in a unified manner, offering a more sophisticated and refined animation effect.
  - The float view can be bound to the [floating ball](js-apis-floatingBall.md) for joint use, enabling more complex scenarios.

**Since**: 26.0.0

> **NOTE**
>
> - Use [canIUse()](../common/js-apis-syscap.md#caniuse) to check whether the device supports the system capability SystemCapability.Window.SessionManager and the corresponding APIs.
>
> - The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { floatView } from '@kit.ArkUI';
```

## floatView.isFloatViewEnabled

isFloatViewEnabled(): boolean

Checks whether the device supports the float view.

**Since**: 26.0.0

**System capability**: SystemCapability.Window.SessionManager

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type| Description|
|------------|------------|
| boolean  | Whether the device supports the float view. **true** to support; **false** otherwise.|

**Example**

```ts
let enable: boolean = floatView.isFloatViewEnabled();
console.info('Float view enabled is: ' + enable);
```

## floatView.create

create(config: FloatViewConfiguration): Promise&lt;FloatViewController&gt;

Creates a float view controller. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

**Parameters**

| Name| Type| Mandatory| Description|
|------------|------------|------------|------------|
| config | [FloatViewConfiguration](#floatviewconfiguration) | Yes| Parameter for creating a float view controller. This parameter and the context for constructing this parameter cannot be null or undefined. Otherwise, error code 401 is thrown. Error code 1300016 is thrown for other parameter exceptions.|

**Return value**

| Type| Description|
|------------|------------|
| Promise&lt;[FloatViewController](#floatviewcontroller)&gt; | Promise used to return the created float view controller.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Window Error Codes](errorcode-window.md).

| ID| Error Message|
|------------|------------|
| 801 | Capability not supported. Possible cause: Call the API on unsupported device. |
| 1300002 | This window state is abnormal. Possible cause: 1. This window context is abnormal. 2. System error, such as a null pointer, insufficient memory or a JS engine exception. |
| 1300016 | Parameter error. Possible cause: Invalid template type. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  private floatViewController: floatView.FloatViewController | undefined = undefined;
  aboutToAppear(): void {
    // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
    let ctx = this.getUIContext().getHostContext() as common.UIAbilityContext;
    let config: floatView.FloatViewConfiguration = {
      context: ctx,
      templateType: floatView.FloatViewTemplateType.ROUNDED_RECTANGLE
    };
    try {
      floatView.create(config).then((data: floatView.FloatViewController) => {
        this.floatViewController = data;
        console.info(`Succeeded in creating float view controller. Data: ${data}`);
      }).catch((err: BusinessError): void => {
        console.error(`Failed to create float view controller. Cause:${err.code}, message:${err.message}`);
      });
    } catch(e) {
      console.error(`Failed to create float view controller. Cause:${e.code}, message:${e.message}`);
    }
  }
}
```

## floatView.bind

bind(floatViewController: FloatViewController, floatingBallController: floatingBall.FloatingBallController, floatingBallParams: floatingBall.FloatingBallParams): Promise&lt;void&gt;

Binds the float view and floating ball. You need to create the [float view controller](#floatviewcontroller) and [floating ball controller](js-apis-floatingBall.md#floatingballcontroller) first, and neither of them has been started. This API uses a promise to return the result.

> **NOTE**
>
> - After the binding is successful, calling [start()](#start) or [startFloatingBall()](js-apis-floatingBall.md#startfloatingball) will create both a float view and the floating ball window, and trigger the status callback registered for the corresponding window. However, only one window is displayed at a time, and the display sequence depends on which controller's start API is called first.
> - After the binding is successful, users can switch between the float view and the floating ball window by clicking.
> - After the binding is successful, calling the stop API ([stop()](#stop) or [stopFloatingBall()](js-apis-floatingBall.md#stopfloatingball)) of either controller will destroy both the float view and the floating ball window, and trigger the status callback registered for the corresponding window.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Required permissions**: ohos.permission.USE_FLOAT_BALL and ohos.permission.FLOAT_VIEW

**System capability**: SystemCapability.Window.SessionManager

**Parameters**

| Name| Type| Mandatory| Description|
|------------|------------|------------|------------|
| floatViewController | [FloatViewController](#floatviewcontroller) | Yes| Float view controller.|
| floatingBallController | [floatingBall.FloatingBallController](js-apis-floatingBall.md#floatingballcontroller) | Yes| Floating ball controller.|
| floatingBallParams | [floatingBall.FloatingBallParams](js-apis-floatingBall.md#floatingballparams) | Yes| Floating ball parameters. The parameters set during binding will overwrite the parameters saved when the floating ball controller is started.|

**Return value**

| Type| Description|
|------------|------------|
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Window Error Codes](errorcode-window.md).

| ID| Error Message|
|------------|------------|
| 201 | Permission verification failed. Possible cause: The application does not have the permission required to call the API. |
| 801 | Capability not supported on this device. Possible cause: Call api on unsupported device. |
| 1300019 | Wrong parameters for operating the floating ball. Possible cause: Invalid floating ball params. |
| 1300025 | The floating ball state does not support this operation. Possible cause: 1. The floating ball has started but not stopped yet. 2. The floating ball controller has been bound. |
| 1300031 | The floatView state does not support this operation. Possible cause: 1. The float view has started but not stopped yet. 2. The float view controller has been bound. |

**Example**

```ts
// Entry.ets
import { BusinessError } from '@kit.BasicServicesKit';
import { floatingBall } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private floatingBallController: floatingBall.FloatingBallController | undefined = undefined;
  private floatViewController: floatView.FloatViewController | undefined = undefined;
  // Create a controller.
  // ...
  public bindController(): void {
    let floatingBallParams: floatingBall.FloatingBallParams = {
      template: floatingBall.FloatingBallTemplate.EMPHATIC,
      title: 'title',
      content: 'content'
    };

    try {
      if (this.floatViewController && this.floatingBallController) {
        floatView.bind(this.floatViewController!, this.floatingBallController!, floatingBallParams).then(() => {
          console.info('Succeeded in binding float view and floating ball.');
        }).catch((err: BusinessError): void => {
          console.error(`Failed to bind float view and floating ball. Cause:${err.code}, message:${err.message}`);
        });
      }
    } catch(e) {
      console.error(`Failed to bind float view and floating ball. Cause:${e.code}, message:${e.message}`);
    }
  }
}
```

## floatView.unbind

unbind(floatViewController: FloatViewController, floatingBallController: floatingBall.FloatingBallController): Promise&lt;void&gt;

Unbinds the float view and floating ball. The unbinding can be performed only after both the [float view controller](#floatviewcontroller) and [floating ball controller](js-apis-floatingBall.md#floatingballcontroller) are stopped. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

**Parameters**

| Name| Type| Mandatory| Description|
|------------|------------|------------|------------|
| floatViewController | [FloatViewController](#floatviewcontroller) | Yes| Float view controller.|
| floatingBallController | [floatingBall.FloatingBallController](js-apis-floatingBall.md#floatingballcontroller) | Yes| Floating ball controller.|

**Return value**

| Type| Description|
|------------|------------|
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Window Error Codes](errorcode-window.md).

| ID| Error Message|
|------------|------------|
| 801 | Capability not supported on this device. Possible cause: Call api on unsupported device. |
| 1300025 | The floating ball state does not support this operation. Possible cause: 1. The floating ball has started but not stopped yet. 2. The floatingBallController has not been bound. |
| 1300031 | The floatView state does not support this operation. Possible cause: 1. The float view has started but not stopped yet. 2. The floatViewController has not been bound. 3. The floatViewController and the floatingBallController are not bound together. |

**Example**

```ts
// Entry.ets
import { BusinessError } from '@kit.BasicServicesKit';
import { floatingBall } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private floatingBallController: floatingBall.FloatingBallController | undefined = undefined;
  private floatViewController: floatView.FloatViewController | undefined = undefined;
  // Create a controller.
  // ...
  public unbindController(): void {
    try {
      // Use the float view controller and floating ball controller passed during the binding.
      if (this.floatViewController && this.floatingBallController) {
        floatView.unbind(this.floatViewController!, this.floatingBallController!).then(() => {
          console.info('Succeeded in unbinding float view and floating ball.');
        }).catch((err: BusinessError): void => {
          console.error(`Failed to unbind float view and floating ball. Cause:${err.code}, message:${err.message}`);
        });
      }
    } catch(e) {
      console.error(`Failed to unbind float view and floating ball. Cause:${e.code}, message:${e.message}`);
    }
  }
}
```

## floatView.getFloatViewLimits

getFloatViewLimits(templateType: FloatViewTemplateType): FloatViewLimits

Obtains the limits of the float view based on the passed template type. The unit is px.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

**Parameters**

| Name| Type| Mandatory| Description|
|------------|------------|------------|------------|
| templateType | [FloatViewTemplateType](#floatviewtemplatetype) | Yes| Template type of the float view.|

**Return value**

| Type| Description|
|------------|------------|
| [FloatViewLimits](#floatviewlimits) | Limits of the float view, including the maximum size, minimum size, and aspect ratio.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Window Error Codes](errorcode-window.md).

| ID| Error Message|
|------------|------------|
| 801 | Capability not supported. Possible cause: Call the API on unsupported device. |
| 1300002 | This window state is abnormal. Possible cause: System error, such as a null pointer, insufficient memory or a JS engine exception. |
| 1300003 | This window manager service works abnormally. Possible cause: Internal IPC error. |
| 1300016 | Parameter error. Possible cause: Invalid template type. |

**Example**

```ts
let limits: floatView.FloatViewLimits = floatView.getFloatViewLimits(floatView.FloatViewTemplateType.ROUNDED_RECTANGLE);
console.info('Float view limits: ' + JSON.stringify(limits));
```

## FloatViewConfiguration

Provides parameter configuration required for creating a float view controller.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

| Name| Type| Read-Only| Optional| Description|
|------------|------------|------------|------------|------------|
| context | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | No| No| Context environment.|
| templateType | [FloatViewTemplateType](#floatviewtemplatetype) | No| No| Template type of the float view.|

## TemplateProperty

Provides parameter configuration required for switching the float view template and modifying the size of the window.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

| Name| Type| Read-Only| Optional| Description|
|------------|------------|------------|------------|------------|
| templateType | [FloatViewTemplateType](#floatviewtemplatetype) | No| No| Template type of the float view.|
| size | [window.Size](arkts-apis-window-i.md#size7) | No| No| Window size required for updating the template type.|

## FloatViewController

Defines a float view controller instance, which is used to start and stop the float view and register callbacks.

Before calling the following APIs, you must use [floatView.create()](#floatviewcreate) to create a float view controller instance (that is, **floatViewController**).

**Model restriction**: This API can be used only in the stage model.

### setUIContext

setUIContext(path: string, storage?: LocalStorage): Promise&lt;void&gt;

Loads the content of a page, with its path specified in the current project, for the float view, and transfers the state attribute to the page through **LocalStorage**. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

**Parameters**

| Name| Type| Mandatory| Description|
|------------|------------|------------|------------|
| path | string | Yes| Path of the page content which needs to be loaded to the window. The path needs to be configured in the **main_pages.json** file of the project. The path cannot be a relative path and must be the same as the value of **src** in the **main_pages.json** file.|
| storage | [LocalStorage](../../ui/state-management/arkts-localstorage.md) | No| Page-level UI state storage unit, which is used to transfer the state attribute for the page. By default, the value is empty.|

**Return value**

| Type| Description|
|------------|------------|
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Window Error Codes](errorcode-window.md).

| ID| Error Message|
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |
| 1300016 | Parameter error. Possible causes: Invalid path. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  this.floatViewController?.setUIContext('pages/Index').then(() => {
    console.info('Succeeded in setting UI context.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to set UI context. Cause:${err.code}, message:${err.message}`);
  });
} catch(e) {
  console.error(`Failed to set UI context. Cause:${e.code}, message:${e.message}`);
}
```

### setUIContextByName

setUIContextByName(name: string, storage?: LocalStorage): Promise&lt;void&gt;

Loads the content of a [named route](../../ui/arkts-routing.md#named-route) page to this window, and transfers the state attribute to the page through a local storage. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

**Parameters**

| Name| Type| Mandatory| Description|
|------------|------------|------------|------------|
| name | string | Yes| Name of the named route page.|
| storage | [LocalStorage](../../ui/state-management/arkts-localstorage.md) | No| Page-level UI state storage unit, which is used to transfer the state attribute for the page. By default, the value is empty.|

**Return value**

| Type| Description|
|------------|------------|
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Window Error Codes](errorcode-window.md).

| ID| Error Message|
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |
| 1300016 | Parameter error. Possible causes: Invalid name. |

**Example**

<!--code_no_check-->
```ts
// Index.ets
import { BusinessError } from '@kit.BasicServicesKit';
import { entryName } from './Hello'; // Import the named route page.

@Entry
@Component
struct Index {
  private floatViewController: floatView.FloatViewController | undefined = undefined;
  // Create a controller.
  // ...
  public setUIContextByName(): void {
    try {
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
<!--code_no_check-->
```ts
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

### setWindowSize

setWindowSize(size: window.Size): Promise&lt;void&gt;

Sets the size of the float view. You are advised to call the [getFloatViewLimits](#floatviewgetfloatviewlimits) API to obtain the recommended width and height ranges and aspect ratio range, and then call this API based on the recommended values. The actual window size change can be listened to through the [onRectChange](#onrectchange) API. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

**Parameters**

| Name| Type| Mandatory| Description|
|------------|------------|------------|------------|
| size | [window.Size](arkts-apis-window-i.md#size7) | Yes| Window size. It is recommended that the size meet the limits returned by the [getFloatViewLimits](#floatviewgetfloatviewlimits) API.|

**Return value**

| Type| Description|
|------------|------------|
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Window Error Codes](errorcode-window.md).

| ID| Error Message|
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |
| 1300003 | This window manager service works abnormally. Possible cause: Internal IPC error. |
| 1300016 | Parameter error. Possible cause: The value of the size is less than or equal to 0. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

let size: window.Size = {
  width: 400,
  height: 600
};
try {
  this.floatViewController?.setWindowSize(size).then(() => {
    console.info('Succeeded in setting window size.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to set window size. Cause:${err.code}, message:${err.message}`);
  });
} catch(e) {
  console.error(`Failed to set window size. Cause:${e.code}, message:${e.message}`);
}
```

### switchTemplate

switchTemplate(templateProperty: TemplateProperty): Promise&lt;void&gt;

Switches the template of the flow view and changes the window size. You are advised to call the [getFloatViewLimits](#floatviewgetfloatviewlimits) API to obtain the recommended width and height ranges and aspect ratio range of the target template type, and then call this API based on the recommended values. The actual window size change can be listened to through the [onRectChange](#onrectchange) API. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

**Parameters**

| Name| Type| Mandatory| Description|
|------------|------------|------------|------------|
| templateProperty | [TemplateProperty](#templateproperty) | Yes| Target flow view template and window size. It is recommended that the size meet the limits returned by the [getFloatViewLimits](#floatviewgetfloatviewlimits) API.|

**Return value**

| Type| Description|
|------------|------------|
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Window Error Codes](errorcode-window.md).

| ID| Error Message|
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |
| 1300003 | This window manager service works abnormally. Possible cause: Internal IPC error. |
| 1300016 | Parameter error. Possible cause: 1. Invalid template type. 2. The value of the size is less than or equal to 0. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

let newSize: window.Size = {
  width: 800,
  height: 100
};
let templateProperty: floatView.TemplateProperty = {
  templateType: floatView.FloatViewTemplateType.HORIZONTAL_BAR,
  size: newSize,
}
try {
  this.floatViewController?.switchTemplate(templateProperty).then(() => {
    console.info('Succeeded in switching window type and size.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to switch window type and size. Cause:${err.code}, message:${err.message}`);
  });
} catch(e) {
  console.error(`Failed to switch window type and size. Cause:${e.code}, message:${e.message}`);
}
```

### start

start(): Promise&lt;void&gt;

Starts the float view. The return value of this API does not indicate that the start process is complete. You need to use the [onStateChange](#onstatechange) API to listen for the **STARTED** callback to determine whether the start is successful. You are advised to call this API after calling [setUIContext()](#setuicontext) or [setUIContextByName()](#setuicontextbyname). This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Required permission**: ohos.permission.FLOAT_VIEW

**System capability**: SystemCapability.Window.SessionManager

**Return value**

| Type| Description|
|------------|------------|
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Window Error Codes](errorcode-window.md).

| ID| Error Message|
|------------|------------|
| 201 | Permission verification failed. Possible cause: The application does not have the permission required to call the API. |
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |
| 1300003 | This window manager service works abnormally. Possible cause: Internal IPC error. |
| 1300030 | Repeated operations on the float view. Possible cause: The float view is starting or has already started. |
| 1300031 | The float view state does not support this operation. Possible cause: The float view is stopping. |
| 1300033 | Failed to start float view. Possible causes: 1. Start multiple float views. 2. The main window of context is not foreground. |
| 1300034 | This operation conflicts with other floating windows. Possible cause: App has already started floating ball or pip window. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  this.floatViewController?.start().then(() => {
    console.info('Succeeded in starting float view.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to start float view. Cause:${err.code}, message:${err.message}`);
  });
} catch(e) {
  console.error(`Failed to start float view. Cause:${e.code}, message:${e.message}`);
}
```

### stop

stop(): Promise&lt;void&gt;

Stops the float view. The return value of this API does not indicate that the stop process is complete. You need to use the [onStateChange](#onstatechange) API to listen for the **STOPPED** callback to determine whether the stop is successful. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

**Return value**

| Type| Description|
|------------|------------|
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Window Error Codes](errorcode-window.md).

| ID| Error Message|
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |
| 1300003 | This window manager service works abnormally. Possible cause: Internal IPC error. |
| 1300030 | Repeated operations on the float view. Possible cause: The float view is stopping or has already stopped. |
| 1300031 | This operation is not supported on the float view in the current state. Possible cause: The float view window is not started. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  this.floatViewController?.stop().then(() => {
    console.info('Succeeded in stopping float view.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to stop float view. Cause:${err.code}, message:${err.message}`);
  });
} catch(e) {
  console.error(`Failed to stop float view. Cause:${e.code}, message:${e.message}`);
}
```

### setFloatViewVisibilityInApp

setFloatViewVisibilityInApp(isVisible: boolean): Promise&lt;void&gt;

Sets whether the float view is visible when the application is running in the foreground. This API uses a promise to return the result.

After the float view is created and before this API is called, the float view is visible by default when the application is running in the foreground.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

**Parameters**

| Name| Type| Mandatory| Description|
|------------|------------|------------|------------|
| isVisible | boolean | Yes| Whether the float view is visible when the application is running in the foreground. The value **true** indicates that the window is visible, and **false** indicates the opposite.|

**Return value**

| Type| Description|
|------------|------------|
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Window Error Codes](errorcode-window.md).

| ID| Error Message|
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |
| 1300003 | This window manager service works abnormally. Possible cause: Internal IPC error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  this.floatViewController?.setFloatViewVisibilityInApp(true).then(() => {
    console.info('Succeeded in setting float view visibility in app.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to set float view visibility in app. Cause:${err.code}, message:${err.message}`);
  });
} catch(e) {
  console.error(`Failed to set float view visibility in app. Cause:${e.code}, message:${e.message}`);
}
```

### restoreMainWindow

restoreMainWindow(wantParameters?: Record&lt;string, Object&gt;): Promise&lt;void&gt;

Restores the main window of the float view to display in the foreground. If this API is called when the main window is already in the foreground, the main window level will be raised. This API can be used only after the float view is clicked. If the main window is in the **PAUSED** state or in the multitasking state, error code 1300032 will be returned if this API is called. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

**Parameters**

| Name| Type| Mandatory| Description|
|------------|------------|------------|------------|
| wantParameters | Record&lt;string, Object&gt; | No| Custom parameters passed to the main window when the main window of the float view is restored. The main window will receive the parameters when the [onNewWant](../apis-ability-kit/js-apis-app-ability-abilityLifecycleCallback.md#onnewwant12) callback is triggered. The default value is empty, indicating that no custom parameters are passed to the main window.|

**Return value**

| Type| Description|
|------------|------------|
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Window Error Codes](errorcode-window.md).

| ID| Error Message|
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |
| 1300003 | This window manager service works abnormally. Possible cause: Internal IPC error. |
| 1300031 | This operation is not supported on the float view in the current state. Possible cause: The float view window is not started when restoring. |
| 1300032 | Failed to restore the main window. Possible cause: 1. User has never clicked the float view window before restore. 2. The float view window is not in the foreground. 3. The main window is in PAUSED lifecycle state. 4. The main window is in background during recent. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let param: Record<string, Object> = {
  "info": "helloworld",
};
// The float view must be in the STARTED state.
try {
  this.floatViewController?.restoreMainWindow(param).then(() => {
    console.info('Succeeded in restoring main window.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to restore main window. Cause:${err.code}, message:${err.message}`);
  });
} catch(e) {
  console.error(`Failed to restore main window. Cause:${e.code}, message:${e.message}`);
}
```

### getWindowProperties

getWindowProperties(): FloatViewProperties

Obtains the properties of the float view.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

**Return value**

| Type| Description|
|------------|------------|
| [FloatViewProperties](#floatviewproperties) | Properties of the float view.|

**Error codes**

For details about the error codes, see [Window Error Codes](errorcode-window.md).

| ID| Error Message|
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |
| 1300031 | This operation is not supported on the float view in the current state. Possible cause: The float view window has not started, has stopped, or is in an error state. |

**Example**

```ts
try {
  let properties: floatView.FloatViewProperties | undefined = this.floatViewController?.getWindowProperties();
  console.info('Float view properties: ' + JSON.stringify(properties));
} catch(e) {
  console.error(`Failed to get window properties. Cause:${e.code}, message:${e.message}`);
}
```

### onStateChange

onStateChange(callback: Callback&lt;FloatViewStateChangeInfo&gt;): void

Registers a callback for listening to float view state changes. To prevent memory leaks, remember to unregister the callback when it is no longer needed.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

**Parameters**

| Name| Type| Mandatory| Description|
|------------|------------|------------|------------|
| callback | Callback&lt;[FloatViewStateChangeInfo](#floatviewstatechangeinfo)&gt; | Yes| Callback used to return the status change information of the current float view.|

**Error codes**

For details about the error codes, see [Window Error Codes](errorcode-window.md).

| ID| Error Message|
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |
| 1300030 | Repeated operations on the float view. Possible cause: The callback has already registered. |

**Example**

```ts
let onStateChange = (info: floatView.FloatViewStateChangeInfo) => {
  console.info('Float view stateChange: ' + JSON.stringify(info));
};
try {
  this.floatViewController?.onStateChange(onStateChange);
} catch(e) {
  console.error(`Failed to on stateChange float view. Cause:${e.code}, message:${e.message}`);
}
```

### offStateChange

offStateChange(callback?: Callback&lt;FloatViewStateChangeInfo&gt;): void

Unregisters the callback for listening to float view state changes.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

**Parameters**

| Name| Type| Mandatory| Description|
|------------|------------|------------|------------|
| callback | Callback&lt;[FloatViewStateChangeInfo](#floatviewstatechangeinfo)&gt; | No| Callback used to return the status change information of the current float view. If a value is passed in, the corresponding callback is unregistered. If no value is passed in, all callbacks associated with the status change event of the float view are unregistered.|

**Error codes**

For details about the error codes, see [Window Error Codes](errorcode-window.md).

| ID| Error Message|
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |

**Example**

```ts
let onStateChange = (info: floatView.FloatViewStateChangeInfo) => {
  console.info('Float view stateChange: ' + JSON.stringify(info));
};
try {
  this.floatViewController?.offStateChange(onStateChange);
} catch(e) {
  console.error(`Failed to off stateChange float view. Cause:${e.code}, message:${e.message}`);
}
```

### onRectChange

onRectChange(callback: Callback&lt;FloatViewRectChangeInfo&gt;): void

Registers a callback for listening to changes in the rectangular area (position and size) of the float view. To prevent memory leaks, remember to unregister the callback when it is no longer needed.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

**Parameters**

| Name| Type| Mandatory| Description|
|------------|------------|------------|------------|
| callback | Callback&lt;[FloatViewRectChangeInfo](#floatviewrectchangeinfo)&gt; | Yes| Callback used to return the rectangle area change information of the current float view.|

**Error codes**

For details about the error codes, see [Window Error Codes](errorcode-window.md).

| ID| Error Message|
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |
| 1300030 | Repeated operations on the float view. Possible cause: The callback has already registered. |

**Example**

```ts
let onRectChange = (info: floatView.FloatViewRectChangeInfo) => {
  console.info('Float view rectChange: ' + JSON.stringify(info));
};
try {
  this.floatViewController?.onRectChange(onRectChange);
} catch(e) {
  console.error(`Failed to on rectChange float view. Cause:${e.code}, message:${e.message}`);
}
```

### offRectChange

offRectChange(callback?: Callback&lt;FloatViewRectChangeInfo&gt;): void

Unregisters the callback for listening to changes in the rectangular area of the float view.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

**Parameters**

| Name| Type| Mandatory| Description|
|------------|------------|------------|------------|
| callback | Callback&lt;[FloatViewRectChangeInfo](#floatviewrectchangeinfo)&gt; | No| Callback used to return the rectangle area change information of the current float view. If a value is passed in, the corresponding callback is unregistered. If no value is passed in, all callbacks associated with the rectangle area change event of the float view are unregistered.|

**Error codes**

For details about the error codes, see [Window Error Codes](errorcode-window.md).

| ID| Error Message|
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |

**Example**

```ts
let onRectChange = (info: floatView.FloatViewRectChangeInfo) => {
  console.info('Float view rectChange: ' + JSON.stringify(info));
};
try {
  this.floatViewController?.offRectChange(onRectChange);
} catch(e) {
  console.error(`Failed to off rectChange float view. Cause:${e.code}, message:${e.message}`);
}
```

### onLimitsChange

onLimitsChange(callback: Callback&lt;FloatViewLimits&gt;): void

Registers a callback for listening to limit changes of the float view. When the limit changes, for example, when the device is folded or unfolded, the callback is triggered. To prevent memory leaks, remember to unregister the callback when it is no longer needed.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

**Parameters**

| Name| Type| Mandatory| Description|
|------------|------------|------------|------------|
| callback | Callback&lt;[FloatViewLimits](#floatviewlimits)&gt; | Yes| Callback used to return the limit change information of the current float view.|

**Error codes**

For details about the error codes, see [Window Error Codes](errorcode-window.md).

| ID| Error Message|
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |
| 1300030 | Repeated operations on the float view. Possible cause: The callback has already registered. |

**Example**

```ts
let onLimitsChange = (limits: floatView.FloatViewLimits) => {
  console.info('Float view limitsChange: ' + JSON.stringify(limits));
};
try {
  this.floatViewController?.onLimitsChange(onLimitsChange);
} catch(e) {
  console.error(`Failed to on limitsChange float view. Cause:${e.code}, message:${e.message}`);
}
```

### offLimitsChange

offLimitsChange(callback?: Callback&lt;FloatViewLimits&gt;): void

Unregisters the callback for listening to limit changes of the float view.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

**Parameters**

| Name| Type| Mandatory| Description|
|------------|------------|------------|------------|
| callback | Callback&lt;[FloatViewLimits](#floatviewlimits)&gt; | No| Callback used to return the limit change information of the current float view. If a value is passed in, the corresponding callback is unregistered. If no value is passed in, all callbacks associated with the limit change event of the float view are unregistered.|

**Error codes**

For details about the error codes, see [Window Error Codes](errorcode-window.md).

| ID| Error Message|
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |

**Example**

```ts
let onLimitsChange = (limits: floatView.FloatViewLimits) => {
  console.info('Float view limitsChange: ' + JSON.stringify(limits));
};
try {
  this.floatViewController?.offLimitsChange(onLimitsChange);
} catch(e) {
  console.error(`Failed to off limitsChange float view. Cause:${e.code}, message:${e.message}`);
}
```

## FloatViewTemplateType

Enumerates the template types of the float view.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

| Name| Value| Description|
|------------|------------|------------|
| ROUNDED_RECTANGLE | 0 | Rectangle with rounded corners.|
| HORIZONTAL_BAR | 1 | Horizontal bar rectangle.|

## FloatViewProperties

Provides the properties of the float view.

**Since**: 26.0.0

**System capability**: SystemCapability.Window.SessionManager

**Model restriction**: This API can be used only in the stage model.

| Name| Type| Read-Only| Optional| Description|
|------------|------------|------------|------------|------------|
| templateType | [FloatViewTemplateType](#floatviewtemplatetype) | No| No| Template type of the float view.|
| windowId | number | No| No| Float view ID.|
| displayId | number | No| No| ID of the display where the float view is located.|
| windowRect | [window.Rect](arkts-apis-window-i.md#rect7) | No| No| Rectangle area of the float view.|
| windowScale | number | No| No| Scale factor of the float view.|
| avoidArea | [window.AvoidArea](arkts-apis-window-i.md#avoidarea7) | No| No| Avoid area for the content of the float view.<br>Note:<br>On the page loaded by [setUIContext()](#setuicontext) or [setUIContextByName()](#setuicontextbyname), components in the avoid area do not respond to gesture events. When adding components that require gesture response events, avoid the area.|
| inSidebar | boolean | No| No| Whether the float view is in the sidebar. **true**: in the sidebar; **false**: not in the sidebar.|

## RatioLimit

Provides the aspect ratio range of the float view. The aspect ratio is obtained by dividing the width of the rectangular area of the window by its height.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

| Name| Type| Read-Only| Optional| Description|
|------------|------------|------------|------------|------------|
| minRatio | number | No| No| Minimum aspect ratio of the float view.|
| maxRatio | number | No| No| Maximum aspect ratio of the float view.|

## FloatViewLimits

Provides the limits of the float view.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

| Name| Type| Read-Only| Optional| Description|
|------------|------------|------------|------------|------------|
| minSize | [window.Size](arkts-apis-window-i.md#size7) | No| No| Minimum size of the float view.|
| maxSize | [window.Size](arkts-apis-window-i.md#size7) | No| No| Maximum size of the float view.|
| ratioLimits | Array&lt;[RatioLimit](#ratiolimit)&gt; | No| No| Aspect ratio range of the float view.|

## FloatViewStateChangeInfo

Provides the state change information of the float view.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

| Name| Type| Read-Only| Optional| Description|
|------------|------------|------------|------------|------------|
| state | [FloatViewState](#floatviewstate) | No| No| State of the float view.|
| stopReason | string | No| No| Reason why the float view stops. This parameter is valid only when **state** is set to **FloatViewState.STOPPED**. In other states, this parameter is an empty string by default. The stop reasons and their meanings are as follows:<br>**"APP_STOP"**: The application proactively stops the float view.<br>**"STOP_IN_SIDEBAR"**: The float view is closed in the sidebar.<br>**"TITLE_BAR_STOP_CLICK"**: The float view is closed by clicking the close button on the title bar.<br>**"DUMPSTER_STOP"**: The float view is dragged to the trash can.<br>**"REPLACE_STOP"**: The float view is occupied by another float view.<br>**"FLOATING_BALL_STOP"**: The float view stops when the bound floating ball stops.<br> **"MAIN_WINDOW_DESTROY_STOP"**: The float view stops after the main window associated with the context is destroyed.|

## FloatViewState

Enumerates the states of the float view.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

| Name| Value| Description|
|------------|------------|------------|
| STARTED | 1 | The float view has been started and displayed.|
| HIDDEN | 2 | The float view has been hidden. This event is triggered when the user swipes up to enter the multitasking screen or when the [setFloatViewVisibilityInApp](#setfloatviewvisibilityinapp) API is called to hide the float view when the application is in the foreground and the application is in the foreground.|
| STOPPED | 3 | The float view has been stopped.|
| IN_SIDEBAR | 4 | The float view is in the sidebar.|
| IN_FLOATING_BALL | 5 | The float view is switched to the floating ball.|
| ERROR | 6 | An exception occurs in the float view.|

## FloatViewRectChangeInfo

Provides the rectangle area change information of the float view.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

| Name| Type| Read-Only| Optional| Description|
|------------|------------|------------|------------|------------|
| windowRect | [window.Rect](arkts-apis-window-i.md#rect7) | No| No| Rectangle area of the float view.|
| windowScale | number | No| No| Scale factor of the float view.|
| reason | string | No| No| Reason for the change of the rectangle area of the float view. The reasons and their meanings are as follows:<br>**"POSITION_CHANGE"**: The position changes.<br>**"SIZE_CHANGE"**: The size changes.<br>**"RECT_CHANGE"**: Both the position and size change.|
