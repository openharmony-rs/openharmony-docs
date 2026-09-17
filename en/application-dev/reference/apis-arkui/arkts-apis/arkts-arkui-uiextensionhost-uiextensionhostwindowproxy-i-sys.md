# UIExtensionHostWindowProxy (System API)

Transition Controller

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { uiExtensionHost } from '@kit.ArkUI';
```

## createSubWindowWithOptions

```TypeScript
createSubWindowWithOptions(name: string, subWindowOptions: window.SubWindowOptions): Promise<window.Window>
```

Creates a subwindow for this **UIExtensionHostWindowProxy** instance. This API uses a promise to return the result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the subwindow. |
| subWindowOptions | [window.SubWindowOptions](arkts-arkui-window-subwindowoptions-i.md) | Yes | Parameters used for creating the subwindow. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[window.Window](arkts-arkui-window-window-i.md)&gt; | Promise used to return the subwindow created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible causes: 1. The window is not created or destroyed. 2. Internal task error. 3. The subWindow has been created and cannot be created again. 4. It is not allowed to create non-secure window when secure extension exists. |
| 1300035 | Creating a subwindow is not allowed in the current context. Possible cause: 1. An AgentUIExtensionAbility cannot create a subwindow. |

**Examples**

```TypeScript
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    const subWindowOpts: window.SubWindowOptions = {
      title: 'This is a subwindow',
      decorEnabled: true
    };
    // Create a subwindow.
    extensionHostWindow.createSubWindowWithOptions('subWindowForHost', subWindowOpts)
      .then((subWindow: window.Window) => {
        subWindow.setUIContent('pages/Index', (err, data) => {
          if (err && err.code) {
            return;
          }
          subWindow?.resize(300, 300, (err, data) => {
            if (err && err.code) {
              return;
            }
            subWindow?.moveWindowTo(100, 100, (err, data) => {
              if (err && err.code) {
                return;
              }
              subWindow?.showWindow((err, data) => {
                if (err && err.code) {
                  console.error(`Failed to show the subwindow. Code: ${err.code}, message: ${err.message}`);
                } else {
                  console.info(`The subwindow has been shown!`);
                }
              });
            });
          });
        });
      }).catch((error: BusinessError) => {
        console.error(`Create subwindow failed. Code: ${error.code}, message: ${error.message}`);
      });
  }
}
```

```TypeScript
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    const subWindowConfig: window.SubWindowOptions = {
      title: 'This is a subwindow',
      decorEnabled: true
    };
    // Create a subwindow.
    extensionHostWindow.createSubWindowWithOptions('subWindowForHost', subWindowConfig, true)
      .then((subWindow: window.Window) => {
        subWindow.setUIContent('pages/Index', (err, data) => {
          if (err && err.code) {
            return;
          }
          subWindow?.resize(300, 300, (err, data) => {
            if (err && err.code) {
              return;
            }
            subWindow?.moveWindowTo(100, 100, (err, data) => {
              if (err && err.code) {
                return;
              }
              subWindow?.showWindow((err, data) => {
                if (err && err.code) {
                  console.error(`Failed to show the subwindow. Code: ${err.code}, message: ${err.message}`);
                } else {
                  console.info(`The subwindow has been shown!`);
                }
              });
            });
          });
        });
      }).catch((error: BusinessError) => {
        console.error(`Create subwindow failed. Code: ${error.code}, message: ${error.message}`);
      });
  }
}
```

## createSubWindowWithOptions

```TypeScript
createSubWindowWithOptions(name: string, subWindowConfig: window.SubWindowOptions,
        followCreatorLifecycle: boolean): Promise<window.Window>
