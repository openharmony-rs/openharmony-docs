# FloatingBallController

```TypeScript
interface FloatingBallController
```

Implements a floating ball controller instance, which is used to start, update, and stop floating balls, and register callbacks.

Before calling any of the following APIs, you must use [floatingBall.create()](arkts-arkui-floatingball-create-f.md) to create a floating ball controller instance.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { floatingBall } from '@kit.ArkUI';
```

## getFloatingBallWindowInfo

```TypeScript
getFloatingBallWindowInfo(): Promise<FloatingBallWindowInfo>
```

Obtains the floating ball window information. This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FloatingBallWindowInfo](arkts-arkui-floatingball-floatingballwindowinfo-i.md)&gt; | Promise used to return the floating ball window information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: Internal error, the window type is not a floating ball. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: Internal IPC error. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: The process ID calling the API does not match the process ID of the session that created the floating ball. |
| [1300023](../errorcode-window.md#1300023-internal-error-of-the-floating-ball) | Floating ball internal error. Possible cause: System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-abnormal-floating-ball-window-state) | The floating ball window state is abnormal. Possible causes:<br>1. The floating ball controller has been destroyed. <br>2. The floating ball window is not created or has been destroyed. |
| [1300025](../errorcode-window.md#1300025-unsupported-operation-in-the-current-floating-ball-state) | The floating ball state does not support this operation. Possible cause: The floating ball is not started. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the window information of the floating ball.
floatingBallController.getFloatingBallWindowInfo().then((data: floatingBall.FloatingBallWindowInfo) => {
  console.info('Succeeded in getting floating ball window info. Info: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`Failed to get floating ball window info. Cause code: ${err.code}, message: ${err.message}`);
});
```

## off('stateChange')

```TypeScript
off(type: 'stateChange', callback?: Callback<FloatingBallState>): void
```

