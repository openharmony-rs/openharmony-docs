# @ohos.inputMethodEngine (Input Method Service) (System API)
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=4c244f2ed12456a4c6059eccff764e442d7872b9 translatedAt=2026-09-02T11:45:25.921Z pushedAt=2026-09-08T07:14:44.470Z -->

This module provides management capabilities for system input method applications, including creating soft keyboard windows, inserting/deleting characters, selecting text, and listening for physical keyboard key events. It is suitable for scenarios that require custom input method interactions and can improve the input experience.

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
| size         | [window.Size](../apis-arkui/arkts-apis-window-i.md#size7) | Yes   | Current panel size, including width and height.                   |
| keyboardArea | [KeyboardArea](./js-apis-inputmethodengine.md#keyboardarea15)    | Yes   | Keyboard area size of the current panel. |

## Panel<sup>10+</sup>

You need to use [createPanel](./js-apis-inputmethodengine.md#createpanel10) to obtain the panel instance and then call the following APIs through the instance.

### on('sizeUpdate')<sup>14+</sup>

on(type: 'sizeUpdate', callback: SizeUpdateCallback): void

Listens for the current panel size change through the **Panel** instance, and asynchronously invokes the callback when the change occurs.

**Return value**

| Type | Description |
| --- | --- |
| void | No return value. Used to asynchronously register a listener for the current panel size change. |

> **NOTE**
>
> This API applies only to the panels of the **SOFT_KEYBOARD** type in the **FLG_FIXED** or **FLG_FLOATING** state. When the input method adjusts the panel size through APIs such as [adjustPanelRect](./js-apis-inputmethodengine.md#adjustpanelrect15), the system calculates the final value according to certain rules (for example, when the panel exceeds the screen). The input method application can obtain the final panel size through this callback to complete the final panel layout refresh.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Parameters**

| Name  | Type                                       | Mandatory| Description                                                  |
| -------- | ------------------------------------------- | ---- | ------------------------------------------------------ |
| type     | string                                      | Yes   | Event type, which is **'sizeUpdate'**. |
| callback | [SizeUpdateCallback](#sizeupdatecallback14) | Yes   | Callback invoked when the panel size changes. The parameters include the width and height of the current soft keyboard panel. |

**Example**

```ts
import { window } from '@kit.ArkUI';

// Listen for panel size changes.
panel.on('sizeUpdate', (windowSize: window.Size, keyboardArea: inputMethodEngine.KeyboardArea) => {
  // Print the panel size and keyboard area information.
  console.info(`panel size changed, windowSize: ${windowSize.width}, ${windowSize.height}, ` +
    `keyboardArea: ${keyboardArea.top}, ${keyboardArea.bottom}, ${keyboardArea.left}, ${keyboardArea.right}`);
});
```

### off('sizeUpdate')<sup>14+</sup>

off(type: 'sizeUpdate', callback?: SizeUpdateCallback): void

Cancels listening for the current panel size change through the **Panel** instance, and stops the asynchronous callback.

**Return value**

| Type | Description |
| --- | --- |
| void | No return value. Used to asynchronously cancel listening for the current panel size change event. |

> **NOTE**
>
> This API applies only to the panels of the **SOFT_KEYBOARD** type in the **FLG_FIXED** or **FLG_FLOATING** state.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Parameters**

| Name  | Type                                       | Mandatory| Description                                                    |
| -------- | ------------------------------------------- | ---- | -------------------------------------------------------- |
| type     | string                                      | Yes   | Cancels listening for whether the current panel size changes. The fixed value is **'sizeUpdate'**. |
| callback | [SizeUpdateCallback](#sizeupdatecallback14) | No   | Callback function. Specifies the callback to cancel. If it is not specified, all **sizeUpdate** listeners are canceled. |

**Example**

```ts
import { window } from '@kit.ArkUI';

// Cancel listening for panel size changes.
panel.off('sizeUpdate', (windowSize: window.Size, _keyboardArea: inputMethodEngine.KeyboardArea) => {
  // Print the panel width and height information.
  console.info(`panel size changed, width: ${windowSize.width}, height: ${windowSize.height}`);
});
```

### setShadow<sup>22+</sup>

setShadow(radius: number, color: string, offsetX: number, offsetY: number): void

Sets the shadow effect of the input method window through the **Panel** instance.

**Return value**

| Type | Description |
| --- | --- |
| void | No return value. Used to set the shadow effect of the input method window. |

> **NOTE**
>
> Panels whose [PanelType](./js-apis-inputmethodengine.md#paneltype10) is **SOFT_KEYBOARD** and [PanelFlag](./js-apis-inputmethodengine.md#panelflag10) is **FLG_FIXED** are not supported.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| radius  | number | Yes   | Blur radius of the window edge shadow, in px. The value range is [0.0, +∞). When the value is **0.0**, the window edge shadow is disabled. |
| color   | string | Yes   | Color of the window edge shadow, in hexadecimal RGB or ARGB format, case-insensitive, for example, `#000000` or `#FF000000`. |
| offsetX | number | Yes   | Offset of the window edge shadow along the X axis, in px. A positive value shifts the shadow to the right, and a negative value shifts it to the left. |
| offsetY | number | Yes   | Offset of the window edge shadow along the Y axis, in px. A positive value shifts the shadow downward, and a negative value shifts it upward. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Input Method Framework Error Codes](errorcode-inputmethod-framework.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 202 | not system application. |
| 12800013  | window manager service error.      |
| 12800017 | invalid panel type or panel flag. Possible causes: Panel's flag is FLG_FIXED. |

**Example**

```ts
// Set the shadow effect for the input method window, with a radius of 20 px, black color, and X/Y axis offsets of 20 px.
panel.setShadow(20, '#000000', 20, 20);
```
## FluidLightMode<sup>20+</sup>

Enumerates the fluid light modes of the input method.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

| Name        | Value| Description              |
| ------------ | -- | ------------------ |
| NONE | 0 | The fluid light mode is not used.|
| BACKGROUND_FLUID_LIGHT  | 1 | Enables the background fluid light mode. The system panel becomes transparent, and the fluid light effect is implemented by the host application of the edit box. |

## EditorAttribute<sup>20+</sup>

Describes the attribute of the edit box.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

| Name        | Type| Read-Only| Optional| Description              |
| ------------ | -------- | ---- | ---- | ------------------ |
| fluidLightMode | [FluidLightMode](#fluidlightmode20) | No | Yes | Fluid light mode. If this parameter is not set or is set to an invalid value, the fluid light mode is not used by default.<br>This attribute is available only to system applications.|

## ImmersiveEffect<sup>20+</sup>

Describes the immersive effect.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

| Name  | Type                                 | Read-Only| Optional| Description          |
| ------ | ------------------------------------ | ---- | ---- | -------------- |
| fluidLightMode | [FluidLightMode](#fluidlightmode20) | No   | Yes   | Fluid light mode. The default value is **NONE** when it is not filled in.<br>This attribute is available only to system applications. |
<!--no_check-->