```

Create subwindow.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the subwindow. |
| subWindowConfig | [window.SubWindowOptions](arkts-arkui-window-subwindowoptions-i.md) | Yes | Configuration parameters for creating the subwindow. |
| followCreatorLifecycle | boolean | Yes | Whether the lifecycle of the subwindow follows creator of subwindow. If true, when the creator goes to background, the subwindow will also go to background, when the creator returns to foreground, the subwindow will also return to foreground. If false, the subwindow will not change when the creator goes to background or returns to foreground. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[window.Window](arkts-arkui-window-window-i.md)&gt; | Promise used to return the subwindow. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible causes: 1. The window is not created or destroyed. 2. Internal task error. 3. The subWindow has been created and cannot be created again. 4. It is not allowed to create non-secure window when secure extension exists. |
| 1300035 | Creating a subwindow is not allowed in the current context. Possible cause: 1. An AgentUIExtensionAbility cannot create a subwindow. |

**Examples**

See [createSubWindowWithOptions](#createsubwindowwithoptions)

## getWindowAvoidArea

```TypeScript
getWindowAvoidArea(type: window.AvoidAreaType): window.AvoidArea
```

Obtains the area where this window cannot be displayed, for example, the system bar area, notch, gesture area, and soft keyboard area.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [window.AvoidAreaType](arkts-arkui-window-avoidareatype-e.md) | Yes | Type of the avoidance area. |

**Return value:**

| Type | Description |
| --- | --- |
| [window.AvoidArea](arkts-arkui-window-avoidarea-i.md) | Avoidance area for the content of the host window. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |

**Examples**

```TypeScript
// ExtensionProvider.ets