Unregisters the listener for lifecycle state changes of the floating ball.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'stateChange' | Yes | Event type. The event **'stateChange'** is triggered when the floating ball lifecycle state changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[FloatingBallState](arkts-arkui-floatingball-floatingballstate-e.md)&gt; | No | Callback used to return the floating ball lifecycle state. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300019](../errorcode-window.md#1300019-floating-ball-parameter-verification-error) | Wrong parameters for operating the floating ball. Possible causes:<br>1.Mandatory parameters are left unspecified. <br>2.Callback is null or not callable. |
| [1300023](../errorcode-window.md#1300023-internal-error-of-the-floating-ball) | Floating ball internal error. Possible cause: System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-abnormal-floating-ball-window-state) | The floating ball window state is abnormal. Possible cause: The floating ball controller has been destroyed. |

**Examples**

```TypeScript
// Define the callback function for status changes (the callback function must be the same as that registered).
let onStateChange = (state: floatingBall.FloatingBallState) => {
  console.info('Floating ball stateChange: ' + state);
};
try {
  // Unregister the callback for listening to floating ball state changes.
  floatingBallController.off('stateChange', onStateChange);
} catch (e) {
  console.error(`Failed to off stateChange floating ball. Cause:${e.code}, message:${e.message}`);
}
```

## off('click')

```TypeScript
off(type: 'click', callback?: Callback<void>): void
```

Unregisters the listener for click events of the floating ball.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'click' | Yes | Event type. The event **'click'** is triggered when the floating ball is tapped. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | Callback invoked when the floating ball is tapped. It does not return any parameter. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300019](../errorcode-window.md#1300019-floating-ball-parameter-verification-error) | Wrong parameters for operating the floating ball. Possible causes:<br>1.Mandatory parameters are left unspecified. <br>2.Callback is null or not callable. |
| [1300023](../errorcode-window.md#1300023-internal-error-of-the-floating-ball) | Floating ball internal error. Possible cause: System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-abnormal-floating-ball-window-state) | The floating ball window state is abnormal. Possible cause: The floating ball controller has been destroyed. |

**Examples**

```TypeScript
// Define the callback function for the click event (the callback function must be the same as that registered).
let onClick = () => {
  console.info('Floating ball onClick');
};
try {
  // Unregister the callback for listening to click events of the floating ball.
  floatingBallController.off('click', onClick);
} catch (e) {
  console.error(`Failed to off click floating ball. Cause:${e.code}, message:${e.message}`);
}
```

## offDestroy

```TypeScript
offDestroy(callback?: Callback<string>): void
```

Unregister floating ball destroy event listener.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | No | Indicates the callback function. If not provided, all callbacks for the given event type will be removed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300019](../errorcode-window.md#1300019-floating-ball-parameter-verification-error) | Wrong parameters for operating the floating ball. Possible cause: Callback is null or not callable. |
| [1300023](../errorcode-window.md#1300023-internal-error-of-the-floating-ball) | Floating ball internal error. Possible cause: System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-abnormal-floating-ball-window-state) | The floating ball window state is abnormal. Possible cause: The floating ball controller has been destroyed. |

**Examples**

```TypeScript
// Define the callback function for the destruction event (the callback function must be the same as that registered).
let onDestroy = (reason: string) => {
  console.info('Floating ball has destroyed, reason: ' + reason);
};
try {
  // Unregister the callback for listening to floating ball destruction events.
  floatingBallController?.offDestroy(onDestroy);
} catch (e) {
  console.error(`Failed to offDestroy floating ball. Cause:${e.code}, message:${e.message}`);
}
// Unregister all callbacks.
try {
  floatingBallController?.offDestroy();
} catch (e) {
  console.error(`Failed to offDestroy all listeners. Cause:${e.code}, message:${e.message}`);
}
```

## on('stateChange')

```TypeScript
on(type: 'stateChange', callback: Callback<FloatingBallState>): void
```

Registers a listener for lifecycle state changes of the floating ball. To prevent memory leaks, remember to unregister the listener when it is no longer needed.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'stateChange' | Yes | Event type. The event **'stateChange'** is triggered when the floating ball lifecycle state changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[FloatingBallState](arkts-arkui-floatingball-floatingballstate-e.md)&gt; | Yes | Callback used to return the floating ball lifecycle state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300019](../errorcode-window.md#1300019-floating-ball-parameter-verification-error) | Wrong parameters for operating the floating ball. Possible causes:<br>1.Mandatory parameters are left unspecified. <br>2.Callback is null or not callable. |
| [1300022](../errorcode-window.md#1300022-repeated-floating-ball-operation) | Repeated floating ball operation. |
| [1300023](../errorcode-window.md#1300023-internal-error-of-the-floating-ball) | Floating ball internal error. Possible cause: System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-abnormal-floating-ball-window-state) | The floating ball window state is abnormal. Possible cause: The floating ball controller has been destroyed. |

**Examples**

```TypeScript
// Define the callback function for status changes.
let onStateChange = (state: floatingBall.FloatingBallState) => {
  console.info('Floating ball stateChange: ' + state);
};
try {
  // Register the callback for listening to floating ball state changes.
  floatingBallController.on('stateChange', onStateChange);
} catch (e) {
  console.error(`Failed to on stateChange floating ball. Cause:${e.code}, message:${e.message}`);
}
```

## on('click')

```TypeScript
on(type: 'click', callback: Callback<void>): void
```

Registers a listener for click events of the floating ball. To prevent memory leaks, remember to unregister the listener when it is no longer needed.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'click' | Yes | Event type. The event **'click'** is triggered when the floating ball is tapped. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback invoked when the floating ball is tapped. It does not return any parameter. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300019](../errorcode-window.md#1300019-floating-ball-parameter-verification-error) | Wrong parameters for operating the floating ball. Possible causes:<br>1.Mandatory parameters are left unspecified. <br>2.Callback is null or not callable. |
| [1300022](../errorcode-window.md#1300022-repeated-floating-ball-operation) | Repeated floating ball operation. |
| [1300023](../errorcode-window.md#1300023-internal-error-of-the-floating-ball) | Floating ball internal error. Possible cause: System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-abnormal-floating-ball-window-state) | The floating ball window state is abnormal. Possible cause: The floating ball controller has been destroyed. |

**Examples**

```TypeScript
// Define the click event callback function.
let onClick = () => {
  console.info('Floating ball onClick');
};
try {
  // Register the callback for listening to click events of the floating ball.
  floatingBallController.on('click', onClick);
} catch (e) {
  console.error(`Failed to on click floating ball. Cause:${e.code}, message:${e.message}`);
}
```

## onDestroy

```TypeScript
onDestroy(callback: Callback<string>): void
```

Register floating ball destroy event listener.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | Yes | Used to handle {'destroy'} command. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300019](../errorcode-window.md#1300019-floating-ball-parameter-verification-error) | Wrong parameters for operating the floating ball. Possible cause: Callback is null or not callable. |
| [1300022](../errorcode-window.md#1300022-repeated-floating-ball-operation) | Repeated floating ball operation. |
| [1300023](../errorcode-window.md#1300023-internal-error-of-the-floating-ball) | Floating ball internal error. Possible cause: System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-abnormal-floating-ball-window-state) | The floating ball window state is abnormal. Possible cause: The floating ball controller has been destroyed. |

**Examples**

```TypeScript
// Define the callback function for the destruction event.
let onDestroy = (reason: string) => {
  console.info('Floating ball has destroyed, reason: ' + reason);
};
try {
  // Register the callback for listening to floating ball destruction events.
  floatingBallController?.onDestroy(onDestroy);
} catch (e) {
  console.error(`Failed to onDestroy floating ball. Cause:${e.code}, message:${e.message}`);
}
```

## restoreMainWindow

```TypeScript
restoreMainWindow(want: Want): Promise<void>
```

Restores the main window of the application and loads the specified page. This API uses a promise to return the result. This API can be called only after the floating ball is tapped. If the application has the **ohos.permission.AUTO_RESTORE_MAIN_WINDOW** permission, this API can be called directly without tapping the floating ball.

**Since:** 20

**Required permissions:** ohos.permission.USE_FLOAT_BALL

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Want used for loading the specified page. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually returned by VerifyAccessToken. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: Internal error, the window type is not a floating ball. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: Internal IPC error. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: The process ID calling the API does not match the process ID of the session that created the floating ball. |
| [1300019](../errorcode-window.md#1300019-floating-ball-parameter-verification-error) | Wrong parameters for operating the floating ball. Possible cause: Want parameter is null or invalid. |
| [1300023](../errorcode-window.md#1300023-internal-error-of-the-floating-ball) | Floating ball internal error. Possible cause: System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-abnormal-floating-ball-window-state) | The floating ball window state is abnormal. Possible causes:<br>1.The floating ball controller has been destroyed. <br>2.The floating ball window is not created or has been destroyed. |
| [1300025](../errorcode-window.md#1300025-unsupported-operation-in-the-current-floating-ball-state) | The floating ball state does not support this operation. Possible cause: The floating ball is not started. |
| [1300026](../errorcode-window.md#1300026-failure-in-launch-an-application-window-via-a-floating-ball) | Failed to restore the main window. Possible causes: 1. Invalid parameter. The provided bundleName does not match the caller's application bundleName. 2. The application lacks the ohos.permission.AUTO_RESTORE_MAIN_WINDOW permission, and no user interaction (click) on the floating ball has occurred. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

// Set the Want parameter of the main window to be restored.
let want: Want = {
  bundleName: 'xxx.xxx.xxx',
  abilityName: 'EntryAbility'
};
try {
  // Restore the main window of the application and load the specified page.
  floatingBallController.restoreMainWindow(want).then(() => {
    console.info('Succeeded in restoring floating ball main window.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to restore floating ball main window. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (e) {
  console.error(`Failed to restore floating ball main window. Cause:${e.code}, message:${e.message}`);
}
```

## setFloatingBallVisibilityInApp

```TypeScript
setFloatingBallVisibilityInApp(isVisible: boolean): Promise<void>
```

Sets whether the floating ball is visible in the application. This API uses a promise to return the result.

- When the application is on the recent tasks screen (the [lifecycle state](../../../windowmanager/window-lifecycle.md#lifecycle-states-of-an-apps-main-window) is **PAUSED**), the floating ball is invisible.  
- By default (when this API is not called) or when this API is called with the value **true** passed in, the  
floating ball is visible except on the recent tasks screen.  
- When this API is called with the value **false** passed in, the floating ball is invisible when the application  
is in the foreground (the [lifecycle state](../../../windowmanager/window-lifecycle.md#lifecycle-states-of-an-apps-main-window) is **SHOWN** or **RESUMED**) and is visible when the application is in the background (the [lifecycle state](../../../windowmanager/window-lifecycle.md#lifecycle-states-of-an-apps-main-window) is **HIDDEN**).

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isVisible | boolean | Yes | **true** indicates that the floating ball is visible in the application, and **false** indicates the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: Internal IPC error. |
| [1300023](../errorcode-window.md#1300023-internal-error-of-the-floating-ball) | Floating ball internal error. Possible cause: The floating ball controller is null. |
| [1300024](../errorcode-window.md#1300024-abnormal-floating-ball-window-state) | The floating ball window state is abnormal. Possible causes: The floating ball window has not been created or has been destroyed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Set the floating ball to be invisible in the application.
floatingBallController?.setFloatingBallVisibilityInApp(false).then(() => {
  console.info('Succeeded in setting floating ball visibility.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set floating ball visibility. Cause code: ${err.code}, message: ${err.message}`);
});
```

## startFloatingBall

```TypeScript
startFloatingBall(params: FloatingBallParams): Promise<void>
```

Starts the floating ball. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.USE_FLOAT_BALL

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [FloatingBallParams](arkts-arkui-floatingball-floatingballparams-i.md) | Yes | Parameters for starting the floating ball. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually returned by VerifyAccessToken. |
| [1300019](../errorcode-window.md#1300019-floating-ball-parameter-verification-error) | Wrong parameters for operating the floating ball. Possible causes:<br>1. FloatingBallParams parameter is null. <br>2. Parameter is invalid, such as invalid icon object, template type, or title (empty or exceeds 64 bytes). |
| [1300020](../errorcode-window.md#1300020-failure-in-creating-a-floating-ball-window) | Failed to create the floating ball window. Possible cause: The main window is not shown. |
| [1300021](../errorcode-window.md#1300021-failure-in-starting-multiple-floating-balls) | Failed to start multiple floating ball windows. |
| [1300022](../errorcode-window.md#1300022-repeated-floating-ball-operation) | Repeated floating ball operation. |
| [1300023](../errorcode-window.md#1300023-internal-error-of-the-floating-ball) | Floating ball internal error. Possible causes:<br>1.The floating ball controller has been destroyed. <br>2.Internal error, failed to show the floating ball window. Such as insufficient resources or abnormal window service. |
| [1300024](../errorcode-window.md#1300024-abnormal-floating-ball-window-state) | The floating ball window state is abnormal. Possible cause: The floating ball window is not created or has been destroyed. |
| [1300025](../errorcode-window.md#1300025-unsupported-operation-in-the-current-floating-ball-state) | The floating ball state does not support this operation. Possible cause: The floating ball state is stopping. |
| [1300034](../errorcode-window.md#1300034-operation-of-the-float-view-conflicts-with-those-of-other-floating-windows) | This operation conflicts with other floating windows. Possible cause: App has already started float view.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Set the parameters for starting the floating ball.
let startParams: floatingBall.FloatingBallParams = {
  template: floatingBall.FloatingBallTemplate.EMPHATIC,
  title: 'title',
  content: 'content'
};
try {
  // Start the floating ball.
  floatingBallController.startFloatingBall(startParams).then(() => {
    console.info('Succeeded in starting floating ball.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to start floating ball. Cause:${err.code}, message:${err.message}`);
  });
} catch (e) {
  console.error(`Failed to start floating ball. Cause:${e.code}, message:${e.message}`);
}
```

## stopFloatingBall

```TypeScript
stopFloatingBall(): Promise<void>
```

Stops the floating ball. This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300022](../errorcode-window.md#1300022-repeated-floating-ball-operation) | Repeated floating ball operation. |
| [1300023](../errorcode-window.md#1300023-internal-error-of-the-floating-ball) | Floating ball internal error. Possible cause: System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-abnormal-floating-ball-window-state) | The floating ball window state is abnormal. Possible cause: The floating ball window is not created or has been destroyed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Stop the floating ball.
floatingBallController.stopFloatingBall().then(() => {
  console.info('Succeeded in stopping floating ball.');
}).catch((err: BusinessError) => {
  console.error(`Failed to stop floating ball. Cause:${err.code}, message:${err.message}`);
});
```

## updateFloatingBall

```TypeScript
updateFloatingBall(params: FloatingBallParams): Promise<void>
```

Updates the floating ball. This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [FloatingBallParams](arkts-arkui-floatingball-floatingballparams-i.md) | Yes | Parameters for updating the floating ball. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: Internal error, the window type is not a floating ball. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: Internal IPC error. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: The process ID calling the API does not match the process ID of the session that created the floating ball. |
| [1300019](../errorcode-window.md#1300019-floating-ball-parameter-verification-error) | Wrong parameters for operating the floating ball. Possible causes:<br>1.FloatingBallParams parameter is null. <br>2.Parameter is invalid, such as invalid icon object, template type, or title (empty or exceeds 64 bytes). |
| [1300023](../errorcode-window.md#1300023-internal-error-of-the-floating-ball) | Floating ball internal error. Possible cause: System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-abnormal-floating-ball-window-state) | The floating ball window state is abnormal. Possible cause: The floating ball window is not created or has been destroyed. |
| [1300025](../errorcode-window.md#1300025-unsupported-operation-in-the-current-floating-ball-state) | The floating ball state does not support this operation. Possible cause: The floating ball is not started. |
| [1300027](../errorcode-window.md#1300027-cannot-change-template-type-when-updating-the-floating-ball) | When updating the floating ball, the template type cannot be changed. |
| [1300028](../errorcode-window.md#1300028-floating-ball-based-on-a-static-template-cannot-be-updated) | Updating static template-based floating balls is not supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Set the parameters for updating the floating ball.
let updateParams: floatingBall.FloatingBallParams = {
  template: floatingBall.FloatingBallTemplate.EMPHATIC,
  title: 'title2',
  content: 'content2'
};
try {
  // Update the floating ball.
  floatingBallController.updateFloatingBall(updateParams).then(() => {
    console.info('Succeeded in updating floating ball.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to update floating ball. Cause:${err.code}, message:${err.message}`);
  });
} catch (e) {
  console.error(`Failed to update floating ball. Cause:${e.code}, message:${e.message}`);
}
```
