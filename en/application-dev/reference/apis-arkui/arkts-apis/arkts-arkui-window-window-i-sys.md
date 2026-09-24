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

## attachLayoutToParentWindow

```TypeScript
attachLayoutToParentWindow(anchorInfo?: WindowAnchorInfo, attachOptions?: SubWindowAttachOptions): Promise<void>
```

Attaches a first-level child window to the main window to maintain a fixed relative position. This API uses a promise to return the result. The relative position is represented by the anchor point offset between the child window and the parent window. The child window and the parent window use the same window anchor point.

> **NOTE:** 
> 
> - Only first-level child windows can call this API. The child window must be in floating window mode (that is, the window mode is **window.WindowStatusType.FLOATING**).
> 
> - After the child window calls this API, the display position of the child window immediately follows the main window and the relative position remains unchanged. In addition, the size and mode changes of the main window can be listened to. The effect will persist unless the [detachLayoutToParentWindow()](#detachlayouttoparentwindow) API is called for detaching.
> 
> -After the child window calls this API, calling APIs such as
> [moveWindowTo()](arkts-arkui-window-window-i.md#movewindowto),
> [maximize()](arkts-arkui-window-window-i.md#maximize), and
> [setFollowParentWindowLayoutEnabled()](arkts-arkui-window-window-i.md#setfollowparentwindowlayoutenabled)
> to change the window position, or dragging and moving or dragging and resizing the child window through mouse
> or touch operations will not take effect.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| anchorInfo | [WindowAnchorInfo](arkts-arkui-window-windowanchorinfo-i-sys.md) | No | Anchor point information used to attach the first-level child window to the main window to maintain the fixed relative position. If this parameter is not passed, the default logic is the same as that of [WindowAnchorInfo] [WindowAnchorInfo](arkts-arkui-window-windowanchorinfo-i-sys.md). |
| attachOptions | [SubWindowAttachOptions](arkts-arkui-window-subwindowattachoptions-i-sys.md) | No | Additional parameters for setting the child window layout. If this parameter is not passed, the default logic is the same as that of [SubWindowAttachOptions] SubWindoWattachOptions. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function attachLayoutToParentWindow can not work correctly due to limited device capabilities. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: 1. Invalid window type. Only subwindows are supported; 2. The current window's parent window is not a main window; 3. Only level-1 subwindows are supported. |
| [1300010](../errorcode-window.md#1300010-unsupported-operation-in-the-current-window-mode) | The operation in the current window status is invalid. Possible cause: 1. The subwindow is following its parent window's layout. 2. The subwindow is not in the floating mode. |

**Examples**

```TypeScript
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
        let anchorInfo : window.WindowAnchorInfo = {
          anchorType: window.WindowAnchor.TOP_START,
          offsetX: 0,
          offsetY: 0
        };
        let attachOptions: window.SubWindowAttachOptions = {
          parentWindowSizeChangeCallback:(data: window.Size) => {
            console.info(`Successfully accepted parentWindow size change, width: ${data.width}, height: ${data.height}`);
          },
          parentWindowStatusChangeCallback:(type: window.WindowStatusType) => {
            console.info(`Successfully accepted parentWindow status change, statusType: ${type}`);
          },
          isIntersectedWidthLimit: true,
          isIntersectedHeightLimit: true
        }
        subWindow.attachLayoutToParentWindow(anchorInfo, attachOptions).then(() => {
          console.info("Succeeded in attaching to the main window");
        }).catch((error: BusinessError) => {
          console.error(`attachLayoutToParentWindow failed. ${error.code} ${error.message}`);
        })
      }).catch((error: BusinessError) => {
        console.error(`createSubWindow failed. ${error.code} ${error.message}`);
      })
    });
  }
}
```

## bindDialogTarget

```TypeScript
bindDialogTarget(token: rpc.RemoteObject, deathCallback: Callback<void>): Promise<void>
```

Binds the modal window to the target window. After the binding is successful, the target window cannot respond to user operations. In addition, a callback used to listen for modal window destruction events is added. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| token | [rpc.RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md) | Yes | Token of the target window. |
| deathCallback | [Callback](arkts-arkui-window-callback-i.md)&lt;void&gt; | Yes | Callback used to listen for modal window destruction events. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { Want, ServiceExtensionAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export class Property {
  public value: Object

  constructor(value: Object) {
    this.value = value
  }
}

export default class ServiceExtAbility extends ServiceExtensionAbility {
  onRequest(want: Want, startId: number) {
    console.info('onRequest');
    let config: window.Configuration = {
      name: 'test',
      windowType: window.WindowType.TYPE_DIALOG,
      ctx: this.context
    };
    try {
      window.createWindow(config, (err: BusinessError, data) => {
        const errCode: number = err?.code;
        if (errCode) {
          console.error(`Failed to create the window. Cause code: ${err?.code}, message: ${err?.message}`);
          return;
        }
        if (!data) {
          console.error('data is null');
          return;
        }
        let token = want.parameters?.['ohos.ability.params.request.token'] as Property;
        let value = token.value as rpc.RemoteObject;
        let promise = data.bindDialogTarget(value, () => {
          console.info('Dialog Window Need Destroy.');
        });
        promise.then(() => {
          console.info('Succeeded in binding dialog target.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to bind dialog target. Cause code: ${err?.code}, message: ${err?.message}`);
        });
      });
    } catch (err) {
      console.error(`Failed to bind dialog target. Cause code: ${err?.code}, message: ${err?.message}`)
    }
  }
}
```

<a id="binddialogtarget-1"></a>

## bindDialogTarget

```TypeScript
bindDialogTarget(token: rpc.RemoteObject, deathCallback: Callback<void>, callback: AsyncCallback<void>): void
```

Binds the modal window to the target window. After the binding is successful, the target window cannot respond to user operations. In addition, a callback used to listen for modal window destruction events is added. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| token | [rpc.RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md) | Yes | Token of the target window. |
| deathCallback | [Callback](arkts-arkui-window-callback-i.md)&lt;void&gt; | Yes | Callback used to listen for modal window destruction events. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { Want, ServiceExtensionAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export class Property {
  public value: Object

  constructor(value: Object) {
    this.value = value
  }
}

export default class ServiceExtAbility extends ServiceExtensionAbility {
  onRequest(want: Want, startId: number) {
    console.info('onRequest');
    let config: window.Configuration = {
      name: 'test',
      windowType: window.WindowType.TYPE_DIALOG,
      ctx: this.context
    };
    try {
      window.createWindow(config, (err: BusinessError, data) => {
        let errCode: number = err?.code;
        if (errCode) {
          console.error(`Failed to create the window. Cause code: ${err?.code}, message: ${err?.message}`);
          return;
        }
        if (!data) {
          console.error('data is null');
          return;
        }
        let token = want.parameters?.['ohos.ability.params.request.token'] as Property;
        let value = token.value as rpc.RemoteObject;
        data.bindDialogTarget(value, () => {
          console.info('Dialog Window Need Destroy.');
          }, (err: BusinessError) => {
          let errCode: number = err?.code;
          if (errCode) {
            console.error(`Failed to bind dialog target. Cause code: ${err?.code}, message: ${err?.message}`);
            return;
          }
          console.info('Succeeded in binding dialog target.');
        });
      });
    } catch (err) {
      console.error(`Failed to bind dialog target. Cause code: ${err?.code}, message: ${err?.message}`)
    }
  }
}
```

<a id="binddialogtarget-2"></a>

## bindDialogTarget

```TypeScript
bindDialogTarget(requestInfo: dialogRequest.RequestInfo, deathCallback: Callback<void>): Promise<void>
```

Binds the modal window to the target window. After the binding is successful, the target window cannot respond to user operations. In addition, a callback used to listen for modal window destruction events is added. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| requestInfo | [dialogRequest.RequestInfo](../../apis-ability-kit/arkts-apis/arkts-ability-dialogrequest-requestinfo-i.md) | Yes | **RequestInfo** of the target window. |
| deathCallback | [Callback](arkts-arkui-window-callback-i.md)&lt;void&gt; | Yes | Callback used to listen for modal window destruction events. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { dialogRequest, Want, ServiceExtensionAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class ServiceExtAbility extends ServiceExtensionAbility {
  onRequest(want: Want, startId: number) {
    console.info('onRequest');
    let config: window.Configuration = {
      name: 'test', windowType: window.WindowType.TYPE_DIALOG, ctx: this.context
    };
    try {
      window.createWindow(config, (err: BusinessError, data) => {
        const errCode: number = err?.code;
        if (errCode) {
          console.error(`Failed to create the window. Cause code: ${err?.code}, message: ${err?.message}`);
          return;
        }
        if (!data) {
          console.error('data is null');
          return;
        }
        let requestInfo = dialogRequest.getRequestInfo(want);
        let promise = data.bindDialogTarget(requestInfo, () => {
          console.info('Dialog Window Need Destroy.');
        });
        promise.then(() => {
          console.info('Succeeded in binding dialog target.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to bind dialog target. Cause code: ${err?.code}, message: ${err?.message}`);
        });
      });
    } catch (err) {
      console.error(`Failed to bind dialog target. Cause code: ${err?.code}, message: ${err?.message}`)
    }
  }
}
```

<a id="binddialogtarget-3"></a>

## bindDialogTarget

```TypeScript
bindDialogTarget(requestInfo: dialogRequest.RequestInfo, deathCallback: Callback<void>, callback: AsyncCallback<void>): void
```

Binds the modal window to the target window. After the binding is successful, the target window cannot respond to user operations. In addition, a callback used to listen for modal window destruction events is added. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| requestInfo | [dialogRequest.RequestInfo](../../apis-ability-kit/arkts-apis/arkts-ability-dialogrequest-requestinfo-i.md) | Yes | **RequestInfo** of the target window. |
| deathCallback | [Callback](arkts-arkui-window-callback-i.md)&lt;void&gt; | Yes | Callback used to listen for modal window destruction events. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { dialogRequest, Want, ServiceExtensionAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class ServiceExtAbility extends ServiceExtensionAbility {
  onRequest(want: Want, startId: number) {
    console.info('onRequest');
    let config: window.Configuration = {
      name: 'test', windowType: window.WindowType.TYPE_DIALOG, ctx: this.context
    };
    try {
      window.createWindow(config, (err: BusinessError, data) => {
        let errCode: number = err?.code;
        if (errCode) {
          console.error(`Failed to create the window. Cause code: ${err?.code}, message: ${err?.message}`);
          return;
        }
        if (!data) {
          console.error('data is null');
          return;
        }
        let requestInfo = dialogRequest.getRequestInfo(want);
        data.bindDialogTarget(requestInfo, () => {
          console.info('Dialog Window Need Destroy.');
          }, (err: BusinessError) => {
          let errCode: number = err?.code;
          if (errCode) {
            console.error(`Failed to bind dialog target. Cause code: ${err?.code}, message: ${err?.message}`);
            return;
          }
          console.info('Succeeded in binding dialog target.');
        });
      });
    } catch (err) {
      console.error(`Failed to bind dialog target. Cause code: ${err?.code}, message: ${err?.message}`)
    }
  }
}
```

## detachLayoutToParentWindow

```TypeScript
detachLayoutToParentWindow(): Promise<void>
```

Detach a first-level child window from the main window to cancel a fixed relative position. This API uses a promise to return the result.

> **NOTE:** 
> 
> - When the child window calls this API, the child window must be in the attached state.
> 
> - After detached by calling this API, the child window retains its position during attaching.You can drag the child window to change its size and position.
> 
> - After the detaching, calling APIs such as [moveWindowTo()](arkts-arkui-window-window-i.md#movewindowto) or [maximize()](arkts-arkui-window-window-i.md#maximize), and [setFollowParentWindowLayoutEnabled()](arkts-arkui-window-window-i.md#setfollowparentwindowlayoutenabled)to change the window position, or dragging and moving or dragging and resizing the child window through mouse or touch operations will take effect.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function detachLayoutToParentWindow cannot work correctly due to limited device capabilities. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: 1. Invalid window type. Only subwindows are supported; 2. Only level-1 subwindows are supported. |
| [1300010](../errorcode-window.md#1300010-unsupported-operation-in-the-current-window-mode) | The operation in the current window status is invalid. Possible cause: The subwindow is not attached to the main window. |

**Examples**

```TypeScript
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
        subWindow.detachLayoutToParentWindow().then(() => {
          console.info("Succeeded in detaching to the main window");
        }).catch((error: BusinessError) => {
          console.error(`detachLayoutToParentWindow failed. ${error.code} ${error.message}`);
        })
      }).catch((error: BusinessError) => {
        console.error(`createSubWindow failed. ${error.code} ${error.message}`);
      })
    });
  }
}
```

## getRotationLocked

```TypeScript
getRotationLocked(): boolean
```

Checks whether the [system window](../../../windowmanager/window-terminology.md#system-window) has its screen rotation locked. If this API is called by a non-system window, error code 1300029 is thrown.

**Since:** 22

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether rotation is currently locked for this system window. **true** if locked, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function getRotationLocked can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| 1300029 | This window type is invalid. Possible cause: A non-system window calls this API. |

**Examples**

```TypeScript
try {
  let locked = windowClass.getRotationLocked();
  console.info('Succeeded in getting rotation locked.');
} catch (exception) {
  console.error(`Failed to get rotation locked. Cause code: ${exception.code}, message: ${exception.message}`);
};
```

## getTransitionController

```TypeScript
getTransitionController(): TransitionController
```

Obtains the transition animation controller.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [TransitionController](arkts-arkui-window-transitioncontroller-i-sys.md) | Transition animation controller. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only system windows, global floating windows, and modal windows are supported. |

**Examples**

```TypeScript
let controller = windowClass.getTransitionController(); // Obtain the transition animation controller.
```

## hide

```TypeScript
hide (callback: AsyncCallback<void>): void
```

Hides this window. This API uses an asynchronous callback to return the result. This API takes effect only for a system window or an application child window.

**Since:** 7

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

windowClass.hide((err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to hide the window. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in hiding the window.');
});
```

<a id="hide-1"></a>

## hide

```TypeScript
hide(): Promise<void>
```

Hides this window. This API uses a promise to return the result. This API takes effect only for a system window or an application child window.

**Since:** 7

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = windowClass.hide();
promise.then(() => {
  console.info('Succeeded in hiding the window.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hide the window. Cause code: ${err.code}, message: ${err.message}`);
});
```

## hideNonSystemFloatingWindows

```TypeScript
hideNonSystemFloatingWindows(shouldHide: boolean, callback: AsyncCallback<void>): void
```

Sets whether to hide non-system floating windows (where [windowType](arkts-arkui-window-windowtype-e.md) is **TYPE_FLOAT**). This API uses an asynchronous callback to return the result.

A non-system floating window is a floating window created by a non-system application. By default, the main window of a system application can be displayed together with a non-system floating window. This means that the main window may be blocked by an upper-layer non-system floating window. If the **shouldHide** parameter is set to **true**, all non-system floating windows are hidden, so that the main window will never be blocked by a non- system floating window.

**Since:** 11

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shouldHide | boolean | Yes | Whether to hide non-system floating windows. **true** to hide, **false** otherwise. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // Load the page corresponding to the main window.
    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('Succeeded in loading the content.');
    });

    // Obtain the main window.
    let mainWindow: window.Window | undefined = undefined;
    windowStage.getMainWindow((err, data) => {
      if (err.code) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      mainWindow = data;
      console.info('Succeeded in obtaining the main window. Data: ' + JSON.stringify(data));

      let shouldHide = true;
      try {
        // Call hideNonSystemFloatingWindows with the callback parameter.
        mainWindow.hideNonSystemFloatingWindows(shouldHide, (err) => {
          if (err.code) {
            console.error(`Failed to hide the non-system floating windows. Cause code: ${err.code}, message: ${err.message}`);
            return;
          }
          console.info('Succeeded in hiding the non-system floating windows.');
        });
      } catch (exception) {
        console.error(`Failed to hide the non-system floating windows. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

<a id="hidenonsystemfloatingwindows-1"></a>

## hideNonSystemFloatingWindows

```TypeScript
hideNonSystemFloatingWindows(shouldHide: boolean): Promise<void>
```

Sets whether to hide non-system floating windows (where [windowType](arkts-arkui-window-windowtype-e.md) is **TYPE_FLOAT**). This API uses a promise to return the result.

A non-system floating window is a floating window created by a non-system application. By default, the main window of a system application can be displayed together with a non-system floating window. This means that the main window may be blocked by an upper-layer non-system floating window. If the **shouldHide** parameter is set to **true**, all non-system floating windows are hidden, so that the main window will never be blocked by a non- system floating window.

**Since:** 11

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shouldHide | boolean | Yes | Whether to hide non-system floating windows. **true** to hide, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // Load the page corresponding to the main window.
    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('Succeeded in loading the content.');
    });

    // Obtain the main window.
    let mainWindow: window.Window | undefined = undefined;
    windowStage.getMainWindow((err, data) => {
      if (err.code) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      mainWindow = data;
      console.info('Succeeded in obtaining the main window. Data: ' + JSON.stringify(data));

      let shouldHide = true;
      try {
        // Call hideNonSystemFloatingWindows to obtain a promise object.
        let promise = mainWindow.hideNonSystemFloatingWindows(shouldHide);
        promise.then(() => {
          console.info('Succeeded in hiding the non-system floating windows.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to hide the non-system floating windows. Cause code: ${err.code}, message: ${err.message}`);
        });
      } catch (exception) {
        console.error(`Failed to hide the non-system floating windows. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

## hideWithAnimation

```TypeScript
hideWithAnimation(callback: AsyncCallback<void>): void
```

Hides this window and plays an animation during the process. This API uses an asynchronous callback to return the result. This API takes effect only for a system window.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only system windows, global floating windows, and modal windows are supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

windowClass.hideWithAnimation((err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to hide the window with animation. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in hiding the window with animation.');
});
```

<a id="hidewithanimation-1"></a>

## hideWithAnimation

```TypeScript
hideWithAnimation(): Promise<void>
```

Hides this window and plays an animation during the process. This API uses a promise to return the result. This API takes effect only for a system window.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only system windows, global floating windows, and modal windows are supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = windowClass.hideWithAnimation();
promise.then(() => {
  console.info('Succeeded in hiding the window with animation.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hide the window with animation. Cause code: ${err.code}, message: ${err.message}`);
});
```

## isMainWindowFullScreenAcrossDisplays

```TypeScript
isMainWindowFullScreenAcrossDisplays(): Promise<boolean>
```

Checks whether the main window is in full-screen mode across multiple displays. This API uses a promise to return the result. It takes effect only for the main window and child windows.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result indicating whether the main window is in full- screen mode across multiple displays. **true** if yes, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let promise = windowClass.isMainWindowFullScreenAcrossDisplays();
  promise.then((data: boolean) => {
      console.info(`Succeeded in using isMainWindowFullScreenAcrossDisplays function. Data: ${data}`);
  }).catch((err: BusinessError) => {
      console.error(`Failed to use isMainWindowFullScreenAcrossDisplays function. code:${err.code}, message:${err.message}.`);
  });
} catch (exception) {
  console.error(`Failed to use isMainWindowFullScreenAcrossDisplays function. Cause code: ${exception.code}, message: ${exception.message}.`);
}
```

## off('mainWindowFullScreenAcrossDisplaysChanged')

```TypeScript
off(type: 'mainWindowFullScreenAcrossDisplaysChanged', callback?: Callback<boolean>): void
```

Unsubscribes from events indicating whether the main window is in full-screen mode across multiple displays.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'mainWindowFullScreenAcrossDisplaysChanged' | Yes | Event type. The value is fixed at **'mainWindowFullScreenAcrossDisplaysChanged'**, indicating changes in whether the main window is in full- screen mode across multiple displays. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;boolean&gt; | No | Callback used to return the result indicating whether the main window is in full-screen mode across multiple displays. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows and subwindows are supported. |

**Examples**

```TypeScript
const callback = (mainWindowFullScreenAcrossDisplaysChanged: boolean) => {
  // ...
}
try {
  // Enable listening through the on API.
  windowClass.on('mainWindowFullScreenAcrossDisplaysChanged', callback);
  // Disable the listening of a specified callback.
  windowClass.off('mainWindowFullScreenAcrossDisplaysChanged', callback);
  // Unregister all the callbacks that have been registered through on().
  windowClass.off('mainWindowFullScreenAcrossDisplaysChanged');
} catch (exception) {
  console.error(`Failed to unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## on('mainWindowFullScreenAcrossDisplaysChanged')

```TypeScript
on(type: 'mainWindowFullScreenAcrossDisplaysChanged', callback: Callback<boolean>): void
```

Subscribes to events indicating whether the main window is in full-screen mode across multiple displays.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'mainWindowFullScreenAcrossDisplaysChanged' | Yes | Event type. The value is fixed at **'mainWindowFullScreenAcrossDisplaysChanged'**, indicating changes in whether the main window is in full- screen mode across multiple displays. |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result indicating whether the main window is in full-screen mode across multiple displays. **true** if yes, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows and subwindows are supported. |

**Examples**

```TypeScript
const callback = (mainWindowFullScreenAcrossDisplaysChanged: boolean) => {
  console.info(`main window across displays changed. Data: ${mainWindowFullScreenAcrossDisplaysChanged}`);
}
try {
  windowClass.on('mainWindowFullScreenAcrossDisplaysChanged', callback);
} catch (exception) {
  console.error(`Failed to register callback. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## opacity

```TypeScript
opacity(opacity: number): void
```

Sets the opacity for this window. This API can be used only when you [customize an animation to be played during the display or hiding of a system window](../../../windowmanager/system-window-stage-sys.md#customizing-an-animation-to-be-played-during-the-display-or-hiding-of-a-system-window).

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| opacity | number | Yes | Opacity. The value is a floating-point number in the range [0.0, 1.0]. The value **0.0** means completely transparent, and **1.0** means completely opaque. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only system windows, global floating windows, and modal windows are supported. |

**Examples**

```TypeScript
try {
  windowClass.opacity(0.5);
} catch (exception) {
  console.error(`Failed to opacity. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## raiseAboveTarget

```TypeScript
raiseAboveTarget(windowId: number, callback: AsyncCallback<void>): void
```

Raises a child window above a target child window. This API uses an asynchronous callback to return the result.

Before calling this API, ensure that the child window to raise and the target child window have been created and [showWindow()](arkts-arkui-window-window-i.md#showwindow) has been successfully executed for each.

**Since:** 10

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| windowId | number | Yes | ID of the target child window, which is the value of **properties.id** in [properties](arkts-arkui-window-windowproperties-i.md) obtained through [getWindowProperties](arkts-arkui-window-window-i.md#getwindowproperties). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: Mandatory parameters are left unspecified. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. The window or target window is not shown. |
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
    let windowClass: window.Window;
    // Create a child window.
    try {
      windowStage.createSubWindow('testSubWindow').then((data) => {
        if (data == null) {
          console.error("Failed to create the subWindow. Cause: The data is empty");
          return;
        }
        windowClass = data;
        windowClass.showWindow().then(() => {
          // The windowClass must be obtained above the targetWindow.
          let targetWindow: window.Window = windowClass;
          let properties = targetWindow.getWindowProperties();
          let targetId = properties.id;
          windowClass.raiseAboveTarget(targetId, (err: BusinessError) => {
            if (err.code) {
              console.error(`Failed to raise the subWindow to target subWindow top. Cause code: ${err.code}, message: ${err.message}`);
              return;
            }
            console.info('Succeeded in raising the subWindow to target subWindow top.');
          });
        });
      });
    } catch (exception) {
      console.error(`Failed to create the subWindow. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

<a id="raiseabovetarget-1"></a>

## raiseAboveTarget

```TypeScript
raiseAboveTarget(windowId: number): Promise<void>
```

Raises a child window above a target child window. This API uses a promise to return the result.

Before calling this API, ensure that the child window to raise and the target child window have been created and [showWindow()](arkts-arkui-window-window-i.md#showwindow) has been successfully executed for each.

**Since:** 10

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| windowId | number | Yes | ID of the target child window, which is the value of **properties.id** in [properties](arkts-arkui-window-windowproperties-i.md) obtained through [getWindowProperties](arkts-arkui-window-window-i.md#getwindowproperties). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: Mandatory parameters are left unspecified. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. The window or target window is not shown. |
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
    let windowClass: window.Window;
    // Create a child window.
    try {
      windowStage.createSubWindow('testSubWindow').then((data) => {
        if (data == null) {
          console.error("Failed to create the subWindow. Cause: The data is empty");
          return;
        }
        windowClass = data;
        windowClass.showWindow().then(() => {
          // The windowClass must be obtained above the targetWindow.
          let targetWindow: window.Window = windowClass;
          let properties = targetWindow.getWindowProperties();
          let targetId = properties.id;
          windowClass.raiseAboveTarget(targetId).then(() => {
            console.info('Succeeded in raising the subWindow to target subWindow top.');
          }).catch((err: BusinessError) => {
            console.error(`Failed to raise the subWindow to target subWindow top. Cause code: ${err.code}, message: ${err.message}`);
          });
        });
      });
    } catch (exception) {
      console.error(`Failed to create the subWindow. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

## raiseMainWindowAboveTarget

```TypeScript
raiseMainWindowAboveTarget(windowId: number): Promise<void>
```

Moves the main window above another main window within the same application, with child windows following their parents' layer change. This API uses a promise to return the result.

This API can be called only by the main window of a system application.

You need to pass the ID of the target main window. Both the calling window and the target window must be in the same application process, displayed on the same physical screen, below the lock screen layer, not topmost, not modal, and have no application-modal child windows.

- If the application's main window or its child windows currently have focus, calling this API to lower the layer  
will cause the window to lose focus automatically, and the highest-layered application window will gain focus.  
- If the main window calls this API to move above the current focused window, the highest-layered window among  
the raised main window and its child windows will gain focus. If the main window calls this API without moving above the current focused window, the focus remains unchanged.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| windowId | number | Yes | ID of the target main window. The value is an integer. It is the value of **properties.id** in [properties](arkts-arkui-window-windowproperties-i.md) obtained through [getWindowProperties](arkts-arkui-window-window-i.md#getwindowproperties). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows are supported, and target must not be modal or topmost. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: 1. Invalid parameter range. 2. Invalid parameter length. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility, Want, StartOptions, AbilityConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}.`);
        return;
      }
      console.info('Succeeded in loading the content.');
      try {
        let want: Want = {
          abilityName: "RaiseMainWindowAbility",
          bundleName: "com.example.myapplication"
        };
        let options: StartOptions = {
          windowMode: AbilityConstant.WindowMode.WINDOW_MODE_FLOATING
        };
        this.context.startAbility(want, options);
      } catch (err) {
        console.error(`Failed to start the ability. Cause code: ${err.code}, message: ${err.message}.`);
      }
      setTimeout(async () => {
        let mainWindow: window.Window | null | undefined = windowStage.getMainWindowSync();
        let targetId: number | null | undefined = AppStorage.get('higher_window_id');
        mainWindow.raiseMainWindowAboveTarget(targetId).then(() => {
          console.info('Succeeded in raising main window above target.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to raise main window above target. Cause code: ${err.code}, message: ${err.message}.`);
        });
      }, 3000);
    });
  }
}
```

```TypeScript
// Create the RaiseMainWindowAbility.ets file in src/main/ets/raisemainwindowability.
import { UIAbility } from '@kit.AbilityKit';

export default class RaiseMainWindowAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    AppStorage.setOrCreate('higher_window_id', windowStage.getMainWindowSync().getWindowProperties().id);
    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}.`);
        return;
      }
      console.info('Succeeded in loading the content.');
    });
  }
}
```

```TypeScript
// module.json5
{
  "module": {
    "name": "entry",
    "type": "entry",
    "description": "$string:module_desc",
    "mainElement": "EntryAbility",
    "deviceTypes": [
      "phone",
      "tablet",
      "2in1"
    ],
    "deliveryWithInstall": true,
    "installationFree": false,
    "pages": "$profile:main_pages",
    "abilities": [
      {
        "name": "EntryAbility",
        "srcEntry": "./ets/entryability/EntryAbility.ets",
        "description": "$string:EntryAbility_desc",
        "icon": "$media:layered_image",
        "label": "$string:EntryAbility_label",
        "startWindowIcon": "$media:startIcon",
        "startWindowBackground": "$color:start_window_background",
        "exported": true,
        "skills": [
          {
            "entities": [
              "entity.system.home"
            ],
            "actions": [
              "action.system.home"
            ]
          }
        ]
      },
      {
        "name": "RaiseMainWindowAbility",
        "launchType": "multiton",
        "srcEntry": "./ets/entryability/EntryAbility.ets",
        "description": "$string:EntryAbility_desc",
        "icon": "$media:layered_image",
        "label": "$string:EntryAbility_label",
        "startWindowIcon": "$media:startIcon",
        "startWindowBackground": "$color:start_window_background",
        "exported": true,
        "skills": [
          {
            "entities": [
              "entity.system.home"
            ],
            "actions": [
              "action.system.home"
            ]
          }
        ]
      }
    ]
  }
}
```

## raiseToAppTop

```TypeScript
raiseToAppTop(callback: AsyncCallback<void>): void
```

Raises the application child window to the top layer of the application. This API uses an asynchronous callback to return the result.

Before calling this API, ensure that the child window has been created and [showWindow()](arkts-arkui-window-window-i.md#showwindow) has been successfully executed.

**Since:** 10

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
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
        subWindow.raiseToAppTop((err: BusinessError) => {
          const errCode: number = err.code;
          if (errCode) {
            console.error(`Failed to raise the window to app top. Cause code: ${err.code}, message: ${err.message}`);
            return;
          }
          console.info('Succeeded in raising the window to app top.');
        });
      });
    });
  }
}
```

## requestFocus

```TypeScript
requestFocus(isFocused: boolean): Promise<void>
```

Allows this window to proactively request to gain or lose focus. This API uses a promise to return the result. A value is returned as long as the API is successfully called. The return value does not indicate that the window has gained or lost focus. You can use [on('windowEvent')](arkts-arkui-window-window-i.md#onwindowevent) to listen for the focus status of the window.

When a focus request is sent, whether the window can successfully gain focus depends on its capability of being focused and its current visibility. To gain focus, the window must be capable of receiving focus and in a visible state (actively displayed and not hidden or destroyed).

Conversely, once a blur request is sent, the window will lose focus without any conditions.

**Since:** 13

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isFocused | boolean | Yes | Whether to gain or lose focus. **true** to gain focus, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, non-system application uses system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isFocused: boolean = true;
let promise = windowClass.requestFocus(isFocused);
promise.then(() => {
  console.info('Succeeded in requesting focus.');
}).catch((err: BusinessError) => {
  console.error(`Failed to request focus. Cause code: ${err.code}, message: ${err.message}`);
});
```

## rotate

```TypeScript
rotate(rotateOptions: RotateOptions): void
```

Sets the rotation parameters for this window. This API can be used only when you [customize an animation to be played during the display or hiding of a system window](../../../windowmanager/system-window-stage-sys.md#customizing-an-animation-to-be-played-during-the-display-or-hiding-of-a-system-window).

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rotateOptions | [RotateOptions](../arkts-components/arkts-arkui-common-comp-rotateoptions-i.md) | Yes | Rotation parameters to set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only system windows, global floating windows, and modal windows are supported. |

**Examples**

```TypeScript
let obj: window.RotateOptions = {
  x: 1.0,
  y: 1.0,
  z: 45.0,
  pivotX: 0.5,
  pivotY: 0.5
};
try {
  windowClass.rotate(obj);
} catch (exception) {
  console.error(`Failed to rotate. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## scale

```TypeScript
scale(scaleOptions: ScaleOptions): void
```

Sets the scale parameters for this window. This API can be used only when you [customize an animation to be played during the display or hiding of a system window](../../../windowmanager/system-window-stage-sys.md#customizing-an-animation-to-be-played-during-the-display-or-hiding-of-a-system-window).

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scaleOptions | [ScaleOptions](../arkts-components/arkts-arkui-common-comp-scaleoptions-i.md) | Yes | Scale parameters to set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only system windows, global floating windows, and modal windows are supported. |

**Examples**

```TypeScript
let obj: window.ScaleOptions = {
  x: 2.0,
  y: 1.0,
  pivotX: 0.5,
  pivotY: 0.5
};
try {
  windowClass.scale(obj);
} catch (exception) {
  console.error(`Failed to scale. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setBackdropBlur

```TypeScript
setBackdropBlur(radius: number): void
```

Blurs the background of this window.

The window background refers to the lower-layer area covered by the window, which is the same as the window size.

To make the blur effect visible, you must set the window background transparent by calling [setWindowBackgroundColor](arkts-arkui-window-window-i.md#setwindowbackgroundcolor).

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| radius | number | Yes | Radius of the blur. The value is a floating-point number greater than or equal to 0.0, in px. The value **0.0** means that the blur is disabled for the background of the window. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only system windows, global floating windows, and modal windows are supported. |

**Examples**

```TypeScript
try {
  windowClass.setWindowBackgroundColor('#00FFFFFF');
  windowClass.setBackdropBlur(4.0);
} catch (exception) {
  console.error(`Failed to set backdrop blur. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setBackdropBlurStyle

```TypeScript
setBackdropBlurStyle(blurStyle: BlurStyle): void
```

Sets the blur style for the background of this window.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blurStyle | [BlurStyle](../arkts-components/arkts-arkui-common-comp-blurstyle-e.md) | Yes | Blur style to set for the background of the window. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only system windows, global floating windows, and modal windows are supported. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
try {
  windowClass.setBackdropBlurStyle(window.BlurStyle.THIN);
} catch (exception) {
  console.error(`Failed to set backdrop blur style. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setBlur

```TypeScript
setBlur(radius: number): void
```

Blurs this window.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| radius | number | Yes | Radius of the blur. The value is a floating-point number greater than or equal to 0.0, in px. The value **0.0** means that the blur is disabled for the window. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only system windows, global floating windows, and modal windows are supported. |

**Examples**

```TypeScript
try {
  windowClass.setBlur(4.0);
} catch (exception) {
  console.error(`Failed to set blur. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setCornerRadius

```TypeScript
setCornerRadius(cornerRadius: number): void
```

Sets the radius of the rounded corners for this window.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cornerRadius | number | Yes | Radius of the rounded corners. The value is a floating-point number greater than or equal to 0.0, in px. The value **0.0** means that the window does not use rounded corners. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Invalid window type. Only subwindows and float windows are supported. |

**Examples**

```TypeScript
try {
  windowClass.setCornerRadius(4.0);
} catch (exception) {
  console.error(`Failed to set corner radius. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setDefaultDensityEnabled

```TypeScript
setDefaultDensityEnabled(enabled: boolean): void
```

Sets whether the window uses the default density of the current screen. In the stage model, you need to call this API after [loadContent()](arkts-arkui-window-window-i.md#loadcontent) or [setUIContent()](arkts-arkui-window-window-i.md#setuicontent).

If this API is not called, the default density is not used.

If this API, [setDefaultDensityEnabled(true)](arkts-arkui-window-windowstage-i.md#setdefaultdensityenabled), and [setCustomDensity](arkts-arkui-window-windowstage-i.md#setcustomdensity) are all called, the setting from the last called API will be applied.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to use the default density of the system. **true** to enable, **false** otherwise. When the default density is enabled, the window layout does not change with the system display size. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: The window is not created or destroyed. |

**Examples**

```TypeScript
try {
  windowClass.setDefaultDensityEnabled(true);
  console.info(`Succeeded in setting default density enabled`);
} catch (exception) {
  console.error(`Failed to set default density enabled. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setForbidSplitMove

```TypeScript
setForbidSplitMove(isForbidSplitMove: boolean, callback: AsyncCallback<void>): void
```

Sets whether the main window is forbidden to move in split-screen mode. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isForbidSplitMove | boolean | Yes | Whether the window is forbidden to move in split-screen mode. **true** if forbidden, **false** otherwise. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

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
      let isForbidSplitMove: boolean = true;
      try {
        windowClass.setForbidSplitMove(isForbidSplitMove, (err: BusinessError) => {
          const errCode: number = err.code;
          if (errCode) {
            console.error(`Failed to forbid window moving in split screen mode. Cause code: ${err.code}, message: ${err.message}`);
            return;
          }
          console.info('Succeeded in forbidding window moving in split screen mode.');
        });
      } catch (exception) {
        console.error(`Failed to forbid window moving in split screen mode. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

<a id="setforbidsplitmove-1"></a>

## setForbidSplitMove

```TypeScript
setForbidSplitMove(isForbidSplitMove: boolean): Promise<void>
```

Sets whether the main window is forbidden to move in split-screen mode. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isForbidSplitMove | boolean | Yes | Whether the window is forbidden to move in split-screen mode. **true** if forbidden, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

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
      let isForbidSplitMove: boolean = true;
      try {
        let promise = windowClass.setForbidSplitMove(isForbidSplitMove);
        promise.then(() => {
          console.info('Succeeded in forbidding window moving in split screen mode.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to forbid window moving in split screen mode. Cause code: ${err.code}, message: ${err.message}`);
        });
      } catch (exception) {
        console.error(`Failed to forbid window moving in split screen mode. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

## setHandwritingFlag

```TypeScript
setHandwritingFlag(enable: boolean): Promise<void>
```

Adds or deletes the handwriting flag for this window. After this flag is added, the window responds to stylus events but not touch events. This API uses a promise to return the result.

**Since:** 12

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to add or delete the flag. **true** to add, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let enable = true;
  let promise = windowClass.setHandwritingFlag(enable);
  promise.then(() => {
    console.info('Succeeded in setting handwriting flag of window.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set handwriting flag of window. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set handwriting flag of window. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setMainWindowRaiseByClickEnabled

```TypeScript
setMainWindowRaiseByClickEnabled(enable: boolean): Promise<void>
```

Sets whether to enable the main window to raise itself by click. This API uses a promise to return the result.

By default, clicking the main window raises both the main window and its associated child windows. Disabling this feature (by passing **false**) prevents the main window and its child windows from being raised when the main window is clicked, preserving their current state. However, clicking on a child window still raises both the child window and the main window together.

**Since:** 23

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable the main window to raise itself by click. **true** to enable, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. The window is not shown. |
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
    windowStage.getMainWindow().then((window: window.Window) => {
      // Load the page corresponding to the main window.
      windowStage.loadContent('pages/Index', (err) => {
        if (err.code) {
          console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in loading the content.');
        try {
          let raiseEnabled: boolean = false;
          let promise = window.setMainWindowRaiseByClickEnabled(raiseEnabled);
          promise.then(() => {
            console.info('Succeeded in disabling the raise-by-click function.');
          });
        } catch (err) {
          console.error(`Failed to disable the raise-by-click function. Cause code: ${err.code}, message: ${err.message}`);
        };
      });
    });
  }
}
```

## setRaiseByClickEnabled

```TypeScript
setRaiseByClickEnabled(enable: boolean, callback: AsyncCallback<void>): void
```

Sets whether to enable a child window to raise itself by click. This API uses an asynchronous callback to return the result.

Generally, when a user clicks a child window, the child window is displayed on the top. If the **enable** parameter is set to **false**, the child window is not displayed on the top when being clicked.

Before calling this API, ensure that the child window has been created and [showWindow()](arkts-arkui-window-window-i.md#showwindow) has been successfully executed.

**Since:** 10

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable a child window to raise itself by click. **true** to enable, **false** otherwise. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
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
          subWindow.setRaiseByClickEnabled(enabled, (err) => {
          if (err.code) {
            console.error(`Failed to disable the raise-by-click function. Cause code: ${err.code}, message: ${err.message}`);
            return;
          }
          console.info('Succeeded in disabling the raise-by-click function.');
          });
        } catch (err) {
          console.error(`Failed to disable the raise-by-click function. Cause code: ${err.code}, message: ${err.message}`);
        }
      });
    });
  }
}
```

## setRotationLocked

```TypeScript
setRotationLocked(locked: boolean): Promise<void>
```

Allows a [system window](../../../windowmanager/window-terminology.md#system-window) to lock or unlock its own screen-rotation behavior. When locked, the window's orientation remains unchanged. When unlocked, the window's orientation follows the main window's orientation, the system rotation-lock button, and the device's physical rotation sensor. If this API is called by a non-system window, error code 1300029 is thrown. This API uses a promise to return the result.

> **NOTE:** 
> 
> - If the main window sets the display orientation via [setPreferredOrientation()](arkts-arkui-window-window-i.md#setpreferredorientation-1)while rotation is locked, the window restores the last orientation request when brought to the foreground after unlocking.
> 
> - If the system window sets the display orientation via [setPreferredOrientation()](arkts-arkui-window-window-i.md#setpreferredorientation-1)while rotation is locked, the window restores the last orientation request when brought to the foreground with the highest level after unlocking. The rotation lock set by a lower-level window using **setRotationLocked**does not hinder the system window at a higher level to set the display orientation by calling [setPreferredOrientation()](arkts-arkui-window-window-i.md#setpreferredorientation-1).
> 
> - If the sensor orientation changes while rotation is locked, the last sensor orientation is restored after unlocking.
> 
> - If the application calls [setOrientation()](arkts-arkui-screen-screen-i-sys.md#setorientation)to set the screen orientation while rotation is locked, that screen?orientation setting is ignored.
> 
> - When rotation is unlocked, the application's display orientation is determined based on the main window's display orientation set via [setPreferredOrientation()](arkts-arkui-window-window-i.md#setpreferredorientation-1), the sensor orientation, and more. For details, see [Window Rotation Overview](../../../windowmanager/window-rotation.md#overview).
> 
> - The API does not affect the launch orientation set by the **orientation** under [**abilities** in the module.json5 file](../../../quick-start/module-configuration-file.md#abilities) of the application.

**Since:** 22

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locked | boolean | Yes | Whether to lock the rotation. **true** to lock, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function setRotationLocked can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| 1300029 | This window type is invalid. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let locked: boolean = true;
let promise = windowClass.setRotationLocked(locked);
promise.then(() => {
  console.info('set rotation locked success.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set rotation locked. Cause code: ${err.code}, message: ${err.message}`);
});
```

## setShadow

```TypeScript
setShadow(radius: number, color?: string, offsetX?: number, offsetY?: number): void
```

Sets the shadow for the window borders.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| radius | number | Yes | Radius of the shadow. The value is a floating-point number greater than or equal to 0.0, in px. The value **0.0** means that the shadow is disabled for the window borders. |
| color | string | No | Color of the shadow. The value is a hexadecimal RGB or ARGB color code and is case insensitive, for example, **#00FF00** or **#FF00FF00**. The default value is **'#000000'**. |
| offsetX | number | No | Offset of the shadow along the x-axis, in px. The value is a floating-point number, in px. The default value is **0.0**. |
| offsetY | number | No | Offset of the shadow along the y-axis, in px. The value is a floating-point number, in px. The default value is **0.0**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only system windows, global floating windows, modal windows and subwindows are supported. |

**Examples**

```TypeScript
try {
  windowClass.setShadow(4.0, '#FF00FF00', 2, 3);
} catch (exception) {
  console.error(`Failed to set shadow. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setSingleFrameComposerEnabled

```TypeScript
setSingleFrameComposerEnabled(enable: boolean): Promise<void>
```

Enables or disables the single-frame composer. This API uses a promise to return the result.

The single-frame composer is mainly used in scenarios that require extremely low interaction latency. It reduces the screen display latency of the rendering node.

**Since:** 11

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable the single-frame composer. **true** to enable, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let enable = true;
try {
  let promise = windowClass.setSingleFrameComposerEnabled(enable);
  promise.then(() => {
      console.info('Succeeded in enabling the single-frame-composer function.');
  }).catch((err: BusinessError) => {
      console.error(`Failed to enable the single-frame-composer function. code:${err.code}, message:${err.message}.`);
  });
} catch (exception) {
  console.error(`Failed to enable the single-frame-composer function. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setSnapshotSkip

```TypeScript
setSnapshotSkip(isSkip: boolean): void
```

Sets whether to ignore this window during screen capture, recording, or casting. This API is typically used in situations where you want to prevent screen capture, recording, or casting.

If you want the window to always be ignored during screen capture, recording, or casting while it is in the foreground, listen for window lifecycle changes using [on('windowEvent')](arkts-arkui-window-window-i.md#onwindowevent). Set **isSkip** to **false** when the window is in the background and **true** when it is in the foreground.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isSkip | boolean | Yes | Whether to ignore the window. The default value is **false**.<br>**true** to ignore, **false** otherwise.<br> |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |

**Examples**

```TypeScript
let isSkip: boolean = true;
try {
  windowClass.setSnapshotSkip(isSkip);
} catch (exception) {
  console.error(`Failed to Skip. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setTitleButtonVisible

```TypeScript
setTitleButtonVisible(isMaximizeVisible: boolean, isMinimizeVisible: boolean, isSplitVisible: boolean): void
```

Shows or hides the maximize, minimize, and split-screen buttons on the title bar of the main window.

This API takes effect only for the title bar buttons (maximize, minimize, and split-screen) that are available in the current scenario.

**Since:** 12

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isMaximizeVisible | boolean | Yes | Whether to show the maximize button. **true** to show, **false** otherwise. |
| isMinimizeVisible | boolean | Yes | Whether to show the minimize button. **true** to show, **false** otherwise. |
| isSplitVisible | boolean | Yes | Whether to show the split-screen button. **true** to show, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    // Load the page corresponding to the main window.
    windowStage.loadContent('pages/Index', (err) => {
      if (err?.code) {
        console.error(`Failed to load content. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      let mainWindow: window.Window | undefined = undefined;
      // Obtain the main window.
      windowStage.getMainWindow().then(
        data => {
          if (!data) {
            console.error('Failed to get main window.');
            return;
          }
          mainWindow = data;
          console.info('Succeeded in obtaining the main window. Data: ' + JSON.stringify(data));
          // Call setTitleButtonVisible to hide the maximize, minimize, and split-screen buttons on the title bar of the main window.
          mainWindow.setTitleButtonVisible(false, false, false);
        }
      ).catch((err: BusinessError) => {
          if (err.code) {
            console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
          }
      });
    });
  }
}
```

## setTopmost

```TypeScript
setTopmost(isTopmost: boolean): Promise<void>
```

Called by the main window to place the window above all the other windows. This API uses a promise to return the result.

**Since:** 12

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isTopmost | boolean | Yes | Whether to pin the main window on top. **true** to pin, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
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

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    // ...
    windowStage.getMainWindow().then((mainWindow) => {
      let isTopmost: boolean = true;
      mainWindow.setTopmost(isTopmost).then(() => {
        console.info('Succeeded in setting the main window to be topmost.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to set the main window to be topmost. Cause code: ${err.code}, message: ${err.message}`);
      });
    });
  }
}
```

## setWakeUpScreen

```TypeScript
setWakeUpScreen(wakeUp: boolean): void
```

Wakes up the screen.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| wakeUp | boolean | Yes | Whether to wake up the screen. **true** to wake up, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
let wakeUp: boolean = true;
try {
  windowClass.setWakeUpScreen(wakeUp);
} catch (exception) {
  console.error(`Failed to wake up the screen. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setWaterMarkFlag

```TypeScript
setWaterMarkFlag(enable: boolean, callback: AsyncCallback<void>): void
```

Adds or deletes the watermark flag for this window. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to add or delete the flag. **true** to add, **false** otherwise. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300008](../errorcode-window.md#1300008-display-device-exception) | The display device is abnormal. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let enable: boolean = true;
  windowClass.setWaterMarkFlag(enable, (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to set water mark flag of window. Cause code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in setting water mark flag of window.');
  });
} catch (exception) {
  console.error(`Failed to set water mark flag of window. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

<a id="setwatermarkflag-1"></a>

## setWaterMarkFlag

```TypeScript
setWaterMarkFlag(enable: boolean): Promise<void>
```

Adds or deletes the watermark flag for this window. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to add or delete the flag. **true** to add, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300008](../errorcode-window.md#1300008-display-device-exception) | The display device is abnormal. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let enable = true;
  let promise = windowClass.setWaterMarkFlag(enable);
  promise.then(() => {
    console.info('Succeeded in setting water mark flag of window.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set water mark flag of window. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set water mark flag of window. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

## setWindowMode

```TypeScript
setWindowMode(mode: WindowMode): Promise<void>
```

Sets the mode of the main window. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [WindowMode](arkts-arkui-window-windowmode-e-sys.md) | Yes | Indicate the mode of a window. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. Invalid window type. Only main windows are supported. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

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
      let mode = window.WindowMode.FULLSCREEN;
      try {
        let promise = windowClass.setWindowMode(mode);
        promise.then(() => {
          console.info('Succeeded in setting the window mode.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to set the window mode. Cause code: ${err.code}, message: ${err.message}`);
        });
      } catch (exception) {
        console.error(`Failed to set the window mode. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

<a id="setwindowmode-1"></a>

## setWindowMode

```TypeScript
setWindowMode(mode: WindowMode, callback: AsyncCallback<void>): void
```

Sets the mode of the main window. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [WindowMode](arkts-arkui-window-windowmode-e-sys.md) | Yes | Indicate the mode of a window. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. Invalid window type. Only main windows are supported. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

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
      let mode = window.WindowMode.FULLSCREEN;
      try {
        windowClass.setWindowMode(mode, (err: BusinessError) => {
          const errCode: number = err.code;
          if (errCode) {
            console.error(`Failed to set the window mode. Cause code: ${err.code}, message: ${err.message}`);
            return;
          }
          console.info('Succeeded in setting the window mode.');
        });
      } catch (exception) {
        console.error(`Failed to set the window mode. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}
```

## setWindowType

```TypeScript
setWindowType(type: WindowType): Promise<void>
```

Sets the type of this window. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [WindowType](arkts-arkui-window-windowtype-e.md) | Yes | Window type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let type = window.WindowType.TYPE_SYSTEM_ALERT;
let promise = windowClass.setWindowType(type);
promise.then(() => {
  console.info('Succeeded in setting the window type.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set the window type. Cause code: ${err.code}, message: ${err.message}`);
});
```

<a id="setwindowtype-1"></a>

## setWindowType

```TypeScript
setWindowType(type: WindowType, callback: AsyncCallback<void>): void
```

Sets the type of this window. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [WindowType](arkts-arkui-window-windowtype-e.md) | Yes | Window type. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let type = window.WindowType.TYPE_SYSTEM_ALERT;
windowClass.setWindowType(type, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to set the window type. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in setting the window type.');
});
```

## showWithAnimation

```TypeScript
showWithAnimation(callback: AsyncCallback<void>): void
```

Shows this window and plays an animation during the process. This API uses an asynchronous callback to return the result. This API takes effect only for a system window.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only system windows, global floating windows, and modal windows are supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

windowClass.showWithAnimation((err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to show the window with animation. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in showing the window with animation.');
});
```

<a id="showwithanimation-1"></a>

## showWithAnimation

```TypeScript
showWithAnimation(): Promise<void>
```

Shows this window and plays an animation during the process. This API uses a promise to return the result. This API takes effect only for a system window.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only system windows, global floating windows, and modal windows are supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = windowClass.showWithAnimation();
promise.then(() => {
  console.info('Succeeded in showing the window with animation.');
}).catch((err: BusinessError) => {
  console.error(`Failed to show the window with animation. Cause code: ${err.code}, message: ${err.message}`);
});
```

## startMovingWithOptions

```TypeScript
startMovingWithOptions(startMovingOptions?: StartMovingOptions): Promise<void>
```

Starts moving this window. The window moves along with the cursor only when this API is called in the callback function of onTouch, where the event type is TouchType.Down.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| startMovingOptions | [StartMovingOptions](arkts-arkui-window-startmovingoptions-i-sys.md) | No | The move configuration during drag-moving. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300001](../errorcode-window.md#1300001-repeated-operation) | Repeated operation. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type, main windows are not supported in non-free window mode. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: Invalid parameter range. |

**Examples**

```TypeScript
// Index.ets
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Blank('160')
          .color(Color.Red)
          .onTouch((event: TouchEvent) => {
            if (event.type == TouchType.Down) {
              let options: window.StartMovingOptions = {
                needFocused: true,
                avoidRect: {
                  left: 0,
                  top: 0,
                  width: 200,
                  height: 200
                }
              };
              try {
                windowClass.startMovingWithOptions(options)
                  .then(() => {
                    console.info('Succeeded in starting moving window.');
                  })
                  .catch((err: BusinessError) => {
                    console.error(`Failed to start moving. Cause code: ${err.code}, message: ${err.message}`);
                  });
              } catch (exception) {
                console.error(`Failed to start moving. Cause code: ${exception.code}, message: ${exception.message}`);
              }
            }
          })
      }
      .width('100%')
    }
    .height('100%')
    .width('100%')
  }
}
```

## translate

```TypeScript
translate(translateOptions: TranslateOptions): void
```

Sets the translation parameters for this window. This API can be used only when you [customize an animation to be played during the display or hiding of a system window](../../../windowmanager/system-window-stage-sys.md#customizing-an-animation-to-be-played-during-the-display-or-hiding-of-a-system-window).

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| translateOptions | [TranslateOptions](../arkts-components/arkts-arkui-common-comp-translateoptions-i.md) | Yes | Translation parameters. The unit is px. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only system windows, global floating windows, and modal windows are supported. |

**Examples**

```TypeScript
let obj: window.TranslateOptions = {
  x: 100.0,
  y: 0.0,
  z: 0.0
};
try {
  windowClass.translate(obj);
} catch (exception) {
  console.error(`Failed to translate. Cause code: ${exception.code}, message: ${exception.message}`);
}
```
