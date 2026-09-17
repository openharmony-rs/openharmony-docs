# getFloatViewLimits

## Modules to Import

```TypeScript
import { floatView } from '@kit.ArkUI';
```

## getFloatViewLimits

```TypeScript
function getFloatViewLimits(templateType: FloatViewTemplateType): FloatViewLimits
```

Obtains the limits of the float view based on the passed template type. The unit is px.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| templateType | [FloatViewTemplateType](arkts-arkui-floatview-floatviewtemplatetype-e.md) | Yes | Template type of the float view. |

**Return value:**

| Type | Description |
| --- | --- |
| [FloatViewLimits](arkts-arkui-floatview-floatviewlimits-i.md) | Limits of the float view, including the maximum size, minimum size, and aspect ratio. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible cause: Call the API on unsupported device. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: System error, such as a null pointer, insufficient memory or a JS engine exception. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: Internal IPC error. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: Invalid template type. |

**Examples**

```TypeScript
// Obtain the float view limit of the rounded rectangle template.
let limits: floatView.FloatViewLimits = floatView.getFloatViewLimits(floatView.FloatViewTemplateType.ROUNDED_RECTANGLE);
console.info('Float view limits: ' + JSON.stringify(limits));
```
