# PiPController

```TypeScript
interface PiPController
```

Implements a PiP controller that starts, stops, or updates a PiP window and registers callbacks.

Before calling any of the following APIs, you must use [PiPWindow.create()](arkts-arkui-pipwindow-create-f.md) to create a PiPController instance.

**Since:** 11

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { PiPWindow } from '@kit.ArkUI';
```

## getPiPSettingSwitch

```TypeScript
getPiPSettingSwitch(): Promise<boolean>
```

Obtains the status of the auto-start PiP switch in Settings. This API uses a promise to return the result.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the auto-start PiP switch status. **true** if enabled, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300014](../errorcode-window.md#1300014-pip-internal-error) | PiP internal error. Possible cause: The PiP controller has been destroyed. |

**Examples**

```TypeScript
let pipSwitchStatus: boolean | undefined = undefined;
try {
  // Obtain the status of the switch for automatically starting the PiP window.
  let promise : Promise<boolean> = this.pipController.getPiPSettingSwitch();
  promise.then((data) => {
    // Save the obtained switch status.
    pipSwitchStatus = data;
    console.info('Succeeded in getting pip switch status. switchStatus: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error(`Failed to get pip switch status. Code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to get pip switch status. Code: ${exception.code}, message: ${exception.message}`);
}
```

## getPiPWindowInfo

```TypeScript
getPiPWindowInfo(): Promise<PiPWindowInfo>
```

Obtains the PIP window information. This API uses a promise to return the result.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PiPWindowInfo](arkts-arkui-pipwindow-pipwindowinfo-i.md)&gt; | Promise used to return the information about the current PIP window. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300014](../errorcode-window.md#1300014-pip-internal-error) | PiP internal error. Possible causes:<br>1.The PiP controller has been destroyed. <br>2.The PiP window is not created or has been destroyed. |

**Examples**

```TypeScript
let pipWindowInfo: PiPWindow.PiPWindowInfo | undefined = undefined;
try {
  // Obtain the PiP window information.
  let promise : Promise<PiPWindow.PiPWindowInfo> = this.pipController.getPiPWindowInfo();
  promise.then((data) => {
    // Save the obtained PiP window information.
    pipWindowInfo = data;
    console.info('Success in get pip window info. Info: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error(`Failed to get pip window info. Code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to get pip window info. Code: ${exception.code}, message: ${exception.message}`);
}
```

## isPiPActive

```TypeScript
isPiPActive(): Promise<boolean>
```

Check whether the PiP window is active. This API uses a promise to return the result.

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the PiP window status. **true** is returned if the PiP window is visible, and **false** is returned if the PiP window is invisible (hidden in the sidebar). If this API is called when the PiP lifecycle is not [STARTED](arkts-arkui-pipwindow-pipstate-e.md), **false** is always returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300014](../errorcode-window.md#1300014-pip-internal-error) | PiP internal error. Possible causes:<br>1.The PiP controller has been destroyed. <br>2.The PiP window is not created or has been destroyed. |

**Examples**

```TypeScript
let pipActiveStatus: boolean | undefined = undefined;
try {
  // Obtain the active status of the PiP window.
  let promise : Promise<boolean> | undefined = this.pipController?.isPiPActive();
  promise?.then((data) => {
    // Save the obtained active status of the PiP window.
    pipActiveStatus = data;
    console.info('Succeeded in getting pip active status. activeStatus: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error(`Failed to get pip active status. Code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to get pip active status. Code: ${exception.code}, message: ${exception.message}`);
}
```

## off('stateChange')

```TypeScript
off(type: 'stateChange'): void
```

Unsubscribes from PiP state events.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'stateChange' | Yes | Event type. The value is fixed at **'stateChange'**, indicating that the PiP state changes. |

**Examples**

```TypeScript
// Unsubscribe from PiP state events.
this.pipController.off('stateChange');
```

## off('controlPanelActionEvent')

```TypeScript
off(type: 'controlPanelActionEvent'): void
```

Unsubscribes from PiP action events. The **[off('controlEvent')](#offcontrolevent)** API is preferred.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'controlPanelActionEvent' | Yes | Event type. The value is fixed at **'controlPanelActionEvent'**, indicating the action event of the PiP controller. |

**Examples**

```TypeScript
// Unsubscribe from PiP controller action events.
this.pipController.off('controlPanelActionEvent');
```

## off('controlEvent')

```TypeScript
off(type: 'controlEvent', callback?: Callback<ControlEventParam>): void
```

Unsubscribes from PiP action events.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'controlEvent' | Yes | Event type. The value is fixed at **'controlEvent'**, indicating the action event of the PiP controller. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ControlEventParam](arkts-arkui-pipwindow-controleventparam-i.md)&gt; | No | Describes the action event callback of the PiP controller. If no value is passed in, all subscriptions to the specified event are canceled. |

**Examples**

```TypeScript
let callbackFunc = (event: PiPWindow.ControlEventParam) => {
  console.info(`receive control event: ${event.controlType}, ${event.status}`);
}
// Unsubscribe from PiP controller action events.
this.pipController.off('controlEvent', callbackFunc);
```

## off('pipWindowSizeChange')

```TypeScript
off(type: 'pipWindowSizeChange', callback?: Callback<PiPWindowSize>): void
```

Unsubscribes from the PiP window size change event.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'pipWindowSizeChange' | Yes | Event type. The value is fixed at **'pipWindowSizeChange'**, indicating that the PiP window size changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PiPWindowSize](arkts-arkui-pipwindow-pipwindowsize-i.md)&gt; | No | Callback used to return the size of the current PiP window. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

```TypeScript
const callback = (size: PiPWindow.PiPWindowSize) => {
  // ...
}
try {
  // Enable listening through the on API.
  this.pipController.on('pipWindowSizeChange', callback);
} catch (exception) {
  console.error(`Failed to enable the listener for pip window size changes. Code: ${exception.code}, message: ${exception.message}`);
}

try {
  // Disable the listening of a specified callback.
  this.pipController.off('pipWindowSizeChange', callback);
  // Unregister all the callbacks that have been registered through on().
  this.pipController.off('pipWindowSizeChange');
} catch (exception) {
  console.error(`Failed to disable the listener for pip window size changes. Code: ${exception.code}, message: ${exception.message}`);
}
```

## off('activeStatusChange')

```TypeScript
off(type: 'activeStatusChange', callback?: Callback<boolean>): void
```

Unsubscribes from PiP window active status change events.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'activeStatusChange' | Yes | Event type. The value is fixed at **'activeStatusChange'**, indicating that the PiP window active status changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | No | PiP window active status. **true** is returned if the PiP window is visible, and **false** is returned if the PiP window is invisible (hidden in the sidebar). If no value is passed in, all subscriptions to the specified event are canceled. |

**Examples**

```TypeScript
let callback = (activeStatus: boolean) => {
  console.info(`pip window is visible: ${activeStatus}`);
}
// Unsubscribe from PiP window active status change events.
this.pipController.off('activeStatusChange', callback);
```

## on('stateChange')

```TypeScript
on(type: 'stateChange', callback: (state: PiPState, reason: string) => void): void
```

Subscribes to PiP state events. To avoid potential memory leaks, you are advised to stop listening when it is no longer needed.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'stateChange' | Yes | Event type. The value is fixed at **'stateChange'**, indicating that the PiP state changes. |
| callback | (state: PiPState, reason: string) =&gt; void | Yes | Callback used to return the result, which includes the following information:<br>- **state**: [PiPState](arkts-arkui-pipwindow-pipstate-e.md), indicating the new PiP state. <br>- **reason**: a string indicating the reason for the state change. <br>Before &lt;!--RP1--&gt;OpenHarmony 6.1&lt;!--RP1End--&gt;, the value of **reason** is always **0**, which can be ignored.<br>Since &lt;!--RP1--&gt;OpenHarmony 6.1&lt;!--RP1End--&gt;, **reason** indicates the reason for switching the current lifecycle. The options are as follows: <br>**"requestStart"**: An application calls the **startPip** API. <br>**"autoStart"**: The application is automatically started in PiP mode when it is switched to the background. <br>**"requestDelete"**: The application calls the **stopPip** API. <br>**"panelActionDelete"**: The user taps the close button in the PiP window. <br>**"dragDelete"**: The user drags the PiP window to delete. <br>**"panelActionRestore"**: The user taps the restore button in the PiP window (or taps the PiP window if there is no restore button) to restore the PiP window. <br>**"other"**: Other reasons, such as the current window or application's main window being closed due to the startup of a new PiP window. |

**Examples**

```TypeScript
// Subscribe to PiP state events.
this.pipController.on('stateChange', (state: PiPWindow.PiPState, reason: string) => {
  let curState: string = '';
  switch (state) {
    case PiPWindow.PiPState.ABOUT_TO_START:
      curState = 'ABOUT_TO_START';
      break;
    case PiPWindow.PiPState.STARTED:
      curState = 'STARTED';
      break;
    case PiPWindow.PiPState.ABOUT_TO_STOP:
      curState = 'ABOUT_TO_STOP';
      break;
    case PiPWindow.PiPState.STOPPED:
      curState = 'STOPPED';
      break;
    case PiPWindow.PiPState.ABOUT_TO_RESTORE:
      curState = 'ABOUT_TO_RESTORE';
      break;
    case PiPWindow.PiPState.ERROR:
      curState = 'ERROR';
      break;
    default:
      break;
  }
  console.info('stateChange:' + curState + ' reason:' + reason);
});
```

## on('controlPanelActionEvent')

```TypeScript
on(type: 'controlPanelActionEvent', callback: ControlPanelActionEventCallback): void
```

Subscribes to PiP action events. To avoid potential memory leaks, you are advised to stop listening when it is no longer needed. The [on('controlEvent')](#oncontrolevent) API is preferred.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'controlPanelActionEvent' | Yes | Event type. The value is fixed at **'controlPanelActionEvent'**, indicating the action event of the PiP controller. |
| callback | [ControlPanelActionEventCallback](arkts-arkui-pipwindow-controlpanelactioneventcallback-t.md) | Yes | Action event callback of the PiP controller.<br>**Since:** 12 |

**Examples**

```TypeScript
// Subscribe to PiP controller action events.
this.pipController.on('controlPanelActionEvent', (event: PiPWindow.PiPActionEventType, status?: number) => {
  switch (event) {
    case 'playbackStateChanged':
      if (status === 0) {
        // Stop the video.
      } else if (status === 1) {
        // Play the video.
      }
      break;
    case 'nextVideo':
      // Switch to the next video.
      break;
    case 'previousVideo':
      // Switch to the previous video.
      break;
    case 'fastForward':
      // Fast forward the video.
      break;
    case 'fastBackward':
      // Rewind the video.
      break;
    default:
      break;
  }
  console.info('registerActionEventCallback, event:' + event);
});
```

## on('controlEvent')

```TypeScript
on(type: 'controlEvent', callback: Callback<ControlEventParam>): void
```

Subscribes to PiP action events. To avoid potential memory leaks, you are advised to stop listening when it is no longer needed.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'controlEvent' | Yes | Event type. The value is fixed at **'controlEvent'**, indicating the action event of the PiP controller. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ControlEventParam](arkts-arkui-pipwindow-controleventparam-i.md)&gt; | Yes | Action event callback of the PiP controller. |

**Examples**

```TypeScript
// Subscribe to PiP controller action events.
this.pipController.on('controlEvent', (control) => {
  switch (control.controlType) {
    case PiPWindow.PiPControlType.VIDEO_PLAY_PAUSE:
      if (control.status === PiPWindow.PiPControlStatus.PAUSE) {
        // Stop the video.
      } else if (control.status === PiPWindow.PiPControlStatus.PLAY) {
        // Play the video.
      }
      break;
    case PiPWindow.PiPControlType.VIDEO_NEXT:
      // Switch to the next video.
      break;
    case PiPWindow.PiPControlType.VIDEO_PREVIOUS:
      // Switch to the previous video.
      break;
    case PiPWindow.PiPControlType.FAST_FORWARD:
      // Fast forward the video.
      break;
    case PiPWindow.PiPControlType.FAST_BACKWARD:
      // Rewind the video.
      break;
    default:
      break;
  }
  console.info('registerControlEventCallback, controlType:' + control.controlType + ', status' + control.status);
});
```

## on('pipWindowSizeChange')

```TypeScript
on(type: 'pipWindowSizeChange', callback: Callback<PiPWindowSize>): void
```

Subscribes to PiP window size change events. To avoid potential memory leaks, you are advised to stop listening when it is no longer needed.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'pipWindowSizeChange' | Yes | Event type. The value is fixed at **'pipWindowSizeChange'**, indicating that the PiP window size changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PiPWindowSize](arkts-arkui-pipwindow-pipwindowsize-i.md)&gt; | Yes | Callback used to return the size of the current PiP window. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Callback is already registered. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300014](../errorcode-window.md#1300014-pip-internal-error) | PiP internal error. Possible cause: The PiP controller has been destroyed. |

**Examples**

```TypeScript
try {
  // Subscribe to PiP window size change events.
  this.pipController.on('pipWindowSizeChange', (size: PiPWindow.PiPWindowSize) => {
    console.info('Succeeded in enabling the listener for pip window size changes. size: ' + JSON.stringify(size));
  });
} catch (exception) {
  console.error(`Failed to enable the listener for pip window size changes. Code: ${exception.code}, message: ${exception.message}`);
}
```

## on('activeStatusChange')

```TypeScript
on(type: 'activeStatusChange', callback: Callback<boolean>): void
```

Subscribes to PiP window active status change events. To avoid potential memory leaks, you are advised to stop listening when it is no longer needed.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'activeStatusChange' | Yes | Event type. The value is fixed at **'activeStatusChange'**, indicating that the PiP window active status changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | Yes | PiP window active status. **true** is returned if the PiP window is visible, and **false** is returned if the PiP window is invisible (hidden in the sidebar). |

**Examples**

```TypeScript
let callback = (activeStatus: boolean) => {
  console.info(`pip window is visible: ${activeStatus}`);
}
// Subscribe to PiP window active status change events.
this.pipController.on('activeStatusChange', callback);
```

## setAutoStartEnabled

```TypeScript
setAutoStartEnabled(enable: boolean): void
```

Sets whether to automatically start the PiP window when the application's main window which can start the PiP window transitions to the background. By default, the PiP window is not automatically started.

If the XComponent approach is used to implement PiP and the **Navigation** component is used for route management, the system caches the top stack information with the specified navigation ID upon the first call of **setAutoStartEnabled(true)**.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | If the PiP window needs to be automatically started when the application's main window transitions to the background, set this parameter to **true**. Otherwise, set this parameter to **false**. If the PiP feature under **Settings**   > **System** > **Multi-window** is disabled, the PiP window will not be automatically started when the application's main window transitions to the background even if this parameter is set to **true**. |

**Examples**

```TypeScript
let enable: boolean = true;
this.pipController.setAutoStartEnabled(enable); // Set whether to automatically start the PiP window when the application's main window transitions to the background.
```

## setPiPControlEnabled

```TypeScript
setPiPControlEnabled(controlType: PiPControlType, enabled: boolean): void
```

Sets the enabled status for a component displayed on the PiP controller.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| controlType | [PiPControlType](arkts-arkui-pipwindow-pipcontroltype-e.md) | Yes | Type of the component displayed on the PiP controller. |
| enabled | boolean | Yes | Enabled status of the component displayed on the PiP controller. **true** if enabled, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: The PiPController is not created or destroyed. |

**Examples**

```TypeScript
let controlType: PiPWindow.PiPControlType = PiPWindow.PiPControlType.VIDEO_PLAY_PAUSE; // Play/Pause component displayed on the video playback control panel.
let enabled: boolean = false; // The Play/Pause component displayed on the video playback control panel is in the disabled state.
this.pipController.setPiPControlEnabled(controlType, enabled); // Set the enabled status of the PiP controller.
```

## startPiP

```TypeScript
startPiP(): Promise<void>
```

Starts a PiP window. This API uses a promise to return the result.

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
| [1300012](../errorcode-window.md#1300012-abnormal-pip-window-status) | The PiP window state is abnormal. Possible causes:<br>1.The PiP controller has been destroyed. <br>2.The PiP window is not created or has been destroyed. |
| [1300013](../errorcode-window.md#1300013-failure-in-creating-a-pip-window) | Failed to create the PiP window. Possible causes:<br>1.PiP configuration parameters are invalid, such as pipOption or context is null. <br>2.The XComponentController or main window is null. <br>3.The main window is not shown (non-auto-start scenario). <br>4.Navigation component operation failed. |
| [1300014](../errorcode-window.md#1300014-pip-internal-error) | PiP internal error. Possible cause: Internal error, failed to show the PiP window. such as insufficient resources or abnormal window service. |
| [1300015](../errorcode-window.md#1300015-repeated-pip-operations) | Repeated PiP operation. |
| [1300034](../errorcode-window.md#1300034-operation-of-the-float-view-conflicts-with-those-of-other-floating-windows) | This operation conflicts with other floating windows. Possible cause: App has already started float view.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
// You can call pipController according to the pipController definition.
let promise : Promise<void> = this.pipController.startPiP(); // Start the PiP window.
promise.then(() => {
  console.info(`Succeeded in starting pip.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to start pip. Cause:${err.code}, message:${err.message}`);
});
```

## stopPiP

```TypeScript
stopPiP(): Promise<void>
```

Stops a PiP window. This API uses a promise to return the result.

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
| [1300011](../errorcode-window.md#1300011-failure-in-destroying-a-pip-window) | Failed to destroy the PiP window. Possible cause: Internal error, the window type is not a PiP window. |
| [1300012](../errorcode-window.md#1300012-abnormal-pip-window-status) | The PiP window state is abnormal. Possible cause: The PiP window is not created or has been destroyed. |
| [1300015](../errorcode-window.md#1300015-repeated-pip-operations) | Repeated PiP operation. |

**Examples**

```TypeScript
let promise : Promise<void> = this.pipController.stopPiP(); // Stop the PiP window.
promise.then(() => {
  console.info(`Succeeded in stopping pip.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to stop pip. Cause:${err.code}, message:${err.message}`);
});
```

## updateContentNode

```TypeScript
updateContentNode(contentNode: typeNode.XComponent): Promise<void>
```

Updates the PiP node content. This API uses a promise to return the result.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| contentNode | [typeNode.XComponent](arkts-arkui-typenode-xcomponent-t.md) | Yes | Content to be rendered in the PiP window. The parameter value cannot be empty. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300014](../errorcode-window.md#1300014-pip-internal-error) | PiP internal error. Possible cause: The PiP controller has been destroyed. |

**Examples**

```TypeScript
import { typeNode, UIContext } from '@kit.ArkUI';

let context: UIContext = this.getUIContext(); // Obtain UIContext using this.getUIContext().

try {
  let contentNode = typeNode.createNode(context, "XComponent"); // Create an XComponent node to render the PiP window content.
  this.pipController.updateContentNode(contentNode); // Update the PiP node content.
} catch (exception) {
  console.error(`Failed to update content node. Code: ${exception.code}, message: ${exception.message}`);
}
```

## updateContentSize

```TypeScript
updateContentSize(width: number, height: number): void
```

Updates the media content size when the media content changes.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | Width of the media content, in px. The value must be an integer greater than 0. It is used to update the aspect ratio of the PiP window. |
| height | number | Yes | Height of the media content, in px. The value must be an integer greater than 0. It is used to update the aspect ratio of the PiP window. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: The PiPController is not created or destroyed. |

**Examples**

```TypeScript
let width: number = 540; // The content width changes to 540 px.
let height: number = 960; // The content height changes to 960 px.
this.pipController.updateContentSize(width, height); // Update the size of the PiP window content.
```

## updatePiPControlStatus

```TypeScript
updatePiPControlStatus(controlType: PiPControlType, status: PiPControlStatus): void
```

Updates the PiP controller status.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| controlType | [PiPControlType](arkts-arkui-pipwindow-pipcontroltype-e.md) | Yes | Type of the component displayed on the PiP controller. Currently, only the **VIDEO_PLAY_PAUSE**, **MICROPHONE_SWITCH**, **CAMERA_SWITCH**, and **MUTE_SWITCH** component types are supported. If other component types are passed, they do not take effect and no error is reported. |
| status | [PiPControlStatus](arkts-arkui-pipwindow-pipcontrolstatus-e.md) | Yes | Status of the component displayed on the PiP controller. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: The PiPController is not created or destroyed. |

**Examples**

```TypeScript
let controlType: PiPWindow.PiPControlType = PiPWindow.PiPControlType.VIDEO_PLAY_PAUSE; // Play/Pause component displayed on the video playback control panel.
let status: PiPWindow.PiPControlStatus = PiPWindow.PiPControlStatus.PLAY; // The Play/Pause component displayed on the video playback control panel is in the playing state.
this.pipController.updatePiPControlStatus(controlType, status); // Update the PiP controller status.
```
