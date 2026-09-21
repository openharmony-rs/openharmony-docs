# WindowProxy

```TypeScript
interface WindowProxy
```

The proxy of the UIExtension window.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { uiExtension } from '@kit.ArkUI';
```

## createSubWindowWithOptions

```TypeScript
createSubWindowWithOptions(name: string, subWindowOptions: window.SubWindowOptions): Promise<window.Window>
```

Creates a subwindow for this window proxy. This API uses a promise to return the result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

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
      console.error(`Create subwindow failed. Cause code: ${error.code}, message: ${error.message}`);
    });
  }
}
```

<a id="createsubwindowwithoptions-1"></a>

## createSubWindowWithOptions

```TypeScript
createSubWindowWithOptions(name: string, subWindowConfig: window.SubWindowOptions,
        followCreatorLifecycle: boolean): Promise<window.Window>
```

Create subwindow.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

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
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. Internal task error. 3. The subWindow has been created and cannot be created again. 4. It is not allowed to create non-secure window when secure extension exists. |
| 1300035 | Creating a subwindow is not allowed in the current context. Possible cause: 1. An AgentUIExtensionAbility cannot create a subwindow. |

**Examples**

```TypeScript
// ExtensionProvider.ets
import { EmbeddedUIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    const subWindowConfig: window.SubWindowOptions = {
      title: 'This is a subwindow',
      decorEnabled: true
    };
    // Create a subwindow.
    extensionWindow.createSubWindowWithOptions('subWindowForHost', subWindowConfig, true)
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
      console.error(`Create subwindow failed. Cause code: ${error.code}, message: ${error.message}`);
    });
  }
}
```

## getWindowAvoidArea

```TypeScript
getWindowAvoidArea(type: window.AvoidAreaType): window.AvoidArea
```

Obtains the area where this window cannot be displayed, for example, the system bar area, notch, gesture area, and soft keyboard area.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

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
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |

**Examples**

```TypeScript
// ExtensionProvider.ets
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

## occupyEvents

```TypeScript
occupyEvents(eventFlags: number): Promise<void>
```

Sets the events that the component (**EmbeddedComponent** or **UIExtensionComponent**) will occupy, preventing the host from responding to these events within the component's area.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| eventFlags | number | Yes | Type of events to occupy. For details about the available values, see [EventFlag](arkts-arkui-uiextension-eventflag-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
// ExtensionProvider.ets
import { EmbeddedUIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { uiExtension } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // Occupy events.
    setTimeout(() => {
      try {
        extensionWindow.occupyEvents(uiExtension.EventFlag.EVENT_CLICK | uiExtension.EventFlag.EVENT_LONG_PRESS).then(() => {
          console.info(`Succeeded in occupying events`);
        }).catch((err: BusinessError) => {
          console.error(`Failed to occupy events. Cause code: ${err.code}, message: ${err.message}`);
        });
      } catch (err) {
        console.error(`Occupy events got exception code: ${err.code}, message: ${err.message}`);
      }
    }, 500);
  }
}
```

## off('avoidAreaChange')

```TypeScript
off(type: 'avoidAreaChange', callback?: Callback<AvoidAreaInfo>): void
```

Unsubscribes from events of system avoidance area changes.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'avoidAreaChange' | Yes | Event type. The value is fixed at **'avoidAreaChange'**, indicating the event of changes to the area where the window cannot be displayed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AvoidAreaInfo](arkts-arkui-uiextension-avoidareainfo-i.md)&gt; | No | Callback used for unsubscription. If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | Abnormal state. Possible causes: 1. The listening type is not supported. 2. The listening type is not registered. 3. The listener has not been registered. 4. The UIExtension window proxy is abnormal. |

**Examples**

```TypeScript
// ExtensionProvider.ets
import { EmbeddedUIExtensionAbility, UIExtensionContentSession } from '@kit.AbilityKit';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // Cancel all subscriptions to the event indicating changes to the area where the window cannot be displayed.
    extensionWindow.off('avoidAreaChange');
  }
}
```

## off('windowSizeChange')

```TypeScript
off(type: 'windowSizeChange', callback?: Callback<window.Size>): void
```

Unsubscribes from size change events of the component (**EmbeddedComponent** or **UIExtensionComponent**).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

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

**Examples**

```TypeScript
// ExtensionProvider.ets
import { EmbeddedUIExtensionAbility, UIExtensionContentSession } from '@kit.AbilityKit';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // Unsubscribe from size change events of the component (EmbeddedComponent or UIExtensionComponent).
    extensionWindow.off('windowSizeChange');
  }
}
```

