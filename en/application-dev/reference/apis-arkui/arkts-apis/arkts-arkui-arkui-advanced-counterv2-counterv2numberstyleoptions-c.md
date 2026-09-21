# CounterV2NumberStyleOptions

```TypeScript
declare class CounterV2NumberStyleOptions extends CounterV2InlineStyleOptions
```

Defines the attributes and events of the list and compact **CounterV2**.

**Inheritance/Implementation:** CounterV2NumberStyleOptions extends [CounterV2InlineStyleOptions](arkts-arkui-arkui-advanced-counterv2-counterv2inlinestyleoptions-c.md)

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CounterV2Component, CounterV2Options, CounterV2DateData, CounterV2Type } from '@kit.ArkUI';
```

## onBlurDecrease

```TypeScript
onBlurDecrease?: VoidCallback
```

Callback triggered when the decrease button of the **CounterV2** component loses focus.

Use scenario: Pass this callback when custom operations (such as validating input and saving state) need to be performed when the decrease button loses focus.

Default value: **undefined**, indicating that this callback is not triggered.

When the value is **undefined**, the default value is used.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onBlurIncrease

```TypeScript
onBlurIncrease?: VoidCallback
```

Callback triggered when the increase button of the **CounterV2** component loses focus.

Use scenario: Pass this callback when custom operations (such as validating input and saving state) need to be performed when the increase button loses focus.

Default value: **undefined**, indicating that this callback is not triggered.

When the value is **undefined**, the default value is used.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onFocusDecrease

```TypeScript
onFocusDecrease?: VoidCallback
```

Callback triggered when the decrease button of the **CounterV2** component gains focus.

Use scenario: Pass this callback when custom operations (such as changing styles and logging) need to be performed when the decrease button gains focus.

Default value: **undefined**, indicating that this callback is not triggered.

When the value is **undefined**, the default value is used.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onFocusIncrease

```TypeScript
onFocusIncrease?: VoidCallback
```

Callback triggered when the increase button of the **CounterV2** component gains focus.

Use scenario: Pass this callback when custom operations (such as changing styles and logging) need to be performed when the increase button gains focus.

Default value: **undefined**, indicating that this callback is not triggered.

When the value is **undefined**, the default value is used.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label?: ResourceStr
```

Description text of **CounterV2**.

Default value: ''

Note: Pass this parameter when description text (such as price and quantity) needs to be displayed next to **CounterV2**.

When the value is **undefined**, the default value is used.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
