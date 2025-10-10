# @ohos.arkui.uiExtension (uiExtension)
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @chbchb12-->
<!--Designer: @stupidb-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

The **uiExtension** module provides APIs for the EmbeddedUIExtensionAbility (or UIExtensionAbility) to obtain the host application window information or the information about the corresponding **EmbeddedComponent**<!--Del--> (or **UIExtensionComponent**)<!--DelEnd--> component.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.
>

## Modules to Import

```
import { uiExtension } from '@kit.ArkUI';
```

## WindowProxy

Implements the proxy for the UIExtension host application window.

### Properties

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 14.

| Name                                | Type                 | Read Only| Optional| Description                                                                                                    |
| ------------------------------------| -------------------------------------------------- | ---- | ---- | ------------------------------------------------------------------------------------------------------ |
| properties<sup>14+</sup>            | [WindowProxyProperties](#windowproxyproperties14) |  No |  No | Information about the component (**EmbeddedComponent** or **UIExtensionComponent**).<br>**NOTE**<br>Due to architecture restrictions, avoid obtaining the value in [onSessionCreate](../apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md#onsessioncreate). Instead, when possible, obtain the value after receiving the [on('windowSizeChange')](../apis-arkui/js-apis-arkui-uiExtension.md#onwindowsizechange) callback.                                                                           |

### getWindowAvoidArea

getWindowAvoidArea(type: window.AvoidAreaType): window.AvoidArea

Obtains the area where this window cannot be displayed, for example, the system bar area, notch, gesture area, and soft keyboard area.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type |[window.AvoidAreaType](arkts-apis-window-e.md#avoidareatype7) | Yes| Type of the area.|

**Return value**

| Type| Description|
| -------- | -------- |
|[window.AvoidArea](arkts-apis-window-i.md#avoidarea7) | Area where the window cannot be displayed.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |

**Example**

```ts
// ExtensionProvider.ts
import { EmbeddedUIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // Obtain the information about the area where the window cannot be displayed.
    let avoidArea: window.AvoidArea | undefined = extensionWindow?.getWindowAvoidArea(window.AvoidAreaType.TYPE_SYSTEM);
    console.info(`avoidArea: ${JSON.stringify(avoidArea)}`);
  }
}
```

### on('avoidAreaChange')

on(type: 'avoidAreaChange', callback: Callback&lt;AvoidAreaInfo&gt;): void

Subscribes to the event indicating changes to the area where the window cannot be displayed.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ---- | ---- | ---- |
| type   | string | Yes| Event type. The value is fixed at **'avoidAreaChange'**, indicating the event of changes to the area where the window cannot be displayed.|
| callback | [Callback](../apis-basic-services-kit/js-apis-base.md#callback)<[AvoidAreaInfo](#avoidareainfo)> | Yes| Callback used to return the area information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |

**Example**

```ts
// ExtensionProvider.ts
import { EmbeddedUIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { uiExtension } from '@kit.ArkUI';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // Subscribe to the event indicating changes to the area where the window cannot be displayed.
    extensionWindow.on('avoidAreaChange', (info: uiExtension.AvoidAreaInfo) => {
      console.info(`The avoid area of the host window is: ${JSON.stringify(info.area)}.`);
    });
  }
}
```

### off('avoidAreaChange')

off(type: 'avoidAreaChange', callback?: Callback&lt;AvoidAreaInfo&gt;): void

Unsubscribes from the event indicating changes to the area where the window cannot be displayed.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name  | Type| Mandatory| Description|
| -------- | ---- | ---- | ---  |
| type     | string | Yes| Event type. The value is fixed at **'avoidAreaChange'**, indicating the event of changes to the area where the window cannot be displayed.|
| callback | [Callback](../apis-basic-services-kit/js-apis-base.md#callback)<[AvoidAreaInfo](#avoidareainfo)> | No| Callback used for unsubscription. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed. |

**Example**

```ts
// ExtensionProvider.ts
import { EmbeddedUIExtensionAbility, UIExtensionContentSession } from '@kit.AbilityKit';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // Cancel all subscriptions to the event indicating changes to the area where the window cannot be displayed.
    extensionWindow.off('avoidAreaChange');
  }
}
```

### on('windowSizeChange')

on(type: 'windowSizeChange', callback: Callback<window.Size>): void

Subscribes to the window size change event of a component (EmbeddedComponent or UIExtensionComponent).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name  | Type                 | Mandatory| Description                  |
| -------- | --------------------- | ---- | ---------------------- |
| type     | string                | Yes  | Listener event type. The value is fixed at windowSizeChange, indicating the size change event of a component (EmbeddedComponent or UIExtensionComponent).|
| callback | [Callback](../apis-basic-services-kit/js-apis-base.md#callback)<[window.Size](arkts-apis-window-i.md#size7)> | Yes  | Callback function: receives the size of the current component (EmbeddedComponent or UIExtensionComponent).|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |

**Example:**

```ts
// ExtensionProvider.ts
import { EmbeddedUIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // Register the listener for the size change of the component (EmbeddedComponent or UIExtensionComponent).
    extensionWindow.on('windowSizeChange', (size: window.Size) => {
      console.info(`The avoid area of the host window is: ${JSON.stringify(size)}.`);
    });
  }
}
```

### off('windowSizeChange')

off(type: 'windowSizeChange', callback?: Callback<window.Size>): void

Unsubscribes from the window size change event of the component (EmbeddedComponent or UIExtensionComponent).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name  | Type                 | Mandatory| Description                  |
| -------- | --------------------- | ---- | ---------------------- |
| type     | string                | Yes  | Type of the event to be deregistered. The value is fixed at windowSizeChange, which indicates the size change event of the component (EmbeddedComponent or UIExtensionComponent).|
| callback | [Callback](../apis-basic-services-kit/js-apis-base.md#callback)<[window.Size](arkts-apis-window-i.md#size7)> | No  | Callback used for unsubscription. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |

**Example**

```ts
// ExtensionProvider.ts
import { EmbeddedUIExtensionAbility, UIExtensionContentSession } from '@kit.AbilityKit';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // Deregister the listening on the size change of the component (EmbeddedComponent or UIExtensionComponent).
    extensionWindow.off('windowSizeChange');
  }
}
```

### on('rectChange')<sup>14+</sup>

on(type: 'rectChange', reasons: number, callback: Callback&lt;RectChangeOptions&gt;): void

Listens to the position and size changes of a registered component (EmbeddedComponent or UIExtensionComponent).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 14.

**Device behavior differences**: This API can be properly called on 2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Parameters**

| Name  | Type                          | Mandatory| Description                                                    |
| -------- | ------------------------------ | ---- | -------------------------------------------------------- |
| type     | string                         | Yes  | Event type. The value is fixed at **'rectChange'**, indicating the rectangle change event for the component (**EmbeddedComponent** or **UIExtensionComponent**).|
| reasons  | number                         | Yes  | Reason why the position and size of the component (EmbeddedComponent or UIExtensionComponent) change. For details about the values, see the enumerated values of [RectChangeReason](#rectchangereason14).
| callback | [Callback](../apis-basic-services-kit/js-apis-base.md#callback)<[RectChangeOptions](#rectchangeoptions14)> | Yes| Callback used to return the current rectangle change values and the reason for the change of the component (**EmbeddedComponent** or **UIExtensionComponent**).|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------------------- |
| 401     | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed. |
| 801     | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example:**

```ts
// ExtensionProvider.ts
import { EmbeddedUIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { uiExtension } from '@kit.ArkUI';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // Subscribe to changes in the position and size of the component (EmbeddedComponent or UIExtensionComponent).
    extensionWindow.on('rectChange', uiExtension.RectChangeReason.HOST_WINDOW_RECT_CHANGE, (data: uiExtension.RectChangeOptions) => {
        console.info('Succeeded window rect changes. Data: ' + JSON.stringify(data));
    });
  }
}
```

### off('rectChange')<sup>14+</sup>

off(type: 'rectChange', callback?: Callback&lt;RectChangeOptions&gt;): void

Deregisters the listener for the location and size changes of the component (EmbeddedComponent or UIExtensionComponent).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 14.

**Device behavior differences**: This API can be properly called on 2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Parameters**

| Name  | Type                          | Mandatory| Description                                                        |
| -------- | ------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                         | Yes  | Event type. The value is fixed at **'rectChange'**, indicating the rectangle change event for the component (**EmbeddedComponent** or **UIExtensionComponent**).|
| callback | [Callback](../apis-basic-services-kit/js-apis-base.md#callback)<[RectChangeOptions](#rectchangeoptions14)> | No  | Callback used to return the current rectangle change values and the reason for the change of the component (**EmbeddedComponent** or **UIExtensionComponent**). If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------------------- |
| 401     | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed. |
| 801     | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example:**

```ts
// ExtensionProvider.ts
import { EmbeddedUIExtensionAbility, UIExtensionContentSession } from '@kit.AbilityKit';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // Unsubscribe from changes in the position and size of the component (EmbeddedComponent or UIExtensionComponent).
    extensionWindow.off('rectChange');
  }
}
```

### createSubWindowWithOptions

createSubWindowWithOptions(name: string, subWindowOptions: window.SubWindowOptions): Promise&lt;window.Window&gt;

Creates a subwindow for this window proxy. This API uses a promise to return the result.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type  | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| name   | string | Yes  | Name of the subwindow.|
| subWindowOptions | [window.SubWindowOptions](arkts-apis-window-i.md#subwindowoptions11) | Yes  | Parameters used for creating the subwindow. |

**Return value**

| Type                            | Description                                            |
| -------------------------------- | ------------------------------------------------ |
| Promise&lt;[window.Window](arkts-apis-window-Window.md)&gt; | Promise used to return the subwindow created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). and [Window Error Codes](errorcode-window.md).

| ID| Error Message|
| ------- | ------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
| 1300002 | This window state is abnormal. |

**Example:**

```ts
// ExtensionProvider.ts
import { EmbeddedUIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    const subWindowOpts: window.SubWindowOptions = {
      title: 'This is a subwindow',
      decorEnabled: true
    };
    // Create a subwindow.
    extensionWindow.createSubWindowWithOptions('subWindowForHost', subWindowOpts)
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
        console.error(`Create subwindow failed. Cause code: ${error.code}, message: ${error.message}`);
      })
  }
}
```

### occupyEvents<sup>18+</sup>

occupyEvents(eventFlags: number): Promise&lt;void&gt;

Sets the events that the component (**EmbeddedComponent** or **UIExtensionComponent**) will occupy, preventing the host from responding to these events within the component's area.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 18.

**Parameters**

| Name| Type   | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| eventFlags | number | Yes| Type of events to occupy. For details about the available values, see [EventFlag](#eventflag18).|

**Return value**

| Type               | Description                    |
| ------------------- | ------------------------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). and [Window Error Codes](errorcode-window.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401      | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.   |
| 1300002  | This window state is abnormal. |
| 1300003  | This window manager service works abnormally. |

**Example:**

```ts
// ExtensionProvider.ts
import { EmbeddedUIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { uiExtension } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // Occupy events.
    setTimeout(() => {
      try {
        let promise = extensionWindow.occupyEvents(uiExtension.EventFlag.EVENT_CLICK | uiExtension.EventFlag.EVENT_LONG_PRESS);
        promise.then(() => {
          console.info(`Successed in occupy events`);
        }).catch((err: BusinessError) => {
          console.error(`Failed to occupy events. Cause code: ${err.code}, message: ${err.message}`);
        });
      } catch (e) {
        console.error(`Occupy events got exception code: ${e.code}, message: ${e.message}`);
      }
    }, 500);
  }
}
```

## EventFlag<sup>18+</sup>

Enumerates event types.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 18.

| Name                       | Value             | Description           |
|-----------------------------| --------------- |----------------|
| EVENT_NONE                  | 0x00000000      | No event.     |
| EVENT_PAN_GESTURE_LEFT      | 0x00000001      | Pan-left event.   |
| EVENT_PAN_GESTURE_RIGHT     | 0x00000002      | Pan-right event.   |
| EVENT_PAN_GESTURE_UP        | 0x00000004      | Pan-up event.   |
| EVENT_PAN_GESTURE_DOWN      | 0x00000008      | Pan-down event.   |
| EVENT_CLICK                 | 0x00000100      | Click event.   |
| EVENT_LONG_PRESS            | 0x00000200      | Long press event.   |

## AvoidAreaInfo

Describes the information about the area where the window cannot be displayed.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 12.

| Name| Type                | Read Only| Optional| Description       |
| ------ | -------------------- | ----- | ---- | ------------------ |
| type   | [window.AvoidAreaType](arkts-apis-window-e.md#avoidareatype7) | No| No| Type of the area where the window cannot be displayed.|
| area   | [window.AvoidArea](arkts-apis-window-i.md#avoidarea7)     | No| No| Area where the window cannot be displayed.|

## WindowProxyProperties<sup>14+</sup>

Provides information about a component.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 14.

| Name                        | Type       | Read Only| Optional| Description                            |
| ------------------------------ | ----------- | ----- | ---- | -------------------------------- |
| uiExtensionHostWindowProxyRect | [window.Rect](arkts-apis-window-i.md#rect7) | No| No|Position and size of the component (**EmbeddedComponent** or **UIExtensionComponent**).|

## RectChangeReason<sup>14+</sup>

Enumerates the reasons for changes in the rectangle (position and size) of the component (**EmbeddedComponent** or **UIExtensionComponent**).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 14.

| Name                   | Value    | Description                                                        |
| ----------------------- | ------ | ------------------------------------------------------------ |
| HOST_WINDOW_RECT_CHANGE | 0x0001 | The rectangle of the host window containing the component changes.|

## RectChangeOptions<sup>14+</sup>

Provides the values and reasons returned when the rectangle (position and size) of the component (**EmbeddedComponent** or **UIExtensionComponent**) changes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 14.

| Name      | Type     | Read Only| Optional| Description              |
| ---------- | ------------- | ---- | ---- | ------------------ |
| rect   | [window.Rect](arkts-apis-window-i.md#rect7) | No  | No  | New values of the rectangle of the component after the change.|
| reason    | [RectChangeReason](#rectchangereason14) | No  | No  | Reason for the rectangle change.|

## Example

This example shows how to use all the available APIs in the EmbeddedUIExtensionAbility. The bundle name of the sample application is **com.example.embeddeddemo**, and the EmbeddedUIExtensionAbility to start is **ExampleEmbeddedAbility**.

- The EntryAbility (UIAbility) of the sample application loads the **pages/Index.ets** file, whose content is as follows:

  ```ts
  // The UIAbility loads pages/Index.ets when started.
  import { Want } from '@kit.AbilityKit';

  @Entry
  @Component
  struct Index {
    @State message: string = 'Message: ';
    private want: Want = {
      bundleName: "com.example.embeddeddemo",
      abilityName: "ExampleEmbeddedAbility",
    }

    build() {
      Row() {
        Column() {
          Text(this.message).fontSize(30)
          EmbeddedComponent(this.want, EmbeddedType.EMBEDDED_UI_EXTENSION)
            .width('100%')
            .height('90%')
            .onTerminated((info)=>{
              this.message = 'Termination: code = ' + info.code + ', want = ' + JSON.stringify(info.want);
            })
            .onError((error)=>{
              this.message = 'Error: code = ' + error.code;
            })
        }
        .width('100%')
      }
      .height('100%')
    }
  }
  ```

- The EmbeddedUIExtensionAbility to start by the **EmbeddedComponent** is implemented in the **ets/extensionAbility/ExampleEmbeddedAbility** file. The file content is as follows:

  ```ts
  import { EmbeddedUIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';

  const TAG: string = '[ExampleEmbeddedAbility]';
  export default class ExampleEmbeddedAbility extends EmbeddedUIExtensionAbility {
    
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

- The entry page file of the EmbeddedUIExtensionAbility is **pages/extension.ets**, whose content is as follows:

  ```ts
  import { UIExtensionContentSession } from '@kit.AbilityKit';
  import { uiExtension, window } from '@kit.ArkUI';
  import { BusinessError } from '@kit.BasicServicesKit';

  @Entry()
  @Component
  struct Extension {
    @State message: string = 'EmbeddedUIExtensionAbility Index';
    private storage: LocalStorage | undefined = this.getUIContext()?.getSharedLocalStorage();
    private session: UIExtensionContentSession | undefined = this.storage?.get<UIExtensionContentSession>('session');
    private extensionWindow: uiExtension.WindowProxy | undefined = this.session?.getUIExtensionWindowProxy();
    private subWindow: window.Window | undefined = undefined;

    aboutToAppear(): void {
      this.extensionWindow?.on('windowSizeChange', (size: window.Size) => {
          console.info(`size = ${JSON.stringify(size)}`);
      });
      this.extensionWindow?.on('rectChange', uiExtension.RectChangeReason.HOST_WINDOW_RECT_CHANGE, (data: uiExtension.RectChangeOptions) => {
          console.info('Succeeded window rect changes. Data: ' + JSON.stringify(data));
      });
      this.extensionWindow?.on('avoidAreaChange', (info: uiExtension.AvoidAreaInfo) => {
          console.info(`type = ${JSON.stringify(info.type)}, area = ${JSON.stringify(info.area)}`);
      });
    }

    aboutToDisappear(): void {
      this.extensionWindow?.off('windowSizeChange');
      this.extensionWindow?.off('rectChange');
      this.extensionWindow?.off('avoidAreaChange');
    }

    build() {
      Column() {
        Text(this.message)
          .fontSize(20)
          .fontWeight(FontWeight.Bold)
        Button("Obtain Component Size").width('90%').margin({top: 5, bottom: 5}).fontSize(16).onClick(() => {
          let rect = this.extensionWindow?.properties.uiExtensionHostWindowProxyRect;
          console.info(`EmbeddedComponent position and size: ${JSON.stringify(rect)}`);
        })
        Button("Obtain Avoid Area Info").width('90%').margin({top: 5, bottom: 5}).fontSize(16).onClick(() => {
          let avoidArea: window.AvoidArea | undefined = this.extensionWindow?.getWindowAvoidArea(window.AvoidAreaType.TYPE_SYSTEM);
          console.info(`System avoid area: ${JSON.stringify(avoidArea)}`);
        })
        Button("Create Subwindow").width('90%').margin({top: 5, bottom: 5}).fontSize(16).onClick(() => {
          let subWindowOpts: window.SubWindowOptions = {
              'title': 'This is a subwindow',
              decorEnabled: true
          };
          this.extensionWindow?.createSubWindowWithOptions('subWindowForHost', subWindowOpts)
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
                  console.error(`Create subwindow failed. Cause code: ${error.code}, message: ${error.message}`);
              })
        })
      }.width('100%').height('100%')
    }
  }
  ```

- Add an item to **extensionAbilities** in the **module.json5** file of the sample application. The details are as follows:
  ```json
  {
    "name": "ExampleEmbeddedAbility",
    "srcEntry": "./ets/extensionAbility/ExampleEmbeddedAbility.ets",
    "type": "embeddedUI"
  }
  ```