## off('rectChange')

```TypeScript
off(type: 'rectChange', callback?: Callback<RectChangeOptions>): void
```

Unsubscribes from position and size change events of the component (**EmbeddedComponent** or **UIExtensionComponent**).

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'rectChange' | Yes | Event type. The value is fixed at **'rectChange'**, indicating the rectangle change event for the component (**EmbeddedComponent** or **UIExtensionComponent**). |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RectChangeOptions](arkts-arkui-uiextension-rectchangeoptions-i.md)&gt; | No | Callback used to return the current rectangle change values and the reason for the change of the component (**EmbeddedComponent** or **UIExtensionComponent**). If a value is passed in, the corresponding subscription is canceled. If no value is passed in, all subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | Abnormal state. Possible causes: 1. The listening type is not supported. 2. The listening type is not registered. 3. The listener has not been registered. 4. The UIExtension window proxy is abnormal. |

**Examples**

```TypeScript
// ExtensionProvider.ets
import { EmbeddedUIExtensionAbility, UIExtensionContentSession } from '@kit.AbilityKit';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // Unsubscribe from position and size change events of the component (EmbeddedComponent or UIExtensionComponent).
    extensionWindow.off('rectChange');
  }
}
```

## on('avoidAreaChange')

```TypeScript
on(type: 'avoidAreaChange', callback: Callback<AvoidAreaInfo>): void
```

Subscribes to events of system avoidance area changes.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'avoidAreaChange' | Yes | Event type. The value is fixed at **'avoidAreaChange'**, indicating the event of changes to the area where the window cannot be displayed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AvoidAreaInfo](arkts-arkui-uiextension-avoidareainfo-i.md)&gt; | Yes | Callback function that receives the information about the current avoidance area. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | Abnormal state. Possible causes: 1. The listening type is not supported. 2. The listener has been registered. 3. The UIExtension window proxy is abnormal. |

**Examples**

```TypeScript
// ExtensionProvider.ets
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

## on('windowSizeChange')

```TypeScript
on(type: 'windowSizeChange', callback: Callback<window.Size>): void
```

Subscribes to size change events of the component (**EmbeddedComponent** or **UIExtensionComponent**).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

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

**Examples**

```TypeScript
// ExtensionProvider.ets
import { EmbeddedUIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // Subscribe to size change events of the component (EmbeddedComponent or UIExtensionComponent).
    extensionWindow.on('windowSizeChange', (size: window.Size) => {
      console.info(`The size of the component is: ${JSON.stringify(size)}.`);
    });
  }
}
```

## on('rectChange')

```TypeScript
on(type: 'rectChange', reasons: number, callback: Callback<RectChangeOptions>): void
```

Subscribes to position and size change events of the component (**EmbeddedComponent** or **UIExtensionComponent**).

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'rectChange' | Yes | Event type. The value is fixed at **'rectChange'**, indicating the rectangle change event for the component (**EmbeddedComponent** or **UIExtensionComponent**). |
| reasons | number | Yes | Reason why the position and size of the component (**EmbeddedComponent** or **UIExtensionComponent**) change. For details about the values, see [RectChangeReason](arkts-arkui-uiextension-rectchangereason-e.md). |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RectChangeOptions](arkts-arkui-uiextension-rectchangeoptions-i.md)&gt; | Yes | Callback used to return the current rectangle change values and the reason for the change of the component (**EmbeddedComponent** or **UIExtensionComponent**). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | Abnormal state. Possible causes: 1. The listening type is not supported. 2. The listener has been registered. 3. The UIExtension window proxy is abnormal. |

**Examples**

```TypeScript
// ExtensionProvider.ets
import { EmbeddedUIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { uiExtension } from '@kit.ArkUI';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // Subscribe to position and size change events of the component (EmbeddedComponent or UIExtensionComponent).
    extensionWindow.on('rectChange', uiExtension.RectChangeReason.HOST_WINDOW_RECT_CHANGE, (data: uiExtension.RectChangeOptions) => {
        console.info('Succeeded window rect changes. Data: ' + JSON.stringify(data));
    });
  }
}
```

## properties

```TypeScript
properties: WindowProxyProperties
```

Information about the component (**EmbeddedComponent** or **UIExtensionComponent**).

Note: Due to architecture restrictions, avoid obtaining the value in [onSessionCreate](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensionability-uiextensionability-c.md#onsessioncreate). Instead, when possible, obtain the value after receiving the [on('windowSizeChange')](#onwindowsizechange) callback.

**Type:** [WindowProxyProperties](arkts-arkui-uiextension-windowproxyproperties-i.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
