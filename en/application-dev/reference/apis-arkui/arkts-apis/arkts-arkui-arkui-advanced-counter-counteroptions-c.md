# CounterOptions

```TypeScript
declare class CounterOptions
```

Defines the type and style of the **Counter** component.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CounterComponent, CounterOptions, CounterType, DateData } from '@kit.ArkUI';
```

## dateOptions

```TypeScript
dateOptions?: DateStyleOptions
```

Style of the inline date Counter. It must be used with the type set to **CounterType.INLINE_DATE**.

Default value: an inline date Counter displaying **0001/01/01**.

If this parameter is set to **undefined**, the default value is used.

**Type:** [DateStyleOptions](arkts-arkui-arkui-advanced-counter-datestyleoptions-c.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: Direction
```

Layout direction. This parameter is passed when adapting to right-to-left languages (such as Arabic) or implementing a mirrored layout. **Direction.Auto**: automatically follows the system language direction (default). **Direction.Ltr**: left-to-right layout, applicable to most languages. **Direction.Rtl**: right-to-left layout, applicable to RTL languages such as Arabic.

Default value: **Direction.Auto**.

If this parameter is set to **undefined**, the default value is used.

**Type:** [Direction](arkts-arkui-direction-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## inlineOptions

```TypeScript
inlineOptions?: InlineStyleOptions
```

Style of the inline number Counter. It must be used with the type set to **CounterType.INLINE**.

Default value: an inline number Counter with the counter displayed as **0**.

If this parameter is set to **undefined**, the default value is used.

**Type:** [InlineStyleOptions](arkts-arkui-arkui-advanced-counter-inlinestyleoptions-c.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## numberOptions

```TypeScript
numberOptions?: NumberStyleOptions
```

Style of the list-type or compact-type Counter. It must be used with the type set to **CounterType.LIST** or **CounterType.COMPACT**.

Default value: a list-type or compact-type Counter with the counter displayed as **0**.

If this parameter is set to **undefined**, the default value is used.

**Type:** [NumberStyleOptions](arkts-arkui-arkui-advanced-counter-numberstyleoptions-c.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: CounterType
```

Type of the current Counter. It must be used with the corresponding style parameters. For details about the mapping, see the Counter Type and Style Mapping table below.

When you select a **Counter** type, you must select the corresponding **Counter** style. If the style parameter does not match the type, the default style of that type is used.

| Counter Type | Counter Style |  
| ----------------------- | ------------------ |  
| [CounterType.LIST](arkts-arkui-arkui-advanced-counter-countertype-e.md) | [NumberStyleOptions](arkts-arkui-arkui-advanced-counter-numberstyleoptions-c.md) |
| [CounterType.COMPACT](arkts-arkui-arkui-advanced-counter-countertype-e.md) | [NumberStyleOptions](arkts-arkui-arkui-advanced-counter-numberstyleoptions-c.md) |
| [CounterType.INLINE](arkts-arkui-arkui-advanced-counter-countertype-e.md) | [InlineStyleOptions](arkts-arkui-arkui-advanced-counter-inlinestyleoptions-c.md) |
| [CounterType.INLINE_DATE](arkts-arkui-arkui-advanced-counter-countertype-e.md) | [DateStyleOptions](arkts-arkui-arkui-advanced-counter-datestyleoptions-c.md) |

**Type:** [CounterType](arkts-arkui-arkui-advanced-counter-countertype-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