import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // Obtain the information about the area where the window cannot be displayed.
    const avoidArea = extensionHostWindow.getWindowAvoidArea(window.AvoidAreaType.TYPE_SYSTEM);
    console.info(`avoidArea: ${JSON.stringify(avoidArea)}`);
  }
}
```

## hideNonSecureWindows

```TypeScript
hideNonSecureWindows(shouldHide: boolean): Promise<void>
```

Sets whether to hide non-secure windows. This API uses a promise to return the result.

> **NOTE:** 
> 
> - A non-secure window refers to any window that may obstruct the EmbeddedComponent or UIExtensionComponent, such as global floating windows , host subwindows, and dialog box windows created by the host application (excluding windows of these types created by system applications).
> 
> - When using the **EmbeddedComponent** or **UIExtensionComponent** to display sensitive information, call this API to hide non-secure windows and prevent information obstruction. Hidden non-secure windows will reappear when the **EmbeddedComponent** or **UIExtensionComponent** is hidden or destroyed.
> 
> - On PCs/2-in-1 devices, global floating windows within non-secure windows remain visible when
> **hideNonSecureWindows(true)** is called.

**Since:** 11

**Required permissions:** 
- API version 12 and later: ohos.permission.ALLOW_SHOW_NON_SECURE_WINDOWS
- API version 11: N/A

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shouldHide | boolean | Yes | Whether to hide insecure windows. The value **true** means to hide insecure windows, and **false** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | Abnormal state. Possible causes: 1. Permission denied. Interface caller does not have permission "ohos.permission.ALLOW_SHOW_NON_SECURE_WINDOWS". 2. The UIExtension window proxy is abnormal.<br>**Applicable version:** 12 and later |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
// ExtensionProvider.ets

import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // Hide non-secure windows.
    extensionHostWindow.hideNonSecureWindows(true).then(() => {
      console.info(`Succeeded in hiding the non-secure windows.`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to hide the non-secure windows. Code: ${err.code}, message: ${err.message}`);
    });
  }
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // Unhide non-secure windows.
    extensionHostWindow.hideNonSecureWindows(false).then(() => {
      console.info(`Succeeded in showing the non-secure windows.`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to show the non-secure windows. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## hidePrivacyContentForHost

```TypeScript
hidePrivacyContentForHost(shouldHide: boolean): Promise<void>
```

Sets whether to enable privacy protection for the UIExtension component during non-system screenshots. This API uses a promise to return the result.

> **NOTE:** 
> 
> When privacy protection is enabled, neither
> window.snapshot nor
> [UIContext.getComponentSnapshot](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getcomponentsnapshot12)
> will capture the content of the current component (excluding subwindows created under this component).

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shouldHide | boolean | Yes | Whether to enable privacy protection for screenshots. The value **true** means to enable privacy protection for screenshots, and **false** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | Abnormal state. Possible causes: 1. The UIExtension window proxy is abnormal. 2. Not the UIExtensionAbility process calling. |

**Examples**

```TypeScript
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // Enable privacy protection for screenshots.
    extensionHostWindow.hidePrivacyContentForHost(true).then(() => {
      console.info(`Succeeded in enabling privacy protection for non-system screenshots.`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to enable privacy protection for non-system screenshots. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## off('avoidAreaChange')

```TypeScript
off(type: 'avoidAreaChange', callback?: Callback<{ type: window.AvoidAreaType, area: window.AvoidArea }>): void
```

Unsubscribes from events of system avoidance area changes.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'avoidAreaChange' | Yes | Event type. The value is fixed at **'avoidAreaChange'**, indicating the event of changes to the area where the window cannot be displayed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[{ type: window.AvoidAreaType](arkts-arkui-window-avoidareatype-e.md), area: window.AvoidArea }&gt; | No | Callback used for unsubscription. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | Abnormal state. Possible causes: 1. The listening type is not supported. 2. The listening type is not registered. 3. The listener has not been registered. 4. The UIExtension window proxy is abnormal. |

## off('windowSizeChange')

```TypeScript
off(type: 'windowSizeChange', callback?: Callback<window.Size>): void
```

Unsubscribes from size change events of the component (**EmbeddedComponent** or **UIExtensionComponent**).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'windowSizeChange' | Yes | Event type. The value is fixed at **'windowSizeChange'**, indicating the component (**EmbeddedComponent** or **UIExtensionComponent**) size change events. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[window.Size](arkts-arkui-window-size-i.md)&gt; | No | Callback used to return the size of the current component (**EmbeddedComponent** or **UIExtensionComponent**). If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | Abnormal state. Possible causes: 1. The listening type is not supported. 2. The listening type is not registered. 3. The listener has not been registered. 4. The UIExtension window proxy is abnormal. |

## on('avoidAreaChange')

```TypeScript
on(type: 'avoidAreaChange', callback: Callback<{ type: window.AvoidAreaType, area: window.AvoidArea }>): void
```

Subscribes to events of system avoidance area changes.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'avoidAreaChange' | Yes | Event type. The value is fixed at **'avoidAreaChange'**, indicating the event of changes to the area where the window cannot be displayed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[{ type: window.AvoidAreaType](arkts-arkui-window-avoidareatype-e.md), area: window.AvoidArea }&gt; | Yes | Callback function that receives the information about the current avoidance area. The **type** parameter indicates the type of the avoidance area, and the **area** parameter indicates the avoidance area for the content of the window. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | Abnormal state. Possible causes: 1. The listening type is not supported. 2. The listener has been registered. 3. The UIExtension window proxy is abnormal. |

## on('windowSizeChange')

```TypeScript
on(type: 'windowSizeChange', callback: Callback<window.Size>): void
```

Subscribes to size change events of the component (**EmbeddedComponent** or **UIExtensionComponent**).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'windowSizeChange' | Yes | Event type. The value is fixed at **'windowSizeChange'**, indicating the component (**EmbeddedComponent** or **UIExtensionComponent**) size change events. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[window.Size](arkts-arkui-window-size-i.md)&gt; | Yes | Callback function that receives the current component size as the input parameter. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | Abnormal state. Possible causes: 1. The listening type is not supported. 2. The listener has been registered. 3. The UIExtension window proxy is abnormal. |

## setWaterMarkFlag

```TypeScript
setWaterMarkFlag(enable: boolean): Promise<void>
```

Adds or deletes the watermark flag for this window. This API uses a promise to return the result.

> **NOTE:** 
> 
> With the watermark flag added, the watermark is applied on the full screen when the window is in the foreground
> , regardless of whether the window is displayed in full screen, floating, and split screen mode.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to add or delete the flag. The value **true** means to add the watermark flag, and **false** means to delete the watermark flag. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | The UIExtension window proxy is abnormal. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300008](../errorcode-window.md#1300008-display-device-exception) | The display device is abnormal. |

**Examples**

```TypeScript
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // Add the watermark flag.
    extensionHostWindow.setWaterMarkFlag(true).then(() => {
      console.info(`Succeeded in setting water mark flag of window.`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to set water mark flag of window. Code: ${err.code}, message: ${err.message}`);
    });
  }
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // Delete the watermark flag.
    extensionHostWindow.setWaterMarkFlag(false).then(() => {
      console.info(`Succeeded in deleting water mark flag of window.`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to delete water mark flag of window. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## properties

```TypeScript
properties: UIExtensionHostWindowProxyProperties
```

Information about the host application window and the **UIExtensionComponent**.

Note: Due to architecture restrictions, avoid obtaining the value in [onSessionCreate](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensionability-uiextensionability-c.md#onsessioncreate). Instead, when possible, obtain the value after receiving the [on('windowSizeChange')](#onwindowsizechange) callback.

**Type:** [UIExtensionHostWindowProxyProperties](arkts-arkui-uiextensionhost-uiextensionhostwindowproxyproperties-i-sys.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
