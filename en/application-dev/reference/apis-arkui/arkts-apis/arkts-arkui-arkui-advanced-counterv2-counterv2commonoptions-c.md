# CounterV2CommonOptions

```TypeScript
declare class CounterV2CommonOptions
```

Defines the common attributes and events of the **CounterV2** component.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CounterV2Component, CounterV2Options, CounterV2DateData, CounterV2Type } from '@kit.ArkUI';
```

## onHoverDecrease

```TypeScript
onHoverDecrease?: OnCounterV2HoverCallback
```

Callback triggered when the mouse enters or leaves the decrease button of the **CounterV2** component.

Use scenario: Pass in this callback when you need to perform custom operations (such as changing button styles and displaying tooltips) when hovering over the decrease button.

**NOTE:** 

This attribute takes effect for the list, compact, and inline number **CounterV2**, but not for the inline date **CounterV2**.

Default value: **undefined**, indicating that this callback is not triggered.

When the value is **undefined**, the default value is used.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onHoverIncrease

```TypeScript
onHoverIncrease?: OnCounterV2HoverCallback
```

Callback triggered when the mouse enters or leaves the increase button of the **CounterV2** component.

Use scenario: Pass in this callback when you need to perform custom operations (such as changing button styles and displaying tooltips) when hovering over the increase button.

**NOTE:** 

This attribute takes effect for the list, compact, and inline number **CounterV2**, but not for the inline date **CounterV2**.

Default value: **undefined**, indicating that this callback is not triggered.

When the value is **undefined**, the default value is used.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## focusable

```TypeScript
focusable?: boolean
```

Whether **CounterV2** can obtain focus.

**NOTE:** 

This attribute takes effect for the list and compact **CounterV2**, but not for the inline number and inline date **CounterV2**.

Default value: **true**

**true**: **CounterV2** can obtain focus; **false**: **CounterV2** cannot obtain focus.

When the value is **undefined**, the default value is used.

**Type:** boolean

**Default:** true

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## step

```TypeScript
step?: number
```

Step of **CounterV2**.

**NOTE:** 

This attribute takes effect for the list, compact Type, and inline number **CounterV2**, but not for the inline date **CounterV2**.

Value range: an integer greater than or equal to 1.

Default value: **1**

If the value is out of the value range, the default value is used.

When the value is **undefined**, the default value is used.

**Type:** number

**Default:** 1

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
