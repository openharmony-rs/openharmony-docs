# @ohos.arkui.advanced.CounterV2

## Modules to Import

```TypeScript
import { CounterV2Component, CounterV2Options, CounterV2DateData, CounterV2Type } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [CounterV2CommonOptions](arkts-arkui-arkui-advanced-counterv2-counterv2commonoptions-c.md) | Defines the common options. |
| [CounterV2DateData](arkts-arkui-arkui-advanced-counterv2-counterv2datedata-c.md) | Defines the date data. |
| [CounterV2DateStyleOptions](arkts-arkui-arkui-advanced-counterv2-counterv2datestyleoptions-c.md) | Defines the date style options. |
| [CounterV2InlineStyleOptions](arkts-arkui-arkui-advanced-counterv2-counterv2inlinestyleoptions-c.md) | Defines the inline style options. |
| [CounterV2NumberStyleOptions](arkts-arkui-arkui-advanced-counterv2-counterv2numberstyleoptions-c.md) | Defines the number style options. |
| [CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md) | Defines the counter options. |

### Structs

| Name | Description |
| --- | --- |
| [CounterV2Component](arkts-arkui-arkui-advanced-counterv2-counterv2component-s.md) | Defines Counter Component. |

### Enums

| Name | Description |
| --- | --- |
| [CounterV2Type](arkts-arkui-arkui-advanced-counterv2-counterv2type-e.md) | Enum for the CounterV2 type. |

### Types

| Name | Description |
| --- | --- |
| [OnCounterV2HoverCallback](arkts-arkui-oncounterv2hovercallback-t.md) | The hover callback of CounterV2. |
| [OnDateCounterV2ChangeCallback](arkts-arkui-ondatecounterv2changecallback-t.md) | The change callback of the date style counter. |
| [OnInlineCounterV2Change](arkts-arkui-oninlinecounterv2change-t.md) | The change callback of the inline CounterV2. |

## Examples

```TypeScript
### Example 1: List CounterV2

This example implements a list CounterV2 by setting [CounterV2Type](arkts-arkui-arkui-advanced-counterv2-counterv2type-e.md).LIST and the numberOptions attribute of [CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md).

Since API version 26.0.0, [CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md) supports the numberOptions attributes.


```

```TypeScript
### Example 2: Compact CounterV2

This example implements a compact CounterV2 by setting [CounterV2Type](arkts-arkui-arkui-advanced-counterv2-counterv2type-e.md).COMPACT and the numberOptions attributes of [CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md).

Since API version 26.0.0, [CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md) supports the numberOptions attribute.


```

```TypeScript
### Example 3: Inline Number CounterV2

This example implements an inline number CounterV2 by setting [CounterV2Type](arkts-arkui-arkui-advanced-counterv2-counterv2type-e.md).INLINE and the inlineOptions attribute of [CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md).

Since API version 26.0.0, [CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md) supports the inlineOptions attribute.


```

```TypeScript
### Example 4: Inline Date CounterV2

This example implements an inline date CounterV2 by setting [CounterV2Type](arkts-arkui-arkui-advanced-counterv2-counterv2type-e.md).INLINE_DATE and the dateOptions attribute of [CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md).

Since API version 26.0.0, [CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md) supports the dateOptions attribute.


```

```TypeScript
### Example 5: Mirrored Layout Display

This example uses the direction attribute of [CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md) to implement mirrored layouts for the list, compact, inline number, and inline date CounterV2 components.

Since API version 26.0.0, [CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md) supports the direction attribute.
```
