# CommonOptions

```TypeScript
declare class CommonOptions
```

Defines the common attributes and events of the **Counter** component.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CounterComponent, CounterOptions, CounterType, DateData } from '@kit.ArkUI';
```

## onHoverDecrease

```TypeScript
onHoverDecrease?: (isHover: boolean) => void
```

Callback triggered when the mouse enters or leaves the decrease button of the Counter.

Use case: pass in this callback when you need to perform custom operations (such as changing the button style or displaying a tooltip) when the mouse hovers over the decrease button.

**isHover**: whether the mouse hovers over the decrease button. The value is **true** when the mouse enters and **false** when it leaves.

Default value: no callback is triggered when the mouse enters or leaves the decrease button of the Counter.

If the value is **undefined**, the default value is used.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isHover | boolean | Yes |  |

## onHoverIncrease

```TypeScript
onHoverIncrease?: (isHover: boolean) => void
```

Callback triggered when the mouse enters or leaves the increase button of the Counter.

Use case: pass in this callback when you need to perform custom operations (such as changing the button style or displaying a tooltip) when the mouse hovers over the increase button.

**isHover**: whether the mouse hovers over the increase button. The value is **true** when the mouse enters and **false** when it leaves.

Default value: no callback is triggered when the mouse enters or leaves the increase button of the Counter.

If the value is **undefined**, the default value is used.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isHover | boolean | Yes |  |

## focusable

```TypeScript
focusable?: boolean
```

Whether the Counter can obtain focus.

**Note:** This attribute takes effect for the list and compact types of Counter, but not for the inline number and inline date types.

Default value: **true**.

**true**: The Counter can obtain focus (selected when the Counter needs to be operated via keyboard or focus navigation); **false**: The Counter cannot obtain focus (selected when focus interaction is not required).

If the value is **undefined**, the default value is used.

**Type:** boolean

**Default:** true

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## step

```TypeScript
step?: number
```

Step of the Counter. This is used when you need to quickly adjust the value (for example, by setting a step greater than the default value 1) or precisely control the amount of each change.

Value range: an integer greater than or equal to 1.

Default value: **1**.

If the value is out of range, the default value is used.

If the value is **undefined**, the default value is used.

**Type:** number

**Default:** 1

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
