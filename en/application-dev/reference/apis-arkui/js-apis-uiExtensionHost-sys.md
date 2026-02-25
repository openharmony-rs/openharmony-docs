# @ohos.uiExtensionHost (System API)
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @chbchb12-->
<!--Designer: @stupidb-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

Intended only for the **UIExtensionComponent** that has process isolation requirements, the **uiExtensionHost** module provides APIs for obtaining the host application window information and information about the component itself.

> **NOTE**
>
> No new function will be added to this module. Related functions will be provided in the [uiExtension](js-apis-arkui-uiExtension.md) interface.
>
> The initial APIs of this module are supported since API version 11. Updates will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { uiExtensionHost } from '@kit.ArkUI';
```

## UIExtensionHostWindowProxy

### Properties

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**System API**: This is a system API.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| properties          | [UIExtensionHostWindowProxyProperties](#uiextensionhostwindowproxyproperties) |  No |  No | Information about the host application window and the **UIExtensionComponent**.<br>Note: Due to architecture restrictions, avoid obtaining the value in [onSessionCreate](../apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md#onsessioncreate). Instead, when possible, obtain the value after receiving the [on('windowSizeChange')](../apis-arkui/js-apis-uiExtensionHost-sys.md#onwindowsizechange) callback.|

### getWindowAvoidArea

getWindowAvoidArea(type: window.AvoidAreaType): window.AvoidArea

Obtains the area where this window cannot be displayed, for example, the system bar area, notch, gesture area, and soft keyboard area.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | [window.AvoidAreaType](arkts-apis-window-e.md#avoidareatype7) | Yes| Type of the area.|

**Return value**

| Type| Description|
| -------- | -------- |
| [window.AvoidArea](arkts-apis-window-i.md#avoidarea7) | Area where the window cannot be displayed.|

**Error codes**

| ID| Error Message        |
| -------- | ---------------- |
| 401      | Parameter error. |

**Example**

```ts
// ExtensionProvider.ts

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

Subscribes to the event indicating changes to the area where the window cannot be displayed.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**System API**: This is a system API.

**Parameters**

