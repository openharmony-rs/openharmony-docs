# @ohos.inputMethodEngine (Input Method Service) (System API)
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @illybyy-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->

The **inputMethodEngine** module provides management capabilities for system input method applications. With the APIs of this module, input method applications are able to create soft keyboard windows, insert or delete characters, select text, and listen for physical keyboard events.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { inputMethodEngine } from '@kit.IMEKit';
```

## SizeUpdateCallback<sup>14+</sup>

type SizeUpdateCallback = (size: window.Size, keyboardArea: KeyboardArea) => void

Callback triggered when the size of the input method panel changes.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Parameters**

| Name      | Type                                                | Mandatory| Description                            |
| ------------ | ---------------------------------------------------- | ---- | -------------------------------- |
| size         | [window.Size](../apis-arkui/arkts-apis-window-i.md#size7) | Yes  | Panel size.                  |
| keyboardArea | [KeyboardArea](./js-apis-inputmethodengine.md#keyboardarea15)    | Yes  | Size of the keyboard area.|

## Panel<sup>10+</sup>

You need to use [createPanel](./js-apis-inputmethodengine.md#createpanel10) to obtain the panel instance and then call the following APIs through the instance.

### on('sizeUpdate')<sup>14+</sup>

on(type: 'sizeUpdate', callback: SizeUpdateCallback): void

Listens for the panel size change. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API applies only to the panels of the **SOFT_KEYBOARD** type in the **FLG_FIXED** or **FLG_FLOATING** state. When you call [adjustPanelRect](./js-apis-inputmethodengine.md#adjustpanelrect15) to adjust the panel size, the system calculates the final value based on certain rules (for example, whether the panel size exceeds the screen). This callback can be used to obtain the actual panel size to refresh the panel layout.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Parameters**

| Name  | Type                                       | Mandatory| Description                                                  |
| -------- | ------------------------------------------- | ---- | ------------------------------------------------------ |
| type     | string                                      | Yes  | Event type, which is **'sizeUpdate'**.|
| callback | [SizeUpdateCallback](#sizeupdatecallback14) | Yes  | Callback used to return the size of the soft keyboard panel, including the width and height.|

**Example**

```ts
import { window } from '@kit.ArkUI';

panel.on('sizeUpdate', (windowSize: window.Size, keyboardArea: inputMethodEngine.KeyboardArea) => {
  console.info(`panel size changed, windowSize: ${windowSize.width}, ${windowSize.height}, ` +
    `keyboardArea: ${keyboardArea.top}, ${keyboardArea.bottom}, ${keyboardArea.left}, ${keyboardArea.right}`);
});
```

### off('sizeUpdate')<sup>14+</sup>

off(type: 'sizeUpdate', callback?: SizeUpdateCallback): void

Disables listening for the panel size change. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API applies only to the panels of the **SOFT_KEYBOARD** type in the **FLG_FIXED** or **FLG_FLOATING** state. When you call [adjustPanelRect](./js-apis-inputmethodengine.md#adjustpanelrect15) to adjust the panel size, the system calculates the final value based on certain rules (for example, whether the panel size exceeds the screen). This callback can be used to obtain the actual panel size to refresh the panel layout.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Parameters**

| Name  | Type                                       | Mandatory| Description                                                    |
| -------- | ------------------------------------------- | ---- | -------------------------------------------------------- |
| type     | string                                      | Yes  | Event type, which is **'sizeUpdate'**.|
| callback | [SizeUpdateCallback](#sizeupdatecallback14) | No  | Callback used to return the size of the soft keyboard panel, including the width and height.  |

**Example**

```ts
import { window } from '@kit.ArkUI';

panel.off('sizeUpdate', (windowSize: window.Size, keyboardArea: inputMethodEngine.KeyboardArea) => {
  console.info(`panel size changed, width: ${windowSize.width}, height: ${windowSize.height}`);
});
```

### setShadow<sup>22+</sup>

setShadow(radius: number, color: string, offsetX: number, offsetY: number): void

Sets the shadow effect of the input method window.

> **NOTE**
>
> Panels whose [PanelType](./js-apis-inputmethodengine.md#paneltype10) is **SOFT_KEYBOARD** and [PanelFlag](./js-apis-inputmethodengine.md#panelflag10) is **FLG_FIXED** are not supported.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| radius  | number | Yes  | Radius of the shadow. The value is a floating-point number greater than or equal to 0.0, in px. The value **0.0** means that the shadow is disabled for the window borders.|
| color   | string | Yes  | Color of the shadow. The value is a hexadecimal RGB or ARGB color code and is case insensitive, for example, `#000000` or `#FF000000`.|
| offsetX | number | Yes  | Offset of the shadow along the x-axis, in pixels. The value is a floating-point number.   |
| offsetY | number | Yes  | Offset of the shadow along the y-axis, in pixels. The value is a floating-point number.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Input Method Framework Error Codes](errorcode-inputmethod-framework.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 202 | not system application. |
| 12800013  | window manager service error.      |
| 12800017 | invalid panel type or panel flag. Possible causes: Panel's flag is FLG_FIXED. |

**Example**

```ts
panel.setShadow(20, '#000000', 20, 20);
```
## FluidLightMode<sup>20+</sup>

Enumerates the fluid light modes of the input method.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

| Name        | Value| Description              |
| ------------ | -- | ------------------ |
| NONE | 0 | The fluid light mode is not used.|
| BACKGROUND_FLUID_LIGHT  | 1 | When the background fluid light mode is enabled, the system panel turns transparent. The fluid light effect must be implemented by the host application of the edit box.|

## EditorAttribute<sup>20+</sup>

Describes the attribute of the edit box.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

| Name        | Type| Read-Only| Optional| Description              |
| ------------ | -------- | ---- | ---- | ------------------ |
| fluidLightMode | [FluidLightMode](#fluidlightmode20) | Yes| Yes| Fluid light mode. If this attribute is not specified or is set to an invalid value, the fluid light mode is not used by default.<br>This attribute is available only to system applications.|

## ImmersiveEffect<sup>20+</sup>

Describes the immersive effect.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

| Name  | Type                                 | Read-Only| Optional| Description          |
| ------ | ------------------------------------ | ---- | ---- | -------------- |
| fluidLightMode | [FluidLightMode](#fluidlightmode20) | No  | Yes  | Fluid light mode. If this attribute is not set, the default value is **NONE**.<br>This attribute is available only to system applications.|
<!--no_check-->
