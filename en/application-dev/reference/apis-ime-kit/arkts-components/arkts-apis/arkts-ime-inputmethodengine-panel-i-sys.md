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

## off('sizeUpdate')

```TypeScript
off(type: 'sizeUpdate', callback?: SizeUpdateCallback): void
```

Disables listening for the panel size change. This API uses an asynchronous callback to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> This API applies only to the panels of the **SOFT_KEYBOARD** type in the **FLG_FIXED** or **FLG_FLOATING** state. When you call [adjustPanelRect](arkts-ime-inputmethodengine-panel-i.md#adjustpanelrect-1) to adjust the panel size, the system calculates the final value based on certain rules (for example, whether the panel size exceeds the screen). This callback can be used to obtain the actual panel size to refresh the panel layout.

**Since:** 14

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'sizeUpdate' | Yes | Event type, which is **'sizeUpdate'**. |
| callback | [SizeUpdateCallback](arkts-ime-inputmethodengine-sizeupdatecallback-t-sys.md) | No | Callback used to return the size of the soft keyboard panel, including the width and height. |

**Examples**

```TypeScript
import { window } from '@kit.ArkUI';

panel.off('sizeUpdate', (windowSize: window.Size, keyboardArea: inputMethodEngine.KeyboardArea) => {
  console.info(`panel size changed, width: ${windowSize.width}, height: ${windowSize.height}`);
});
```

## on('sizeUpdate')

```TypeScript
on(type: 'sizeUpdate', callback: SizeUpdateCallback): void
```

Listens for the panel size change. This API uses an asynchronous callback to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> This API applies only to the panels of the **SOFT_KEYBOARD** type in the **FLG_FIXED** or **FLG_FLOATING** state. When you call [adjustPanelRect](arkts-ime-inputmethodengine-panel-i.md#adjustpanelrect-1) to adjust the panel size, the system calculates the final value based on certain rules (for example, whether the panel size exceeds the screen). This callback can be used to obtain the actual panel size to refresh the panel layout.

**Since:** 14

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'sizeUpdate' | Yes | Event type, which is **'sizeUpdate'**. |
| callback | [SizeUpdateCallback](arkts-ime-inputmethodengine-sizeupdatecallback-t-sys.md) | Yes | Callback used to return the size of the soft keyboard panel, including the width and height. |

**Examples**

```TypeScript
import { window } from '@kit.ArkUI';

panel.on('sizeUpdate', (windowSize: window.Size, keyboardArea: inputMethodEngine.KeyboardArea) => {
  console.info(`panel size changed, windowSize: ${windowSize.width}, ${windowSize.height}, ` +
    `keyboardArea: ${keyboardArea.top}, ${keyboardArea.bottom}, ${keyboardArea.left}, ${keyboardArea.right}`);
});
```

## setShadow

```TypeScript
setShadow(radius: number, color: string, offsetX: number, offsetY: number): void
```

Sets the shadow effect of the input method window. <br> <br>  
> **NOTE:** <br>
> <br>
> Panels whose [PanelType](arkts-ime-inputmethodengine-paneltype-e.md) is **SOFT_KEYBOARD** and [PanelFlag](arkts-ime-inputmethodengine-panelflag-e.md) is **FLG_FIXED** are not supported.

**Since:** 22

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| radius | number | Yes | Radius of the shadow. The value is a floating-point number greater than or equal to 0.0, in px. The value **0.0** means that the shadow is disabled for the window borders. |
| color | string | Yes | Color of the shadow. The value is a hexadecimal RGB or ARGB color code and is case insensitive, for example, `#000000` or `#FF000000`. |
| offsetX | number | Yes | Offset of the shadow along the x-axis, in pixels. The value is a floating-point number. |
| offsetY | number | Yes | Offset of the shadow along the y-axis, in pixels. The value is a floating-point number. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [12800013](../errorcode-inputmethod-framework.md#12800013-window-manager-service-error) | window manager service error. |
| [12800017](../errorcode-inputmethod-framework.md#12800017-invalid-panel-type-or-panel-flag) | invalid panel type or panel flag. Possible causes: Panel's flag is FLG_FIXED. |

**Examples**

```TypeScript
panel.setShadow(20, '#000000', 20, 20);
```