| Name  | Type  | Mandatory| Description                  |
| -------- | ------ | ---- | ---------------------- |
| type     | string | Yes  | Event type. The value is fixed at **'avoidAreaChange'**, indicating the event of changes to the area where the window cannot be displayed.|
| callback | [Callback](../apis-basic-services-kit/js-apis-base.md#callback)<{ type: [window.AvoidAreaType](arkts-apis-window-e.md#avoidareatype7), area: [window.AvoidArea](arkts-apis-window-i.md#avoidarea7) }> | Yes| Callback used to return the area information. **type** indicates the type of the area where the window cannot be displayed, and **area** indicates the area.|

**Error codes**

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |

**Example:**

```ts
// ExtensionProvider.ts
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

Unsubscribes from the event indicating changes to the area where the window cannot be displayed.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**System API**: This is a system API.

**Parameters**

| Name  | Type  | Mandatory| Description                  |
| -------- | ------ | ---- | ---------------------- |
| type     | string | Yes  | Event type. The value is fixed at **'avoidAreaChange'**, indicating the event of changes to the area where the window cannot be displayed.|
| callback | [Callback](../apis-basic-services-kit/js-apis-base.md#callback)<{ type: [window.AvoidAreaType](arkts-apis-window-e.md#avoidareatype7), area: [window.AvoidArea](arkts-apis-window-i.md#avoidarea7) }> | No| Callback used for unsubscription. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled.|

**Error codes**

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |

**Example:**

```ts
// ExtensionProvider.ts
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

**System API**: This is a system API.

**Parameters**

| Name  | Type                 | Mandatory| Description                  |
| -------- | --------------------- | ---- | ---------------------- |
| type     | string                | Yes  | Event type. The value is fixed at **'windowSizeChange'**, indicating the component (**EmbeddedComponent** or **UIExtensionComponent**) size change events.|
| callback | [Callback](../apis-basic-services-kit/js-apis-base.md#callback)<[window.Size](arkts-apis-window-i.md#size7)> | Yes  | Callback function that receives the current component size as the input parameter.|

**Error codes**

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |

**Example:**

```ts
// ExtensionProvider.ts
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // Subscribe to size change events of the component (EmbeddedComponent or UIExtensionComponent).
    extensionHostWindow.on('windowSizeChange', (size) => {
      console.info(`The avoid area of the host window is: ${JSON.stringify(size)}.`);
    });
  }
}
```

### off('windowSizeChange')

off(type: 'windowSizeChange', callback?: Callback<window.Size>): void

Unsubscribes from size change events of the component (**EmbeddedComponent** or **UIExtensionComponent**).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**System API**: This is a system API.

**Parameters**

| Name  | Type                 | Mandatory| Description                  |
| -------- | --------------------- | ---- | ---------------------- |
| type     | string                | Yes  | Event type. The value is fixed at **'windowSizeChange'**, indicating the component (**EmbeddedComponent** or **UIExtensionComponent**) size change events.|
| callback | [Callback](../apis-basic-services-kit/js-apis-base.md#callback)<[window.Size](arkts-apis-window-i.md#size7)> | No  | Callback used to return the current component (**EmbeddedComponent** or **UIExtensionComponent**) size. If a value is passed in, listening will be disabled for the specified event callback. If no value is passed in, all subscriptions to the specified event are canceled.|

**Error codes**

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |

**Example:**

```ts
// ExtensionProvider.ts
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
> - A non-secure window refers to any window that may obstruct the [EmbeddedComponent](arkui-ts/ts-container-embedded-component.md) or [UIExtensionComponent](arkui-ts/ts-container-ui-extension-component-sys.md), such as global floating windows, host subwindows, and dialog box windows created by the host application (excluding windows of these types created by system applications).
> - When using the **EmbeddedComponent** or **UIExtensionComponent** to display sensitive information, call this API to hide non-secure windows and prevent information obstruction. Hidden non-secure windows will reappear when the **EmbeddedComponent** or **UIExtensionComponent** is hidden or destroyed.
> - On PCs/2-in-1 devices, global floating windows within non-secure windows remain visible when **hideNonSecureWindows(true)** is called.

**Required permissions**: ohos.permission.ALLOW_SHOW_NON_SECURE_WINDOWS

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**System API**: This is a system API.

**Parameters**

| Name     | Type                     | Mandatory| Description      |
| ----------- | ------------------------- | ---- | ---------- |
| shouldHide  | boolean                   | Yes  | Whether to hide insecure windows. The value **true** means to hide insecure windows, and **false** means the opposite.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| 1300002  | Abnormal state. Possible causes: <br> 1. Permission denied. Interface caller does not have permission "ohos.permission.ALLOW_SHOW_NON_SECURE_WINDOWS". <br> 2. The UIExtension window proxy is abnormal. |
| 1300003  | This window manager service works abnormally. |

**Example:**

```ts
// ExtensionProvider.ts

import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // Hide insecure windows.
    extensionHostWindow.hideNonSecureWindows(true).then(()=> {
      console.info(`Succeeded in hiding the non-secure windows.`);
    }).catch((err: BusinessError)=> {
      console.error(`Failed to hide the non-secure windows. Cause:${JSON.stringify(err)}`);
    })
  }
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // Unhide insecure windows.
    extensionHostWindow.hideNonSecureWindows(false).then(()=> {
      console.info(`Succeeded in showing the non-secure windows.`);
    }).catch((err: BusinessError)=> {
      console.error(`Failed to show the non-secure windows. Cause:${JSON.stringify(err)}`);
    })
  }
}
```

### createSubWindowWithOptions<sup>12+</sup>

createSubWindowWithOptions(name: string, subWindowOptions: window.SubWindowOptions): Promise&lt;window.Window&gt;

Creates a subwindow for this **UIExtensionHostWindowProxy** instance. This API uses a promise to return the result.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type  | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| name   | string | Yes  | Name of the subwindow.|
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
| 1300002 | This window state is abnormal. Possible causes: 1. The window is not created or destroyed. 2. Internal task error. |

**Example:**

```ts
// ExtensionProvider.ts
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
        subWindow.setUIContent('pages/Index', (err, data) =>{
          if (err && err.code != 0) {
            return;
          }
          subWindow?.resize(300, 300, (err, data)=>{
            if (err && err.code != 0) {
              return;
            }
            subWindow?.moveWindowTo(100, 100, (err, data)=>{
              if (err && err.code != 0) {
                return;
              }
              subWindow?.showWindow((err, data) => {
                if (err && err.code == 0) {
                  console.info(`The subwindow has been shown!`);
                } else {
                  console.error(`Failed to show the subwindow!`);
                }
              });
            });
          });
        });
      }).catch((error: BusinessError) => {
        console.error(`Create subwindow failed: ${JSON.stringify(error)}`);
      })
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

