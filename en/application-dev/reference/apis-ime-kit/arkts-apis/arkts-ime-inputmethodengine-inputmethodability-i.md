# InputMethodAbility

In the following API examples, you must first use [getInputMethodAbility](arkts-ime-inputmethodengine-getinputmethodability-f.md) to obtain an **InputMethodAbility** instance, and then call the APIs using the obtained instance.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## createPanel

```TypeScript
createPanel(ctx: BaseContext, info: PanelInfo, callback: AsyncCallback<Panel>): void
```

Creates an input method panel. This API can be called only by the input method application in the [InputMethodExtensionAbility](arkts-ime-inputmethodextensionability-c.md) class. This API uses an asynchronous callback to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> Only one [SOFT_KEYBOARD](arkts-ime-inputmethodengine-paneltype-e.md) panel and one [STATUS_BAR](arkts-ime-inputmethodengine-paneltype-e.md) panel can be created for a single input method. <br> <br>
> The input method panel does not support subwindows. For example, subwindows cannot be created using APIs such as [window.createWindow](../../../windowmanager/application-window-fa.md#setting-the-child-window-of-an-application), [bindContextMenu](../../apis-arkui/arkts-components/arkts-arkui-commonmethod-c.md#bindcontextmenu), and CustomDialog. You are advised to adopt alternative solutions to sub-windows, such as using a dialog box or [bindMenu](../../apis-arkui/arkts-components/arkts-arkui-commonmethod-c.md#bindmenu), or set **showInSubwindow** to **false**.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ctx | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md) | Yes | Current context of the input method. |
| info | [PanelInfo](arkts-ime-inputmethodengine-panelinfo-i.md) | Yes | Information about the input method panel. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Panel](arkts-ime-inputmethodengine-panel-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, the created input method panel is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800004](../errorcode-inputmethod-framework.md#12800004-not-an-input-method) | not an input method application. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMethodEngine, InputMethodExtensionAbility } from '@kit.IMEKit';
import { Want } from '@kit.AbilityKit';

let panelInfo: inputMethodEngine.PanelInfo = {
  type: inputMethodEngine.PanelType.SOFT_KEYBOARD,
  flag: inputMethodEngine.PanelFlag.FLG_FIXED
}

class InputMethodExt extends InputMethodExtensionAbility {
    onCreate(want: Want): void {
        console.info(`onCreate, want: ${want.abilityName}`);
        if (!this.context) {
            inputMethodEngine.getInputMethodAbility()
            .createPanel(this.context, panelInfo, (err: BusinessError, panel: inputMethodEngine.Panel) => {
                if (err) {
                console.error(`Failed to createPanel. Code is ${err.code}, message is ${err.message}`);
                return;
              }
                console.info('Succeed in creating panel.');
            })
        }
    }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMethodEngine, InputMethodExtensionAbility } from '@kit.IMEKit';
import { Want } from '@kit.AbilityKit';

let panelInfo: inputMethodEngine.PanelInfo = {
  type: inputMethodEngine.PanelType.SOFT_KEYBOARD,
  flag: inputMethodEngine.PanelFlag.FLG_FIXED
}

class InputMethodExt extends InputMethodExtensionAbility {
    onCreate(want: Want): void {
        console.info(`onCreate, want: ${want.abilityName}`);
        if (this.context) {
            inputMethodEngine.getInputMethodAbility().createPanel(this.context, panelInfo)
                .then((panel: inputMethodEngine.Panel) => {
                console.info('Succeed in creating panel.');
            }).catch((err: BusinessError) => {
                console.error(`Failed to create panel. Code is ${err.code}, message is ${err.message}`);
            })
        }
    }
}
```

## createPanel

```TypeScript
createPanel(ctx: BaseContext, info: PanelInfo): Promise<Panel>
```

Creates an input method panel. This API can be called only by the input method application in the [InputMethodExtensionAbility](arkts-ime-inputmethodextensionability-c.md) class. This API uses a promise to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> Only one [SOFT_KEYBOARD](arkts-ime-inputmethodengine-paneltype-e.md) panel and one [STATUS_BAR](arkts-ime-inputmethodengine-paneltype-e.md) panel can be created for a single input method. <br>
> <br>
> The input method panel does not support subwindows. For example, subwindows cannot be created using APIs such as [window.createWindow](../../../windowmanager/application-window-fa.md#setting-the-child-window-of-an-application), [bindContextMenu](../../apis-arkui/arkts-components/arkts-arkui-commonmethod-c.md#bindcontextmenu), and CustomDialog. You are advised to adopt alternative solutions to sub-windows, such as using a dialog box or [bindMenu](../../apis-arkui/arkts-components/arkts-arkui-commonmethod-c.md#bindmenu), or set **showInSubwindow** to **false**.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ctx | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md) | Yes | Current context of the input method. |
| info | [PanelInfo](arkts-ime-inputmethodengine-panelinfo-i.md) | Yes | Information about the input method panel. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Panel](arkts-ime-inputmethodengine-panel-i.md)&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800004](../errorcode-inputmethod-framework.md#12800004-not-an-input-method) | not an input method application. |

**Examples**

See [createPanel](#createpanel)

## destroyPanel

```TypeScript
destroyPanel(panel: Panel, callback: AsyncCallback<void>): void
```

Destroys the specified input method panel. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| panel | [Panel](arkts-ime-inputmethodengine-panel-i.md) | Yes | Input method panel to destroy. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let panelInfo: inputMethodEngine.PanelInfo = {
  type: inputMethodEngine.PanelType.SOFT_KEYBOARD,
  flag: inputMethodEngine.PanelFlag.FLG_FIXED
}

let inputPanel: inputMethodEngine.Panel | undefined = undefined;
if (this.context) {
  inputMethodEngine.getInputMethodAbility()
    .createPanel(this.context, panelInfo, (err: BusinessError, panel: inputMethodEngine.Panel) => {
      if (err) {
        console.error(`Failed to create panel. Code is ${err.code}, message is ${err.message}`);
        return;
      }
      inputPanel = panel;
      console.info('Succeed in creating panel.');
    })
}

if (inputPanel) {
  inputMethodEngine.getInputMethodAbility().destroyPanel(inputPanel, (err: BusinessError) => {
    if (err !== undefined) {
      console.error(`Failed to destroy panel. Code is ${err.code}, message is ${err.message}`);
      return;
    }
    console.info('Succeed in destroying panel.');
  })
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let panelInfo: inputMethodEngine.PanelInfo = {
  type: inputMethodEngine.PanelType.SOFT_KEYBOARD,
  flag: inputMethodEngine.PanelFlag.FLG_FIXED
}

let inputPanel: inputMethodEngine.Panel | undefined = undefined;
if (this.context) {
  inputMethodEngine.getInputMethodAbility()
    .createPanel(this.context, panelInfo, (err: BusinessError, panel: inputMethodEngine.Panel) => {
      if (err) {
        console.error(`Failed to create panel. Code is ${err.code}, message is ${err.message}`);
        return;
      }
      inputPanel = panel;
      console.info('Succeed in creating panel.');
    })
}

if (inputPanel) {
  inputMethodEngine.getInputMethodAbility().destroyPanel(inputPanel).then(() => {
    console.info('Succeed in destroying panel.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to destroy panel. Code is ${err.code}, message is ${err.message}`);
  });
}
```

## destroyPanel

```TypeScript
destroyPanel(panel: Panel): Promise<void>
```

Destroys the specified input method panel. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| panel | [Panel](arkts-ime-inputmethodengine-panel-i.md) | Yes | Input method panel to destroy. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**Examples**

See [destroyPanel](#destroypanel)

## getSecurityMode

```TypeScript
getSecurityMode(): SecurityMode
```

Obtains the current security mode of the input method.

**Since:** 11

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| [SecurityMode](arkts-ime-inputmethodengine-securitymode-e.md) | Security mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800004](../errorcode-inputmethod-framework.md#12800004-not-an-input-method) | not an input method application. |

**Examples**

```TypeScript
let security: inputMethodEngine.SecurityMode = inputMethodEngine.getInputMethodAbility().getSecurityMode();
console.error(`getSecurityMode, securityMode is : ${security}`);
```

## off('inputStart')

```TypeScript
off(type: 'inputStart', callback?: (kbController: KeyboardController, inputClient: InputClient) => void): void
```

Disables listening for the input method binding event. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'inputStart' | Yes | Event type, which is **'inputStart'**. |
| callback | (kbController: KeyboardController, inputClient: InputClient) =&gt; void | No | Callback to unregister. If this parameter is not specified, this API unregisters all callbacks for the specified type. |

## off('inputStop')

```TypeScript
off(type: 'inputStop', callback: () => void): void
```

Disables listening for the input method stop event. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'inputStop' | Yes | Event type, which is **'inputStop'**. |
| callback | () =&gt; void | Yes | Callback to unregister. If this parameter is not specified, this API unregisters all callbacks for the specified type. |

## off('setCallingWindow')

```TypeScript
off(type: 'setCallingWindow', callback: (wid: number) => void): void
```

Disables listening for the window invocation setting event. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'setCallingWindow' | Yes | Event type, which is **'setCallingWindow'**. |
| callback | (wid: number) =&gt; void | Yes | Callback to unregister. If this parameter is not specified, this API unregisters all callbacks for the specified type. |

## off('keyboardShow' | 'keyboardHide')

```TypeScript
off(type: 'keyboardShow' | 'keyboardHide', callback?: () => void): void
```

Disables listening for a keyboard visibility event. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyboardShow' &#124; 'keyboardHide' | Yes | Event type.<br>- The value **'keyboardShow'** indicates the keyboard display event. <br>- The value **'keyboardHide'** indicates the keyboard hiding event. |
| callback | () =&gt; void | No | Callback used to return the result. |

## off('keyboardShow' | 'keyboardHide')

```TypeScript
off(type: 'keyboardShow' | 'keyboardHide', callback?: () => void): void
```

Disables listening for a keyboard visibility event. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyboardShow' &#124; 'keyboardHide' | Yes | Event type.<br>- The value **'keyboardShow'** indicates the keyboard display event. <br>- The value **'keyboardHide'** indicates the keyboard hiding event. |
| callback | () =&gt; void | No | Callback used to return the result. |

## off('setSubtype')

```TypeScript
off(type: 'setSubtype', callback?: (inputMethodSubtype: InputMethodSubtype) => void): void
```

Disables listening for the input method subtype setting event. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'setSubtype' | Yes | Event type, which is **'setSubtype'**. |
| callback | (inputMethodSubtype: InputMethodSubtype) =&gt; void | No | Callback to unregister. If this parameter is not specified, this API unregisters all callbacks for the specified type. |

## off('securityModeChange')

```TypeScript
off(type: 'securityModeChange', callback?: Callback<SecurityMode>): void
```

Disables listening for the security mode changes of the input method. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'securityModeChange' | Yes | Event type, which is **'securityModeChange'**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SecurityMode](arkts-ime-inputmethodengine-securitymode-e.md)&gt; | No | Callback to unregister. If this parameter is not specified, this API unregisters all callbacks for the specified type. |

## off('privateCommand')

```TypeScript
off(type: 'privateCommand', callback?: Callback<Record<string, CommandDataType>>): void
```

Disables listening for the private data event of the input method. This API uses an asynchronous callback to return the result.

**Since:** 12

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'privateCommand' | Yes | Event type, which is **'privateCommand'**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Record&lt;string, [CommandDataType](arkts-ime-inputmethodengine-commanddatatype-t.md)&gt;&gt; | No | Callback to unregister. If this parameter is not specified, this API unregisters all callbacks for the specified type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800010](../errorcode-inputmethod-framework.md#12800010-not-preconfigured-default-input-method) | not the preconfigured default input method. |

## off('callingDisplayDidChange')

```TypeScript
off(type: 'callingDisplayDidChange', callback?: Callback<number>): void
```

Disables listening for changes of the screen ID of the window associated with the edit box. This API uses an asynchronous callback to return the result.

**Since:** 18

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'callingDisplayDidChange' | Yes | Event type, which is **'callingDisplayDidChange'**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | Callback to unregister. If this parameter is not specified, this API unregisters all callbacks for the specified type. |

## off('discardTypingText')

```TypeScript
off(type: 'discardTypingText', callback?: Callback<void>): void
```

Unsubscribes from the event of discarding candidate words and sends the event to the input method. This API uses an asynchronous callback to return the result.

**Since:** 20

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'discardTypingText' | Yes | Event type, which is **'discardTypingText'**.<br> - **'discardTypingText'**: indicates unsubscribing from the event of discarding candidate words and sending the event to the input method. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | Callback to unregister. If this parameter is not specified, this API unregisters all callbacks for the specified type. |

## on('inputStart')

```TypeScript
on(type: 'inputStart', callback: (kbController: KeyboardController, inputClient: InputClient) => void): void
```

Enables listening for the input method binding event. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'inputStart' | Yes | Event type, which is **'inputStart'**. |
| callback | (kbController: KeyboardController, inputClient: InputClient) =&gt; void | Yes | Callback used to return instances related to input method operations. |

## on('inputStop')

```TypeScript
on(type: 'inputStop', callback: () => void): void
```

Enables listening for the input method unbinding event. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'inputStop' | Yes | Event type, which is **'inputStop'**. |
| callback | () =&gt; void | Yes | Callback used to return the result. |

## on('setCallingWindow')

```TypeScript
on(type: 'setCallingWindow', callback: (wid: number) => void): void
```

Enables listening for the window invocation setting event. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'setCallingWindow' | Yes | Event type, which is **'setCallingWindow'**. |
| callback | (wid: number) =&gt; void | Yes | Callback used to return the window ID of the caller. |

## on('keyboardShow' | 'keyboardHide')

```TypeScript
on(type: 'keyboardShow' | 'keyboardHide', callback: () => void): void
```

Enables listening for a keyboard visibility event. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyboardShow' &#124; 'keyboardHide' | Yes | Event type.<br>- The value **'keyboardShow'** indicates the keyboard display event. <br>- The value **'keyboardHide'** indicates the keyboard hiding event. |
| callback | () =&gt; void | Yes | Callback used to return the result. |

## on('keyboardShow' | 'keyboardHide')

```TypeScript
on(type: 'keyboardShow' | 'keyboardHide', callback: () => void): void
```

Enables listening for a keyboard visibility event. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyboardShow' &#124; 'keyboardHide' | Yes | Event type.<br>- The value **'keyboardShow'** indicates the keyboard display event. <br>- The value **'keyboardHide'** indicates the keyboard hiding event. |
| callback | () =&gt; void | Yes | Callback used to return the result. |

## on('setSubtype')

```TypeScript
on(type: 'setSubtype', callback: (inputMethodSubtype: InputMethodSubtype) => void): void
```

Enables listening for the input method subtype setting event. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'setSubtype' | Yes | Event type, which is **'setSubtype'**. |
| callback | (inputMethodSubtype: InputMethodSubtype) =&gt; void | Yes | Callback used to return the input method subtype. |

## on('securityModeChange')

```TypeScript
on(type: 'securityModeChange', callback: Callback<SecurityMode>): void
```

Enables listening for the security mode changes of the input method. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'securityModeChange' | Yes | Event type, which is **'securityModeChange'**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SecurityMode](arkts-ime-inputmethodengine-securitymode-e.md)&gt; | Yes | Callback used to return the current security mode. |

## on('privateCommand')

```TypeScript
on(type: 'privateCommand', callback: Callback<Record<string, CommandDataType>>): void
```

Enables listening for the private data event of the input method. This API uses an asynchronous callback to return the result.

**Since:** 12

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'privateCommand' | Yes | Event type, which is **'privateCommand'**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Record&lt;string, [CommandDataType](arkts-ime-inputmethodengine-commanddatatype-t.md)&gt;&gt; | Yes | Callback used to return the private data sent to the input method application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800010](../errorcode-inputmethod-framework.md#12800010-not-preconfigured-default-input-method) | not the preconfigured default input method. |

## on('callingDisplayDidChange')

```TypeScript
on(type: 'callingDisplayDidChange', callback: Callback<number>): void
```

Enables listening for changes of the screen ID of the window associated with the edit box. This API uses an asynchronous callback to return the result.

**Since:** 18

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'callingDisplayDidChange' | Yes | Event type, which is **'callingDisplayDidChange'**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback used to return the screen ID of the window corresponding to the edit box. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

## on('discardTypingText')

```TypeScript
on(type: 'discardTypingText', callback: Callback<void>): void
```

Subscribes to the event of discarding candidate words and sends the event to the input method. This API uses an asynchronous callback to return the result.

**Since:** 20

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'discardTypingText' | Yes | Event type, which is **'discardTypingText'**.<br> - **'discardTypingText'**: indicates subscribing to the event of discarding candidate words and sending the event to the input method. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |
