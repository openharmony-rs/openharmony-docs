# Panel

```TypeScript
interface Panel
```

You need to use [createPanel](arkts-ime-inputmethodengine-inputmethodability-i.md#createpanel) to obtain the panel instance and then call the following APIs through the instance.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## adjustPanelRect

```TypeScript
adjustPanelRect(flag: PanelFlag, rect: PanelRect): void
```

Adjusts the panel rectangle. After the API is called, the adjust request is submitted to the input method framework, but the execution is not complete. <br> <br>  
> **NOTE:** <br>
> <br>
> This API applies only to the panels of the **SOFT_KEYBOARD** type in the **FLG_FIXED** or **FLG_FLOATING** state. <br>
> <br>
> This API returns the result synchronously. The return only indicates that the system receives the setting request, not that the setting is complete. <br>
> <br>
> When the **PanelFlag** of a smartphone is **FLG_FLOATING** and the panel width is between 0 and 288 vp, the function buttons at the bottom of the panel will dynamically adjust their size according to the panel width. To ensure the optimal user experience, it is recommended that the panel width be no less than 90 vp.

**Since:** 12

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| flag | [PanelFlag](arkts-ime-inputmethodengine-panelflag-e.md) | Yes | Type of the state of the target panel. It can be **FLG_FIXED** or **FLG_FLOATING**. |
| rect | [PanelRect](arkts-ime-inputmethodengine-panelrect-i.md) | Yes | Landscape rectangle and portrait rectangle of the target panel. For the panel of the fixed state, the height cannot exceed 70% of the screen height, and the width cannot exceed the screen width. For the panel of the floating state, the height cannot exceed the screen height, and the width cannot exceed the screen width. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800013](../errorcode-inputmethod-framework.md#12800013-window-manager-service-error) | window manager service error. |

**Examples**

```TypeScript
import { window } from '@kit.ArkUI';

let landscapeRect: window.Rect = {
  left: 100,
  top: 100,
  width: 400,
  height: 400
};

let portraitRect: window.Rect = {
  left: 200,
  top: 200,
  width: 300,
  height: 300
};

// Target panel status type.
let panelFlag: inputMethodEngine.PanelFlag = inputMethodEngine.PanelFlag.FLG_FIXED;
// X-coordinate, Y-coordinate, width, and height of the target panel in both landscape and portrait orientations.
let panelRect: inputMethodEngine.PanelRect = {
  landscapeRect: landscapeRect,
  portraitRect: portraitRect
};
panel.adjustPanelRect(panelFlag, panelRect);
```

<a id="adjustpanelrect-1"></a>

## adjustPanelRect

```TypeScript
adjustPanelRect(flag: PanelFlag, rect: EnhancedPanelRect): void
```

Adjusts the panel rectangle, and customizes the avoid area and touch area. <br> <br>  
> **NOTE:** <br>
> <br>
> This API applies only to the panels of the **SOFT_KEYBOARD** type in the **FLG_FIXED** or **FLG_FLOATING** state. This API is compatible with [adjustPanelRect](#adjustpanelrect). If the input parameter **rect** contains only the **landscapeRect** and **portraitRect** attributes, [adjustPanelRect](#adjustpanelrect) is called by default. <br>
> <br>
> This API returns the result synchronously. The return only indicates that the system receives the setting request, not that the setting is complete. <br>
> <br>
> When the **PanelFlag** of a smartphone is **FLG_FLOATING** and the panel width is between 0 and 288 vp, the function buttons at the bottom of the panel will dynamically adjust their size according to the panel width. To ensure the optimal user experience, it is recommended that the panel width be no less than 90 vp.

**Since:** 15

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| flag | [PanelFlag](arkts-ime-inputmethodengine-panelflag-e.md) | Yes | Type of the state of the target panel. It can be **FLG_FIXED** or **FLG_FLOATING**. |
| rect | [EnhancedPanelRect](arkts-ime-inputmethodengine-enhancedpanelrect-i.md) | Yes | The target panel rectangle, avoid area, and touch area. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800013](../errorcode-inputmethod-framework.md#12800013-window-manager-service-error) | window manager service error. |
| [12800017](../errorcode-inputmethod-framework.md#12800017-invalid-panel-type-or-panel-flag) | invalid panel type or panel flag. |

**Examples**

```TypeScript
import { window } from '@kit.ArkUI';

let landscapeRect1: window.Rect = {
  left: 300,
  top: 650,
  width: 2000,
  height: 500
};
let landscapeInputRegion: Array<window.Rect> = [landscapeRect1];

let portraitRect1: window.Rect = {
  left: 0,
  top: 1800,
  width: 1200,
  height: 800
}
let portraitInputRegion: Array<window.Rect> = [portraitRect1];
// Target panel status type.
let panelFlag: inputMethodEngine.PanelFlag = inputMethodEngine.PanelFlag.FLG_FIXED;
// Location, size, avoid area, and hot zone of the target panel in both landscape and portrait orientations.
let panelRect: inputMethodEngine.EnhancedPanelRect = {
  landscapeAvoidY: 650,
  landscapeInputRegion: landscapeInputRegion,
  portraitAvoidY: 1800,
  portraitInputRegion: portraitInputRegion,
  fullScreenMode: true
};
panel.adjustPanelRect(panelFlag, panelRect);
```

## changeFlag

```TypeScript
changeFlag(flag: PanelFlag): void
```

Changes the state type ([PanelFlag](arkts-ime-inputmethodengine-panelflag-e.md)) of this input method panel. This API only works for [SOFT_KEYBOARD](arkts-ime-inputmethodengine-paneltype-e.md) panels.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| flag | [PanelFlag](arkts-ime-inputmethodengine-panelflag-e.md) | Yes | Type of the state of the target panel. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**Examples**

```TypeScript
let panelFlag: inputMethodEngine.PanelFlag = inputMethodEngine.PanelFlag.FLG_FIXED;
panel.changeFlag(panelFlag);
```

## getDisplayId

```TypeScript
getDisplayId(): Promise<number>
```

Obtains the window ID. This API uses a promise to return the result.

**Since:** 15

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the result. It returns **displayId** of the window. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800002](../errorcode-inputmethod-framework.md#12800002-input-method-engine-error) | input method engine error. Possible causes: 1.input method panel not created. 2.the input method application does not subscribe to related events. |
| [12800013](../errorcode-inputmethod-framework.md#12800013-window-manager-service-error) | window manager service error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

panel.getDisplayId().then((result: number) => {
  console.info('get displayId:' + result);
}).catch((err: BusinessError) => {
  console.error(`Failed to get displayId. Code is ${err.code}, message is ${err.message}`);
});
```

## getImmersiveMode

```TypeScript
getImmersiveMode(): ImmersiveMode
```

Obtains the immersive mode of the input method application.

**Since:** 15

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| [ImmersiveMode](arkts-ime-inputmethodengine-immersivemode-e.md) | Immersive mode. |

**Examples**

```TypeScript
let mode: inputMethodEngine.ImmersiveMode = panel.getImmersiveMode();
```

## getSystemPanelCurrentInsets

```TypeScript
getSystemPanelCurrentInsets(displayId: number): Promise<SystemPanelInsets>
```

Obtains the offset area of the soft keyboard relative to the system panel under the current state of the specified screen (for example, folded or unfolded) and the current state of the input method keyboard (for example, floating or fixed). This API uses a promise to return the result.

**Since:** 21

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| displayId | number | Yes | Display ID of the screen where the input method keyboard is located. It can be obtained by calling [getDisplayId](#getdisplayid). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SystemPanelInsets](arkts-ime-inputmethodengine-systempanelinsets-i.md)&gt; | Promise used to return the offset area between the input method keyboard and the system panel. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800013](../errorcode-inputmethod-framework.md#12800013-window-manager-service-error) | window manager service error. |
| [12800017](../errorcode-inputmethod-framework.md#12800017-invalid-panel-type-or-panel-flag) | invalid panel type or panel flag. Possible causes: 1. Current panel's type is not SOFT_KEYBOARD. 2. Panel's flag is not FLG_FIXED or FLG_FLOATING. |
| [12800022](../errorcode-inputmethod-framework.md#12800022-invalid-displayid) | invalid displayId. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMethodEngine } from '@kit.IMEKit';

let inputMethodAbility: inputMethodEngine.InputMethodAbility = inputMethodEngine.getInputMethodAbility();
let panelConfig: inputMethodEngine.PanelInfo = {
  type: inputMethodEngine.PanelType.SOFT_KEYBOARD,
  flag: inputMethodEngine.PanelFlag.FLG_FIXED
}
// The following logic needs to be executed in InputMethodExtensionAbility. this.context is the context of InputMethodExtensionAbility.
inputMethodAbility.createPanel(this.context, panelConfig).then( (panel: inputMethodEngine.Panel) =>{
  panel.getDisplayId().then((displayId: number) => {
    panel.getSystemPanelCurrentInsets(displayId).then((insets: inputMethodEngine.SystemPanelInsets) => {
      console.info(`getSystemPanelCurrentInsets success, insets is { left: ${insets.left}, right: ${insets.right}, bottom: ${insets.bottom} }`);
    }).catch((error: BusinessError) => {
      console.error(`getSystemPanelCurrentInsets failed, code: ${error.code}, message: ${error.message}`);
    })
  });
})
```

## hide

```TypeScript
hide(callback: AsyncCallback<void>): void
```

Hides this panel. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

panel.hide((err: BusinessError) => {
  if (err) {
    console.error(`Failed to hide panel. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in hiding the panel.');
});
```

<a id="hide-1"></a>

## hide

```TypeScript
hide(): Promise<void>
```

Hides this panel. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

panel.hide().then(() => {
  console.info('Succeeded in hiding the panel.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hide panel. Code is ${err.code}, message is ${err.message}`);
});
```

## moveTo

```TypeScript
moveTo(x: number, y: number, callback: AsyncCallback<void>): void
```

Moves this input method panel to the specified position. This API uses an asynchronous callback to return the result. This API does not work on panels in the [FLG_FIXED](arkts-ime-inputmethodengine-panelflag-e.md) state.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Distance to move along the horizontal axis, in px. A positive value indicates moving rightwards. The value must be an integer. |
| y | number | Yes | Distance to move along the vertical axis, in px. A positive value indicates moving downwards. The value must be an integer. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

panel.moveTo(300, 300, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to move panel. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in moving the panel.');
});
```

<a id="moveto-1"></a>

## moveTo

```TypeScript
moveTo(x: number, y: number): Promise<void>
```

Moves this input method panel to the specified position. This API uses a promise to return the result. This API does not work on panels in the [FLG_FIXED](arkts-ime-inputmethodengine-panelflag-e.md) state.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Distance to move along the horizontal axis, in px. A positive value indicates moving rightwards. The value must be an integer. |
| y | number | Yes | Distance to move along the vertical axis, in px. A positive value indicates moving downwards. The value must be an integer. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

panel.moveTo(300, 300).then(() => {
  console.info('Succeeded in moving the panel.');
}).catch((err: BusinessError) => {
  console.error(`Failed to move panel. Code is ${err.code}, message is ${err.message}`);
});
```

## off('show')

```TypeScript
off(type: 'show', callback?: () => void): void
```

Disables listening for the show event of this panel. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'show' | Yes | Event type, which is **'show'**. |
| callback | () =&gt; void | No | Callback to unregister. If this parameter is not specified, this API unregisters all callbacks for the specified type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**Examples**

```TypeScript
panel.off('show');
```

## off('hide')

```TypeScript
off(type: 'hide', callback?: () => void): void
```

Disables listening for the hide event of this panel. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'hide' | Yes | Event type, which is **'hide'**. |
| callback | () =&gt; void | No | Callback to unregister. If this parameter is not specified, this API unregisters all callbacks for the specified type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**Examples**

```TypeScript
panel.off('hide');
```

## off('sizeChange')

```TypeScript
off(type: 'sizeChange', callback?: SizeChangeCallback): void
```

Disables listening for the panel size change. This API uses an asynchronous callback to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> This API applies only to the panels of the **SOFT_KEYBOARD** type in the **FLG_FIXED** or **FLG_FLOATING** state. When you call **adjustPanelRect** to adjust the panel size, the system calculates the final value based on certain rules (for example, whether the panel size exceeds the screen). This callback can be used to obtain the actual panel size to refresh the panel layout. <br>
> <br>
> - This API is supported from API version 12 to 14. The callback function of this API contains only mandatory parameters of the [window.Size](../../apis-arkui/arkts-apis/arkts-arkui-window-size-i.md) type. <br><br>
> - Since API version 15, after the [adjustPanelRect](#adjustpanelrect-1) API is called, an optional parameter of the [KeyboardArea](arkts-ime-inputmethodengine-keyboardarea-i.md) type is added to the callback function of this API.

**Since:** 12

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'sizeChange' | Yes | Event type, which is **'sizeChange'**. |
| callback | [SizeChangeCallback](arkts-ime-inputmethodengine-sizechangecallback-t.md) | No | Callback used to return the size of the soft keyboard panel, including the width and height.<br>**Since:** 15 |

**Examples**

```TypeScript
import { window } from '@kit.ArkUI';

panel.off('sizeChange', (windowSize: window.Size) => {
  console.info(`panel size changed, width: ${windowSize.width}, height: ${windowSize.height}`);
});
```

## on('show')

```TypeScript
on(type: 'show', callback: () => void): void
```

Enables listening for the show event of this panel. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'show' | Yes | Event type, which is **'show'**. |
| callback | () =&gt; void | Yes | Callback used to return the result. |

**Examples**

```TypeScript
panel.on('show', () => {
  console.info('Panel is showing.');
});
```

## on('hide')

```TypeScript
on(type: 'hide', callback: () => void): void
```

Enables listening for the hide event of this panel. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'hide' | Yes | Event type, which is **'hide'**. |
| callback | () =&gt; void | Yes | Callback used to return the result. |

**Examples**

```TypeScript
panel.on('hide', () => {
  console.info('Panel is hiding.');
});
```

## on('sizeChange')

```TypeScript
on(type: 'sizeChange', callback: SizeChangeCallback): void
```

Enables listening for the panel size change. This API uses an asynchronous callback to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> This API applies only to the panels of the **SOFT_KEYBOARD** type in the **FLG_FIXED** or **FLG_FLOATING** state. When you call **adjustPanelRect** to adjust the panel size, the system calculates the final value based on certain rules (for example, whether the panel size exceeds the screen). This callback can be used to obtain the actual panel size to refresh the panel layout. <br>
> <br>
> - This API is supported from API version 12 to 14. The callback function of this API contains only mandatory <br>parameters of the [window.Size](../../apis-arkui/arkts-apis/arkts-arkui-window-size-i.md) type. <br><br>
> - Since API version 15, after the [adjustPanelRect](#adjustpanelrect-1) API is called, an optional parameter of the [KeyboardArea](arkts-ime-inputmethodengine-keyboardarea-i.md) type is added to the callback function of this API.

**Since:** 12

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'sizeChange' | Yes | Event type, which is **'sizeChange'**. |
| callback | [SizeChangeCallback](arkts-ime-inputmethodengine-sizechangecallback-t.md) | Yes | Callback used to return the size of the soft keyboard panel, including the width and height.<br>**Since:** 15 |

**Examples**

```TypeScript
import { window } from '@kit.ArkUI';

panel.on('sizeChange', (windowSize: window.Size) => {
  console.info(`panel size changed, width: ${windowSize.width}, height: ${windowSize.height}`);
});

panel.on('sizeChange', (windowSize: window.Size, keyboardArea: inputMethodEngine.KeyboardArea) => {
  console.info(`panel size changed, windowSize: ${windowSize.width}, ${windowSize.height}, ` +
    `keyboardArea: ${keyboardArea.top}, ${keyboardArea.bottom}, ${keyboardArea.left}, ${keyboardArea.right}`);
});
```

## resize

```TypeScript
resize(width: number, height: number, callback: AsyncCallback<void>): void
```

Resizes this input method panel. This API uses an asynchronous callback to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> The panel width cannot exceed the screen width, and the panel height cannot be 0.7 times higher than the screen height. <br>
> <br>
> When the **PanelFlag** of a smartphone is **FLG_FLOATING** and the panel width is between 0 and 288 vp, the function buttons at the bottom of the panel will dynamically adjust their size according to the panel width. To ensure the optimal user experience, it is recommended that the panel width be no less than 90 vp.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | Target width of the panel, in px. The value is an integer greater than or equal to 0, and cannot be greater than the screen width. |
| height | number | Yes | Target height of the panel, in px. The value is an integer greater than or equal to 0, and cannot be greater than 0.7 times the screen height. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

panel.resize(500, 1000, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to resize panel. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in changing the panel size.');
});
```

<a id="resize-1"></a>

## resize

```TypeScript
resize(width: number, height: number): Promise<void>
```

Resizes this input method panel. This API uses a promise to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> The panel width cannot exceed the screen width, and the panel height cannot be 0.7 times higher than the screen height. <br>
> <br>
> When the **PanelFlag** of a smartphone is **FLG_FLOATING** and the panel width is between 0 and 288 vp, the function buttons at the bottom of the panel will dynamically adjust their size according to the panel width. To ensure the optimal user experience, it is recommended that the panel width be no less than 90 vp.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | Target width of the panel, in px. The value is an integer greater than or equal to 0, and cannot be greater than the screen width. |
| height | number | Yes | Target height of the panel, in px. The value is an integer greater than or equal to 0, and cannot be greater than 0.7 times the screen height. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

panel.resize(500, 1000).then(() => {
  console.info('Succeeded in changing the panel size.');
}).catch((err: BusinessError) => {
  console.error(`Failed to resize panel. Code is ${err.code}, message is ${err.message}`);
});
```

## setImmersiveEffect

```TypeScript
setImmersiveEffect(effect: ImmersiveEffect): void
```

Sets the immersive effect of the input method application. <br> <br>- Gradient mode and fluid light mode can be used only when the [immersive mode](#setimmersivemode) is enabled. <br>- The fluid light mode can be used only when the gradient mode is enabled. <br>- If the gradient mode is disabled, the gradient height must be 0 px. <br>- Only system applications can set the fluid light mode. <br>- The current API can be called only after any of the following APIs is called: <br> - [adjustPanelRect](#adjustpanelrect) (available since API version 12) <br> - [adjustPanelRect](#adjustpanelrect-1) (available since API version 15) <br> - [resize](#resize) (available since API version 10)

**Since:** 20

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| effect | [ImmersiveEffect](arkts-ime-inputmethodengine-immersiveeffect-i.md) | Yes | Immersive effect. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [12800002](../errorcode-inputmethod-framework.md#12800002-input-method-engine-error) | input method engine error. Possible causes: 1. input method panel not created. 2. the input method application does not subscribe to related events. |
| [12800013](../errorcode-inputmethod-framework.md#12800013-window-manager-service-error) | window manager service error. |
| [12800020](../errorcode-inputmethod-framework.md#12800020-immersive-effect-parameter-configuration-error) | invalid immersive effect. 1. The gradient mode and the fluid light mode can only be used when the immersive mode is enabled. 2. The fluid light mode can only be used when the gradient mode is enabled. 3. When the gradient mode is not enabled, the gradient height can only be 0. |
| [12800021](../errorcode-inputmethod-framework.md#12800021-incorrect-call-sequence) | this operation is allowed only after adjustPanelRect or resize is called. |

**Examples**

```TypeScript
let effect: inputMethodEngine.ImmersiveEffect = {
  gradientHeight: 100,
  gradientMode: inputMethodEngine.GradientMode.LINEAR_GRADIENT
}
panel.setImmersiveEffect(effect);
```

## setImmersiveMode

```TypeScript
setImmersiveMode(mode: ImmersiveMode): void
```

Sets the immersive mode of the input method application. You can only set the immersion mode to **NONE_IMMERSIVE**, **LIGHT_IMMERSIVE**, or **DARK_IMMERSIVE**. **IMMERSIVE** cannot be set.

**Since:** 15

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [ImmersiveMode](arkts-ime-inputmethodengine-immersivemode-e.md) | Yes | Immersive mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [12800002](../errorcode-inputmethod-framework.md#12800002-input-method-engine-error) | input method engine error. Possible causes: 1.input method panel not created. 2.the input method application does not subscribe to related events. |
| [12800013](../errorcode-inputmethod-framework.md#12800013-window-manager-service-error) | window manager service error. |

**Examples**

```TypeScript
panel.setImmersiveMode(inputMethodEngine.ImmersiveMode.LIGHT_IMMERSIVE);
```

## setKeepScreenOn

```TypeScript
setKeepScreenOn(isKeepScreenOn: boolean): Promise<void>
```

Sets to keep the screen always on. This API uses a promise to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> - When the keyboard is displayed, the screen stays on. When the keyboard is hidden, the screen turns off. <br><br>
> - You need to use this API properly. Set the attribute to **true** in necessary scenarios (for example, voice input) and reset this attribute to **false** after exiting necessary scenarios. In other scenarios, do not use this API.

**Since:** 20

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isKeepScreenOn | boolean | Yes | Whether to keep the screen always on. The value **true** means that the screen is always on; the value **false** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800013](../errorcode-inputmethod-framework.md#12800013-window-manager-service-error) | window manager service error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

panel.setKeepScreenOn(true).then(() => {
  console.info(`setKeepScreenOn success.`);
}).catch((error: BusinessError) => {
  console.error(`setKeepScreenOn failed, code: ${error.code}, message: ${error.message}`);
})
```

## setPrivacyMode

```TypeScript
setPrivacyMode(isPrivacyMode: boolean): void
```

Sets the input method panel to privacy mode. In privacy mode, screenshot and screen recording are blocked.

**Since:** 11

**Required permissions:** ohos.permission.PRIVACY_WINDOW

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isPrivacyMode | boolean | Yes | Whether to set the input method panel to privacy mode.<br>- **true**: privacy mode. <br>- **false**: non-privacy mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

```TypeScript
let isPrivacyMode: boolean = true;
panel.setPrivacyMode(isPrivacyMode);
```

## setSystemPanelButtonColor

```TypeScript
setSystemPanelButtonColor(fillColor: string | undefined, backgroundColor: string | undefined): Promise<void>
```

Sets the color of the function buttons and their background color on the current panel. This API uses a promise to return the result.

**Since:** 22

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fillColor | string &#124; undefined | Yes | Color of the function buttons. The value can be [#01000000, #FFFFFFFF] or [#000000, #FFFFFF]. The value of the fully transparent alpha channel (**#00xxxxxx**) is not supported. |
| backgroundColor | string &#124; undefined | Yes | Background color of the function buttons. The value can be [#01000000, #FFFFFFFF] or [#000000, #FFFFFF]. The value of the fully transparent alpha channel (#00xxxxxx) is not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let fillColor = "#FFFF00";
  let backgroundColor = "#0000FF";
  this.panel.setSystemPanelButtonColor(fillColor, backgroundColor).then(() => {
    console.info(`setSystemPanelButtonColor success.`);
  }).catch((error: BusinessError) => {
    console.error(`setSystemPanelButtonColor failed, code: ${error.code}, message: ${error.message}`);
  })
} catch (err) {
  let error = err as BusinessError;
  console.error(`setSystemPanelButtonColor failed, code: ${error.code}, message: ${error.message}`);
}
```

## setUiContent

```TypeScript
setUiContent(path: string, callback: AsyncCallback<void>): void
```

Loads content from a page to this input method panel. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the page from which the content will be loaded. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

panel.setUiContent('pages/page2/page2', (err: BusinessError) => {
  if (err) {
    console.error(`Failed to setUiContent. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in setting the content.');
});
```

<a id="setuicontent-1"></a>

## setUiContent

```TypeScript
setUiContent(path: string): Promise<void>
```

Loads content from a page to this input method panel. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the page from which the content will be loaded. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

panel.setUiContent('pages/page2/page2').then(() => {
  console.info('Succeeded in setting the content.');
}).catch((err: BusinessError) => {
  console.error(`Failed to setUiContent. Code is ${err.code}, message is ${err.message}`);
});
```

<a id="setuicontent-2"></a>

## setUiContent

```TypeScript
setUiContent(path: string, storage: LocalStorage, callback: AsyncCallback<void>): void
```

Loads content from a page linked to LocalStorage to this input method panel. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the page linked to LocalStorage. |
| storage | LocalStorage | Yes | Storage unit that provides storage for mutable and immutable state variables in the application. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let storage: LocalStorage = new LocalStorage();
storage.setOrCreate('storageSimpleProp', 121);
panel.setUiContent('pages/page2/page2', storage, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to setUiContent. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in setting the content.');
});
```

<a id="setuicontent-3"></a>

## setUiContent

```TypeScript
setUiContent(path: string, storage: LocalStorage): Promise<void>
```

Loads content from a page linked to LocalStorage to this panel. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the page from which the content will be loaded. |
| storage | LocalStorage | Yes | Storage unit that provides storage for mutable and immutable state variables in the application. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let storage: LocalStorage = new LocalStorage();
storage.setOrCreate('storageSimpleProp', 121);
panel.setUiContent('pages/page2/page2', storage).then(() => {
  console.info('Succeeded in setting the content.');
}).catch((err: BusinessError) => {
  console.error(`Failed to setUiContent. Code is ${err.code}, message is ${err.message}`);
});
```

## show

```TypeScript
show(callback: AsyncCallback<void>): void
```

Shows this input method panel. This API uses an asynchronous callback to return the result. It can be called when the input method is bound to the edit box.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

panel.show((err: BusinessError) => {
  if (err) {
    console.error(`Failed to show panel. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in showing the panel.');
});
```

<a id="show-1"></a>

## show

```TypeScript
show(): Promise<void>
```

Shows this input method panel. This API uses a promise to return the result. It can be called when the input method is bound to the edit box.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

panel.show().then(() => {
  console.info('Succeeded in showing the panel.');
}).catch((err: BusinessError) => {
  console.error(`Failed to show panel. Code is ${err.code}, message is ${err.message}`);
});
```

## startMoving

```TypeScript
startMoving(): void
```

Sends a command to start moving the window. The window can be moved only when the mouse is clicked.

**Since:** 15

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800002](../errorcode-inputmethod-framework.md#12800002-input-method-engine-error) | input method engine error. Possible causes: 1.input method panel not created. 2.the input method application does not subscribe to related events. |
| [12800013](../errorcode-inputmethod-framework.md#12800013-window-manager-service-error) | window manager service error. |
| [12800017](../errorcode-inputmethod-framework.md#12800017-invalid-panel-type-or-panel-flag) | invalid panel type or panel flag. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported.<br>**Applicable version:** 18 and later |

**Examples**

```TypeScript
panel.startMoving();
```

## updatePanelRect

```TypeScript
updatePanelRect(flag: PanelFlag, rect: PanelRect): Promise<void>
```

Update the panel rectangle. This API uses a promise to return the result. <br>  
> **NOTE:** <br>
> <br>
> This API applies only to the panels of the **SOFT_KEYBOARD** type in the **FLG_FIXED** or **FLG_FLOATING** state. <br>
> <br>
> When the **PanelFlag** of a smartphone is **FLG_FLOATING** and the panel width is between 0 and 288 vp, the function buttons at the bottom of the panel will dynamically update their size according to the panel width. To ensure the optimal user experience, it is recommended that the panel width be no less than 90 vp.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| flag | [PanelFlag](arkts-ime-inputmethodengine-panelflag-e.md) | Yes | Type of the state of the target panel. It can be **FLG_FIXED** or **FLG_FLOATING**. |
| rect | [PanelRect](arkts-ime-inputmethodengine-panelrect-i.md) | Yes | Landscape rectangle and portrait rectangle of the target panel. For the panel of the fixed state, the height cannot exceed 70% of the screen height, and the width cannot exceed the screen width. For the panel of the floating state, the height cannot exceed the screen height, and the width cannot exceed the screen width. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800013](../errorcode-inputmethod-framework.md#12800013-window-manager-service-error) | window manager service error. |

<a id="updatepanelrect-1"></a>

## updatePanelRect

```TypeScript
updatePanelRect(flag: PanelFlag, rect: EnhancedPanelRect): Promise<void>
```

Update the panel rectangle, and customizes the avoid area and touch area. This API uses a promise to return the result. <br>  
> **NOTE:** <br>
> <br>
> This API applies only to the panels of the **SOFT_KEYBOARD** type in the **FLG_FIXED** or **FLG_FLOATING** state. This API is compatible with [updatePanelRect](#updatepanelrect). If the input parameter **rect** contains only the **landscapeRect** and **portraitRect** attributes, [updatePanelRect](#updatepanelrect) is called by default. <br>
> <br>
> When the **PanelFlag** of a smartphone is **FLG_FLOATING** and the panel width is between 0 and 288 vp, the function buttons at the bottom of the panel will dynamically update their size according to the panel width. To ensure the optimal user experience, it is recommended that the panel width be no less than 90 vp.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| flag | [PanelFlag](arkts-ime-inputmethodengine-panelflag-e.md) | Yes | Type of the state of the target panel. It can be **FLG_FIXED** or **FLG_FLOATING**. |
| rect | [EnhancedPanelRect](arkts-ime-inputmethodengine-enhancedpanelrect-i.md) | Yes | The target panel rectangle, avoid area, and touch area. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800013](../errorcode-inputmethod-framework.md#12800013-window-manager-service-error) | window manager service error. |
| [12800017](../errorcode-inputmethod-framework.md#12800017-invalid-panel-type-or-panel-flag) | invalid panel type or panel flag. |

## updatePanelRectSync

```TypeScript
updatePanelRectSync(flag: PanelFlag, rect: PanelRect): void
```

Update the panel rectangle. <br>  
> **NOTE:** <br>
> <br>
> This API applies only to the panels of the **SOFT_KEYBOARD** type in the **FLG_FIXED** or **FLG_FLOATING** state. <br>
> <br>
> When the **PanelFlag** of a smartphone is **FLG_FLOATING** and the panel width is between 0 and 288 vp, the function buttons at the bottom of the panel will dynamically update their size according to the panel width. To ensure the optimal user experience, it is recommended that the panel width be no less than 90 vp.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| flag | [PanelFlag](arkts-ime-inputmethodengine-panelflag-e.md) | Yes | Type of the state of the target panel. It can be **FLG_FIXED** or **FLG_FLOATING**. |
| rect | [PanelRect](arkts-ime-inputmethodengine-panelrect-i.md) | Yes | Landscape rectangle and portrait rectangle of the target panel. For the panel of the fixed state, the height cannot exceed 70% of the screen height, and the width cannot exceed the screen width. For the panel of the floating state, the height cannot exceed the screen height, and the width cannot exceed the screen width. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800013](../errorcode-inputmethod-framework.md#12800013-window-manager-service-error) | window manager service error. |

<a id="updatepanelrectsync-1"></a>

## updatePanelRectSync

```TypeScript
updatePanelRectSync(flag: PanelFlag, rect: EnhancedPanelRect): void
```

Update the panel rectangle, and customizes the avoid area and touch area. <br>  
> **NOTE:** <br>
> <br>
> This API applies only to the panels of the **SOFT_KEYBOARD** type in the **FLG_FIXED** or **FLG_FLOATING** state. This API is compatible with [updatePanelRectSync](#updatepanelrectsync). If the input parameter **rect** contains only the **landscapeRect** and **portraitRect** attributes, [updatePanelRectSync](#updatepanelrectsync) is called by default. <br>
> <br>
> When the **PanelFlag** of a smartphone is **FLG_FLOATING** and the panel width is between 0 and 288 vp, the function buttons at the bottom of the panel will dynamically update their size according to the panel width. To ensure the optimal user experience, it is recommended that the panel width be no less than 90 vp.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| flag | [PanelFlag](arkts-ime-inputmethodengine-panelflag-e.md) | Yes | Type of the state of the target panel. It can be **FLG_FIXED** or **FLG_FLOATING**. |
| rect | [EnhancedPanelRect](arkts-ime-inputmethodengine-enhancedpanelrect-i.md) | Yes | The target panel rectangle, avoid area, and touch area. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800013](../errorcode-inputmethod-framework.md#12800013-window-manager-service-error) | window manager service error. |
| [12800017](../errorcode-inputmethod-framework.md#12800017-invalid-panel-type-or-panel-flag) | invalid panel type or panel flag. |

## updateRegion

```TypeScript
updateRegion(inputRegion: Array<window.Rect>): void
```

Updates the hot zone on the input method panel in the current state. <br> <br>  
> **NOTE:** <br>
> <br>
> This API applies only to the panels of the **SOFT_KEYBOARD** type in the **FLG_FIXED** or **FLG_FLOATING** state. <br>
> <br>
> This API returns the result synchronously. The return only indicates that the system has received the request for updating the hot zone, not that the hot zone has been updated.

**Since:** 15

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inputRegion | Array&lt;[window.Rect](../../apis-arkui/arkts-apis/arkts-arkui-window-rect-i.md)&gt; | Yes | Region for receiving input events.<br>- The array size is limited to [1, 4]. <br>- The input hot zone is relative to the left vertex of the input method panel window. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800013](../errorcode-inputmethod-framework.md#12800013-window-manager-service-error) | window manager service error. |
| [12800017](../errorcode-inputmethod-framework.md#12800017-invalid-panel-type-or-panel-flag) | invalid panel type or panel flag. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

let inputRegion: Array<window.Rect> = [{
  left: 300,
  top: 650,
  width: 2000,
  height: 500
}];
panel.updateRegion(inputRegion);
```
