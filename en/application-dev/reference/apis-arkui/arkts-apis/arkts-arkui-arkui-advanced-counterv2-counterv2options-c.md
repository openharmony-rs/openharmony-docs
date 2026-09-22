# CounterV2Options

```TypeScript
declare class CounterV2Options
```

Defines the type and style of the **CounterV2** component.

When you select a **CounterV2** type, you must select the corresponding **CounterV2** style. If the style parameter does not match the type, the default style of that type is used.

| CounterV2 Type | CounterV2 Style |  
| ----------------------- | ------------------ |  
| [CounterV2Type.LIST](arkts-arkui-arkui-advanced-counterv2-counterv2type-e.md) | [CounterV2NumberStyleOptions](arkts-arkui-arkui-advanced-counterv2-counterv2numberstyleoptions-c.md) |
| [CounterV2Type.COMPACT](arkts-arkui-arkui-advanced-counterv2-counterv2type-e.md) | [CounterV2NumberStyleOptions](arkts-arkui-arkui-advanced-counterv2-counterv2numberstyleoptions-c.md) |
| [CounterV2Type.INLINE](arkts-arkui-arkui-advanced-counterv2-counterv2type-e.md) | [CounterV2InlineStyleOptions](arkts-arkui-arkui-advanced-counterv2-counterv2inlinestyleoptions-c.md) |
| [CounterV2Type.INLINE_DATE](arkts-arkui-arkui-advanced-counterv2-counterv2type-e.md) | [CounterV2DateStyleOptions](arkts-arkui-arkui-advanced-counterv2-counterv2datestyleoptions-c.md) |

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CounterV2Component, CounterV2Options, CounterV2DateData, CounterV2Type } from '@kit.ArkUI';
```

## dateOptions

```TypeScript
dateOptions?: CounterV2DateStyleOptions
```

Style of the inline date **CounterV2**.

Default value: **undefined**, which displays an inline date **CounterV2** with the date **0001/01/01**.

Pass this parameter when you need to customize attributes such as the initial date and date change callback of the inline date **CounterV2**. If the default date **0001/01/01** needs to be displayed and no custom configuration is required, you can skip this parameter to use the default style.

If the value is **undefined**, the default value is used.

**Type:** [CounterV2DateStyleOptions](arkts-arkui-arkui-advanced-counterv2-counterv2datestyleoptions-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: Direction
```

Layout direction.

Default value: **Direction.Auto**

If the value is **undefined**, the default value is used.

**Type:** [Direction](arkts-arkui-direction-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## inlineOptions

```TypeScript
inlineOptions?: CounterV2InlineStyleOptions
```

Style of the inline number **CounterV2**.

Default value: **undefined**, which displays an inline number **CounterV2** with the value **0**.

Pass this parameter when you need to customize attributes such as the initial value, range, step, text width, and change callback of the inline number **CounterV2**. If the initial value of the counter is **0** and no custom configuration is required, you can skip this parameter to use the default style.

If the value is **undefined**, the default value is used.

**Type:** [CounterV2InlineStyleOptions](arkts-arkui-arkui-advanced-counterv2-counterv2inlinestyleoptions-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## numberOptions

```TypeScript
numberOptions?: CounterV2NumberStyleOptions
```

Style of the list and compact **CounterV2**.

Default value: **undefined**, which displays a list or compact **CounterV2** with the value **0**.

Pass this parameter when you need to customize attributes such as the label, initial value, range, and step of the list or compact **CounterV2**. If the initial value of the counter is **0** and no custom configuration is required, you can skip this parameter to use the default style.

If the value is **undefined**, the default value is used.

**Type:** [CounterV2NumberStyleOptions](arkts-arkui-arkui-advanced-counterv2-counterv2numberstyleoptions-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: CounterV2Type
```

Type of the **CounterV2**. It must be used with the corresponding style parameter. For details about the mapping, see the table below.

**Type:** [CounterV2Type](arkts-arkui-arkui-advanced-counterv2-counterv2type-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
