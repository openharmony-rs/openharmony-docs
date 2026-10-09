# @ohos.uiExtensionHost (System API)
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @Pakoo007-->
<!--Designer: @stupidb-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=4e5be674e287f8213e38343ff22d0403ff7ef1a3 translatedAt=2026-09-01T03:38:33.055Z pushedAt=2026-09-02T07:21:53.508Z -->

Intended only for the **UIExtensionComponent** that has process isolation requirements, the **uiExtensionHost** module provides APIs for obtaining the host application window information and information about the component itself.

> **NOTE**
>
> - No new feature will be added to this module. Related features will be provided in [uiExtension](js-apis-arkui-uiExtension.md).
>
> - The initial APIs of this module are supported since API version 11. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module are system APIs.

## Modules to Import

```ts
import { uiExtensionHost } from '@kit.ArkUI';
```

## UIExtensionHostWindowProxy

### Properties

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| properties          | [UIExtensionHostWindowProxyProperties](#uiextensionhostwindowproxyproperties) |  No  |  No  | Information about the **UIExtensionComponent** and the host application window.<br>**Note:** Due to architecture restrictions, avoid obtaining the value in [onSessionCreate](../apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md#onsessioncreate). Instead, when possible, obtain the value after receiving the [on('windowSizeChange')](#onwindowsizechange) callback. |

### getWindowAvoidArea

getWindowAvoidArea(type: window.AvoidAreaType): window.AvoidArea

Obtains the area where the host application window cannot be displayed, for example, the system bar area, notch, gesture area, and soft keyboard area.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | [window.AvoidAreaType](arkts-apis-window-e.md#avoidareatype7) | Yes| Type of the avoid area.|

**Return value**

| Type| Description|
| -------- | -------- |
| [window.AvoidArea](arkts-apis-window-i.md#avoidarea7) | Avoidance area for the content of the host window.|

**Error codes**

| ID| Error Message        |
| -------- | ---------------- |
| 401      | Parameter error. |

**Example**

```ts
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

### on('avoidAreaChange')

on(type: 'avoidAreaChange', callback: Callback<{ type: window.AvoidAreaType, area: window.AvoidArea }>): void

Subscribes to the event of changes to the area where the host application window cannot be displayed.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Parameters**

| Name  | Type  | Mandatory| Description                  |
| -------- | ------ | ---- | ---------------------- |
| type     | string | Yes  | Event type. The value is fixed at **'avoidAreaChange'**, indicating the event of changes to the area where the window cannot be displayed.|
| callback | [Callback](../apis-basic-services-kit/js-apis-base.md#callback)<{ type: [window.AvoidAreaType](arkts-apis-window-e.md#avoidareatype7), area: [window.AvoidArea](arkts-apis-window-i.md#avoidarea7) }> | Yes| Callback function that receives the information about the current avoid area. The **type** parameter indicates the type of the avoid area, and the **area** parameter indicates the avoid area for the content of the window.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Window Error Codes](errorcode-window.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| 1300002  | Abnormal state. Possible causes: <br> 1. The listening type is not supported. <br> 2. The listener has been registered. <br> 3. The UIExtension window proxy is abnormal. |

**Example**

```ts
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // Subscribe to the event indicating changes to the area where the window cannot be displayed.
    extensionHostWindow.on('avoidAreaChange', (info) => {
      console.info(`The avoid area of the host window is: ${JSON.stringify(info.area)}.`);
    });
  }
}
```

### off('avoidAreaChange')

off(type: 'avoidAreaChange', callback?: Callback<{ type: window.AvoidAreaType, area: window.AvoidArea }>): void

Unsubscribes from the event of changes to the area where the host application window cannot be displayed.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Parameters**

| Name  | Type  | Mandatory| Description                  |
| -------- | ------ | ---- | ---------------------- |
| type     | string | Yes  | Event type. The value is fixed at **'avoidAreaChange'**, indicating the event of changes to the area where the window cannot be displayed.|
| callback | [Callback](../apis-basic-services-kit/js-apis-base.md#callback)<{ type: [window.AvoidAreaType](arkts-apis-window-e.md#avoidareatype7), area: [window.AvoidArea](arkts-apis-window-i.md#avoidarea7) }> | No | Callback used for unsubscription. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Window Error Codes](errorcode-window.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| 1300002  | Abnormal state. Possible causes: <br> 1. The listening type is not supported. <br> 2. The listening type is not registered. <br> 3. The listener has not been registered. <br> 4. The UIExtension window proxy is abnormal. |

**Example**

```ts
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession} from '@kit.AbilityKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // Cancel all subscriptions to the event indicating changes to the area where the window cannot be displayed.
    extensionHostWindow.off('avoidAreaChange');
  }
}
```

### on('windowSizeChange')

on(type: 'windowSizeChange', callback: Callback<window.Size>): void

Subscribes to size change events of the component (**EmbeddedComponent** or **UIExtensionComponent**).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Parameters**

| Name  | Type                 | Mandatory| Description                  |
| -------- | --------------------- | ---- | ---------------------- |
| type     | string                | Yes  | Event type. The value is fixed at **'windowSizeChange'**, indicating the component (**EmbeddedComponent** or **UIExtensionComponent**) size change events.|
| callback | [Callback](../apis-basic-services-kit/js-apis-base.md#callback)<[window.Size](arkts-apis-window-i.md#size7)> | Yes  | Callback function that receives the current component size as the input parameter.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Window Error Codes](errorcode-window.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| 1300002  | Abnormal state. Possible causes: <br> 1. The listening type is not supported. <br> 2. The listener has been registered. <br> 3. The UIExtension window proxy is abnormal. |

**Example**

```ts
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // Subscribe to size change events of the component (EmbeddedComponent or UIExtensionComponent).
    extensionHostWindow.on('windowSizeChange', (size) => {
      console.info(`The size of the component is: ${JSON.stringify(size)}.`);
    });
  }
}
```

### off('windowSizeChange')

off(type: 'windowSizeChange', callback?: Callback<window.Size>): void

Unsubscribes from size change events of the component (**EmbeddedComponent** or **UIExtensionComponent**).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Parameters**

| Name  | Type                 | Mandatory| Description                  |
| -------- | --------------------- | ---- | ---------------------- |
| type     | string                | Yes  | Event type. The value is fixed at **'windowSizeChange'**, indicating the component (**EmbeddedComponent** or **UIExtensionComponent**) size change events.|
| callback | [Callback](../apis-basic-services-kit/js-apis-base.md#callback)<[window.Size](arkts-apis-window-i.md#size7)> | No | Callback used for unsubscription. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Window Error Codes](errorcode-window.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| 1300002  | Abnormal state. Possible causes: <br> 1. The listening type is not supported. <br> 2. The listening type is not registered. <br> 3. The listener has not been registered. <br> 4. The UIExtension window proxy is abnormal. |

**Example**

```ts
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession } from '@kit.AbilityKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // Unsubscribe from size change events of the component (EmbeddedComponent or UIExtensionComponent).
    extensionHostWindow.off('windowSizeChange');
  }
}
```

### hideNonSecureWindows

hideNonSecureWindows(shouldHide: boolean): Promise&lt;void&gt;

Sets whether to hide non-secure windows. This API uses a promise to return the result.
> **NOTE**
>
> - A non-secure window refers to any window that may obstruct the [EmbeddedComponent](arkui-ts/ts-container-embedded-component.md) or [UIExtensionComponent](arkui-ts/ts-container-ui-extension-component-sys.md) component, such as global floating windows, host subwindows, and dialog box windows created by the host window (excluding windows of these types created by system applications).
> - When using the **EmbeddedComponent** (or **UIExtensionComponent**) component to display sensitive operation prompts, you can choose to hide non-secure windows to protect the prompts from being obscured. When the **EmbeddedComponent** (or **UIExtensionComponent**) component is not displayed or is destroyed, the non-secure windows will be displayed again.
> - For PCs/2-in-1 devices, when **hideNonSecureWindows(true)** is called, global floating windows within the non-secure windows are not hidden.

**Required permissions**: ohos.permission.ALLOW_SHOW_NON_SECURE_WINDOWS

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Parameters**

| Name     | Type                     | Mandatory| Description      |
| ----------- | ------------------------- | ---- | ---------- |
| shouldHide  | boolean                   | Yes  | Whether to hide insecure windows. The value **true** means to hide insecure windows, and **false** means the opposite.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed. A non-system application calls a system API.<br>Applicable Versions: 12+ |
| 401      | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| 1300002  | Abnormal state. Possible causes: <br> 1. Permission denied. Interface caller does not have permission "ohos.permission.ALLOW_SHOW_NON_SECURE_WINDOWS". <br> 2. The UIExtension window proxy is abnormal.<br>Applicable Versions: 12+ |
| 1300003  | This window manager service works abnormally.<br>Applicable Versions: 12+ |

**Example**

```ts
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

