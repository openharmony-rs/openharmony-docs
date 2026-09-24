# NumberStyleOptions

```TypeScript
declare class NumberStyleOptions extends InlineStyleOptions
```

Defines the list and compact counter attributes and events.

Inherits from [InlineStyleOptions](arkts-arkui-arkui-advanced-counter-inlinestyleoptions-c.md) and includes all attributes of that API. This section only describes the newly added attributes. For inherited attributes, see the parent API.

**Inheritance/Implementation:** NumberStyleOptions extends [InlineStyleOptions](arkts-arkui-arkui-advanced-counter-inlinestyleoptions-c.md)

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CounterComponent, CounterOptions, CounterType, DateData } from '@kit.ArkUI';
```

## onBlurDecrease

```TypeScript
onBlurDecrease?: () => void
```

Callback invoked when the decrease button of the current Counter component loses focus.

Usage scenario: pass this callback when you need to perform custom operations (such as validating input, saving state, etc.) when the decrease button loses focus.

Default value: the callback is not triggered when the decrease button loses focus.

If the value is **undefined**, the default value is used.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onBlurIncrease

```TypeScript
onBlurIncrease?: () => void
```

Callback invoked when the increase button of the current Counter component loses focus.

Usage scenario: pass this callback when you need to perform custom operations (such as validating input, saving state, etc.) when the increase button loses focus.

Default value: the callback is not triggered when the increase button loses focus.

If the value is **undefined**, the default value is used.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onFocusDecrease

```TypeScript
onFocusDecrease?: () => void
```

Callback invoked when the decrease button of the current Counter component gains focus.

Usage scenario: pass this callback when you need to perform custom operations (such as changing styles, logging, etc.) when the decrease button gains focus.

Default value: the callback is not triggered when the decrease button gains focus.

If the value is **undefined**, the default value is used.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onFocusIncrease

```TypeScript
onFocusIncrease?: () => void
```

Callback invoked when the increase button of the current Counter component gains focus.

Usage scenario: pass this callback when you need to perform custom operations (such as changing styles, logging, etc.) when the increase button gains focus.

Default value: the callback is not triggered when the increase button gains focus.

If the value is **undefined**, the default value is used.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label?: ResourceStr
```

Label text of the Counter.

Usage scenario: pass this parameter when you need to display descriptive text (such as 'Price', 'Quantity', etc.) next to the Counter.

Default value: ''.

If the value is **undefined**, the default value is used.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