**System API**: This is a system API.

**Parameters**

| Name| Type    | Mandatory| Description                                           |
| ------ | ------- | --- | ------------------------------------------------ |
| enable | boolean | Yes  | Whether to add or delete the flag. The value **true** means to add the watermark flag, and **false** means to delete the watermark flag.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

| ID| Error Message|
| ------- | ---------------------------------------------- |
| 1300002 | The UIExtension window proxy is abnormal.      |
| 1300003 | This window manager service works abnormally.  |
| 1300008 | The display device is abnormal. |

**Example:**

```ts
// ExtensionProvider.ts
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // Add the watermark flag.
    extensionHostWindow.setWaterMarkFlag(true).then(() => {
      console.info(`Succeeded in setting water mark flag of window.`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to setting water mark flag of window. Cause:${JSON.stringify(err)}`);
    })
  }
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // Delete the watermark flag.
    extensionHostWindow.setWaterMarkFlag(false).then(() => {
      console.info(`Succeeded in deleting water mark flag of window.`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to deleting water mark flag of window. Cause:${JSON.stringify(err)}`);
    })
  }
}
```
### hidePrivacyContentForHost<sup>13+</sup>

hidePrivacyContentForHost(shouldHide: boolean): Promise&lt;void&gt;

Sets whether to enable privacy protection for the UIExtension component during non-system screenshots. This API uses a promise to return the result.
> **NOTE**
>
> When privacy protection is enabled, neither [window.snapshot](arkts-apis-window-Window.md#snapshot9) nor [UIContext.getComponentSnapshot](arkts-apis-uicontext-uicontext.md#getcomponentsnapshot12) will capture the content of the current component (excluding subwindows created under this component).
 

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**System API**: This is a system API.

**Parameters**

| Name| Type    | Mandatory| Description                                           |
| ------ | ------- | --- | ------------------------------------------------ |
| shouldHide | boolean | Yes  | Whether to enable privacy protection for screenshots. The value **true** means to enable privacy protection for screenshots, and **false** means the opposite.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Window Error Codes](errorcode-window.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| 1300002  | Abnormal state. Possible causes: <br> 1. The UIExtension window proxy is abnormal. <br> 2. Not the UIExtensionAbility process calling.                    |

**Example:**

```ts
// ExtensionProvider.ts
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // Enable privacy protection for screenshots.
    extensionHostWindow.hidePrivacyContentForHost(true).then(() => {
      console.info(`Successfully enabled privacy protection for non-system screenshots.`);
    }).catch((err: BusinessError) => {
      console.error(`Failed enabled privacy protection for non-system screenshots. Cause:${JSON.stringify(err)}`);
    })
  }
}
```

## UIExtensionHostWindowProxyProperties

Defines information about the host application window and **UIExtensionComponent**.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**System API**: This is a system API.

| Name                        | Type       | Read-Only | Optional   | Description                            |
| ------------------------------ | ----------- | --------------- | ----------------- | -------------------------------- |
| uiExtensionHostWindowProxyRect | [window.Rect](arkts-apis-window-i.md#rect7) | Yes| No|Position, width, and height of the **UIExtensionComponent**.|

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
      bundleName: "com.example.uiextensiondemo",
      abilityName: "ExampleUIExtensionAbility",
      parameters: {
        "ability.want.params.uiExtensionType": "sys/commonUI"
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
      let promise = this.extensionHostWindow?.hideNonSecureWindows(true);
      promise?.then(()=> {
        console.info(`Succeeded in hiding the non-secure windows.`);
      }).catch((err: BusinessError)=> {
        console.error(`Failed to hide the non-secure windows. Cause:${JSON.stringify(err)}`);
      })
      this.extensionHostWindow?.hidePrivacyContentForHost(true)?.then(() => {
        console.info(`Successfully enabled privacy protection for non-system screenshots.`);
      }).catch((err: BusinessError) => {
        console.error(`Failed enabled privacy protection for non-system screenshots. Cause:${JSON.stringify(err)}`);
      })
    }

    aboutToDisappear(): void {
      this.extensionHostWindow?.off('windowSizeChange');
      this.extensionHostWindow?.off('avoidAreaChange');
      let promise = this.extensionHostWindow?.hideNonSecureWindows(false);
      promise?.then(()=> {
        console.info(`Succeeded in showing the non-secure windows.`);
      }).catch((err: BusinessError)=> {
        console.error(`Failed to show the non-secure windows. Cause:${JSON.stringify(err)}`);
      })
    }

    build() {
      Column() {
        Text(this.message)
          .fontSize(20)
          .fontWeight(FontWeight.Bold)
        Button("Obtain Component Size").width('90%').margin({top: 5, bottom: 5}).fontSize(16).onClick(() => {
          let rect = this.extensionHostWindow?.properties.uiExtensionHostWindowProxyRect;
          console.info(`Width, height, and position of the UIExtensionComponent: ${JSON.stringify(rect)}`);
        })
        Button("Obtain Avoid Area Info").width('90%').margin({top: 5, bottom: 5}).fontSize(16).onClick(() => {
          let avoidArea: window.AvoidArea | undefined = this.extensionHostWindow?.getWindowAvoidArea(window.AvoidAreaType.TYPE_SYSTEM);
          console.info(`System avoid area: ${JSON.stringify(avoidArea)}`);
        })
        Button("Create Subwindow").width('90%').margin({top: 5, bottom: 5}).fontSize(16).onClick(() => {
          let subWindowOpts: window.SubWindowOptions = {
            'title': 'This is a subwindow',
            decorEnabled: true
          };
          this.extensionHostWindow?.createSubWindowWithOptions('subWindowForHost', subWindowOpts)
            .then((subWindow: window.Window) => {
              this.subWindow = subWindow;
              this.subWindow.loadContent('pages/Index', this.storage, (err, data) =>{
                if (err && err.code != 0) {
                  return;
                }
                this.subWindow?.resize(300, 300, (err, data)=>{
                  if (err && err.code != 0) {
                    return;
                  }
                  this.subWindow?.moveWindowTo(100, 100, (err, data)=>{
                    if (err && err.code != 0) {
                      return;
                    }
                    this.subWindow?.showWindow((err, data) => {
                      if (err && err.code == 0) {
                        console.info(`The subwindow has been shown!`);
                      } else {
                        console.error(`Failed to show the subwindow!`);
                      }
                    });
                  });
                });
              });
            }).catch((error: BusinessError) => {
              console.error(`Create subwindow failed: ${JSON.stringify(error)}`);
            })
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
    "type": "sys/commonUI",
  }
  ```