### createSubWindowWithOptions<sup>12+</sup>

createSubWindowWithOptions(name: string, subWindowOptions: window.SubWindowOptions): Promise&lt;window.Window&gt;

Creates a subwindow for this **UIExtensionHostWindowProxy** instance. This API uses a promise to return the result.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**Device behavior differences**: When **isModal** in [subWindowOptions](arkts-apis-window-i.md#subwindowoptions11) is set to **true** and [modalityType](arkts-apis-window-e.md#modalitytype14) is set to **APPLICATION_MODALITY**, this API can be called properly on devices that support [freeform windows](../../windowmanager/window-terminology.md#freeform-window) and are in the freeform window state, and error code 801 is returned when this API is called on devices that support freeform windows but are not in the freeform window state or on devices that do not support freeform windows.

**Parameters**

| Name| Type  | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| name   | string | Yes   | Name of the subwindow, used to uniquely identify the subwindow. It is globally unique within the current process. |
| subWindowOptions | [window.SubWindowOptions](arkts-apis-window-i.md#subwindowoptions11) | Yes| Parameters used for creating the subwindow.|

**Return value**

| Type                            | Description                                            |
| -------------------------------- | ------------------------------------------------ |
| Promise&lt;[window.Window](arkts-apis-window-Window.md)&gt; | Promise used to return the subwindow created.|

**Error codes**

For details about the error codes, see [Window Error Codes](errorcode-window.md).

| ID| Error Message|
| ------- | ------------------------------ |
| 401 | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
| 1300002 | This window state is abnormal. Possible causes: 1. The window is not created or destroyed. 2. Internal task error. 3. The subWindow has been created and cannot be created again. 4. It is not allowed to create non-secure window when secure extension exists. |
| 1300035 | Creating a subwindow is not allowed in the current context. Possible cause: 1. An AgentUIExtensionAbility cannot create a subwindow. |

**Example**

```ts
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

### createSubWindowWithOptions<sup>22+</sup>

createSubWindowWithOptions(name: string, subWindowConfig: window.SubWindowOptions, followCreatorLifecycle: boolean): Promise&lt;window.Window&gt;

Creates a subwindow under this **UIExtensionHostWindowProxy** instance. You can set **followCreatorLifecycle** to determine whether the subwindow follows the lifecycle of the component (**EmbeddedComponent** or **UIExtensionComponent**). This API uses a promise to return the result.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**Device behavior differences**: When **isModal** in **subWindowConfig** is set to **true** and [modalityType](arkts-apis-window-e.md#modalitytype14) is set to **APPLICATION_MODALITY**, this API can be called properly on devices that support [freeform windows](../../windowmanager/window-terminology.md#freeform-window) and in the freeform window state, and error code 801 is returned when this API is called on devices that support freeform windows but are not in the freeform window state or on devices that do not support freeform windows.

**Parameters**

| Name| Type  | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| name   | string | Yes   | Name of the subwindow, used to uniquely identify the subwindow. It is globally unique within the current process. |
| subWindowConfig | [window.SubWindowOptions](arkts-apis-window-i.md#subwindowoptions11) | Yes| Parameters used for creating the subwindow.|
| followCreatorLifecycle | boolean | Yes   | Whether the lifecycle of the subwindow stays synchronized with the component (**EmbeddedComponent** or **UIExtensionComponent**). The value **true** means that the subwindow is hidden when the component is hidden and shown when the component is shown; the value **false** means that the visibility of the subwindow does not follow the component.|

**Return value**

| Type                            | Description                                            |
| -------------------------------- | ------------------------------------------------ |
| Promise&lt;[window.Window](arkts-apis-window-Window.md)&gt; | Promise used to return the subwindow created.|

**Error codes**

For details about the error codes, see [Window Error Codes](errorcode-window.md).

| ID| Error Message|
| ------- | ------------------------------ |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
| 1300002 | This window state is abnormal. Possible causes: 1. The window is not created or destroyed. 2. Internal task error. 3. The subWindow has been created and cannot be created again. 4. It is not allowed to create non-secure window when secure extension exists. |
| 1300035 | Creating a subwindow is not allowed in the current context. Possible cause: 1. An AgentUIExtensionAbility cannot create a subwindow. |

**Example**

```ts
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

### setWaterMarkFlag<sup>12+</sup>

setWaterMarkFlag(enable: boolean): Promise&lt;void&gt;

Adds or deletes the watermark flag for this window. This API uses a promise to return the result.
> **NOTE**
>
> With the watermark flag added, the watermark is applied on the full screen when the window is in the foreground, regardless of whether the window is displayed in full screen, floating, and split screen mode.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Parameters**

| Name| Type    | Mandatory| Description                                           |
| ------ | ------- | --- | ------------------------------------------------ |
| enable | boolean | Yes  | Whether to add or delete the flag. The value **true** means to add the watermark flag, and **false** means to delete the watermark flag.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

| ID| Error Message|
| ------- | ---------------------------------------------- |
| 1300002 | The UIExtension window proxy is abnormal.      |
| 1300003 | This window manager service works abnormally.  |
| 1300008 | The display device is abnormal. |

**Example**

```ts
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
### hidePrivacyContentForHost<sup>13+</sup>

hidePrivacyContentForHost(shouldHide: boolean): Promise&lt;void&gt;

Sets whether to enable privacy protection for the UIExtension component during non-system screenshots. This API uses a promise to return the result.

> **NOTE**
>
> After privacy protection for screenshot content is enabled, neither the window screenshot API [window.snapshot](arkts-apis-window-Window.md#snapshot9) nor the component screenshot API [UIContext.getComponentSnapshot](arkts-apis-uicontext-uicontext.md#getcomponentsnapshot12) will capture the content of the current component (excluding subwindows created under this component).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Parameters**

| Name| Type    | Mandatory| Description                                           |
| ------ | ------- | --- | ------------------------------------------------ |
| shouldHide | boolean | Yes | Whether to enable privacy protection for screenshot content. The value **true** means to enable, and **false** means to disable. |

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Window Error Codes](errorcode-window.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| 1300002  | Abnormal state. Possible causes: <br> 1. The UIExtension window proxy is abnormal. <br> 2. Not the UIExtensionAbility process calling.                    |

**Example**

```ts
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

## UIExtensionHostWindowProxyProperties

Defines information about the host application window and **UIExtensionComponent**.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

| Name                        | Type       | Read-Only | Optional   | Description                            |
| ------------------------------ | ----------- | --------------- | ----------------- | -------------------------------- |
| uiExtensionHostWindowProxyRect | [window.Rect](arkts-apis-window-i.md#rect7) | No | No | Position and size of the **UIExtensionComponent**. |

## Example

This example shows how to use all the available APIs in the UIExtensionAbility. The bundle name of the sample application, which requires a system signature, is **com.example.uiextensiondemo**, and the UIExtensionAbility to start is **ExampleUIExtensionAbility**.

- The EntryAbility (UIAbility) of the sample application loads the **pages/Index.ets** file, whose content is as follows:

  ```ts
  // The UIAbility loads pages/Index.ets when started.
  import { Want } from '@kit.AbilityKit';

  @Entry
  @Component
  struct Index {
    @State message: string = 'Message: ';
    private want: Want = {
      bundleName: 'com.example.uiextensiondemo',
      abilityName: 'ExampleUIExtensionAbility',
      parameters: {
        'ability.want.params.uiExtensionType': 'sys/commonUI'
      }
    }

    build() {
      Row() {
        Column() {
          Text(this.message).fontSize(30)
          UIExtensionComponent(this.want)
            .width('100%')
            .height('90%')
        }
        .width('100%')
      }
      .height('100%')
    }
  }
  ```

- The UIExtensionAbility to start by the **UIExtensionComponent** is implemented in the **ets/extensionAbility/ExampleUIExtensionAbility** file. The file content is as follows:

  ```ts
  import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';

  const TAG: string = '[ExampleUIExtensionAbility]';
  export default class ExampleUIExtensionAbility extends UIExtensionAbility {
    onCreate() {
      console.info(TAG, `onCreate`);
    }

    onForeground() {
      console.info(TAG, `onForeground`);
    }

    onBackground() {
      console.info(TAG, `onBackground`);
    }

    onDestroy() {
      console.info(TAG, `onDestroy`);
    }

    onSessionCreate(want: Want, session: UIExtensionContentSession) {
      console.info(TAG, `onSessionCreate, want: ${JSON.stringify(want)}`);
      let param: Record<string, UIExtensionContentSession> = {
        'session': session
      };
      let storage: LocalStorage = new LocalStorage(param);
      session.loadContent('pages/extension', storage);
    }
  }
  ```

- The entry page file of the UIExtensionAbility is **pages/extension.ets**, whose content is as follows:

  ```ts
  import { UIExtensionContentSession } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { uiExtensionHost, window } from '@kit.ArkUI';

  @Entry()
  @Component
  struct Extension {
    @State message: string = 'UIExtensionAbility Index';
    private storage: LocalStorage | undefined = this.getUIContext()?.getSharedLocalStorage();
    private session: UIExtensionContentSession | undefined = this.storage?.get<UIExtensionContentSession>('session');
    private extensionHostWindow: uiExtensionHost.UIExtensionHostWindowProxy | undefined = this.session?.getUIExtensionHostWindowProxy();
    private subWindow: window.Window | undefined = undefined;

    aboutToAppear(): void {
      this.extensionHostWindow?.on('windowSizeChange', (size) => {
          console.info(`size = ${JSON.stringify(size)}`);
      });
      this.extensionHostWindow?.on('avoidAreaChange', (info) => {
          console.info(`type = ${JSON.stringify(info.type)}, area = ${JSON.stringify(info.area)}`);
      });
      this.extensionHostWindow?.hideNonSecureWindows(true)?.then(() => {
        console.info(`Succeeded in hiding the non-secure windows.`);
      }).catch((err: BusinessError) => {
        console.error(`Failed to hide the non-secure windows. Code: ${err.code}, message: ${err.message}`);
      });
      this.extensionHostWindow?.hidePrivacyContentForHost(true)?.then(() => {
        console.info(`Succeeded in enabling privacy protection for non-system screenshots.`);
      }).catch((err: BusinessError) => {
        console.error(`Failed to enable privacy protection for non-system screenshots. Code: ${err.code}, message: ${err.message}`);
      });
    }

    aboutToDisappear(): void {
      this.extensionHostWindow?.off('windowSizeChange');
      this.extensionHostWindow?.off('avoidAreaChange');
      this.extensionHostWindow?.hideNonSecureWindows(false)?.then(() => {
        console.info(`Succeeded in showing the non-secure windows.`);
      }).catch((err: BusinessError) => {
        console.error(`Failed to show the non-secure windows. Code: ${err.code}, message: ${err.message}`);
      });
    }

    build() {
      Column() {
        Text(this.message)
          .fontSize(20)
          .fontWeight(FontWeight.Bold)
        Button('Obtain Component Size').width('90%').margin({top: 5, bottom: 5}).fontSize(16).onClick(() => {
          let rect = this.extensionHostWindow?.properties.uiExtensionHostWindowProxyRect;
          console.info(`EmbeddedComponent position and size info: ${JSON.stringify(rect)}`);
        })
        Button('Obtain System Avoid Area Info').width('90%').margin({top: 5, bottom: 5}).fontSize(16).onClick(() => {
          let avoidArea: window.AvoidArea | undefined = this.extensionHostWindow?.getWindowAvoidArea(window.AvoidAreaType.TYPE_SYSTEM);
          console.info(`System avoid area: ${JSON.stringify(avoidArea)}`);
        })
        Button('Create Subwindow').width('90%').margin({top: 5, bottom: 5}).fontSize(16).onClick(() => {
          let subWindowOpts: window.SubWindowOptions = {
            title: 'This is a subwindow',
            decorEnabled: true
          };
          this.extensionHostWindow?.createSubWindowWithOptions('subWindowForHost', subWindowOpts)
            .then((subWindow: window.Window) => {
              this.subWindow = subWindow;
              this.subWindow.loadContent('pages/Index', this.storage, (err, data) => {
                if (err && err.code) {
                  return;
                }
                this.subWindow?.resize(300, 300, (err, data) => {
                  if (err && err.code) {
                    return;
                  }
                  this.subWindow?.moveWindowTo(100, 100, (err, data) => {
                    if (err && err.code) {
                      return;
                    }
                    this.subWindow?.showWindow((err, data) => {
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
        })
      }.width('100%').height('100%')
    }
  }
  ```

- Add an item to **extensionAbilities** in the **module.json5** file of the sample application. The details are as follows:
  ```json
  {
    "name": "ExampleUIExtensionAbility",
    "srcEntry": "./ets/extensionAbility/ExampleUIExtensionAbility.ets",
    "type": "sys/commonUI"
  }
  ```
