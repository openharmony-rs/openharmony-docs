# @ohos.arkui.advanced.ChipGroup

## Modules to Import

```TypeScript
import { IconOptions, LabelOptions as ChipItemLabelOptions, ChipGroupItemOptions, ChipItemStyle, ChipGroupSpaceOptions, IconItemOptions, IconGroupSuffix, ChipGroup, SuffixImageIconOptions, SymbolItemOptions } from '@kit.ArkUI';
```

## Summary

### Structs

| Name | Description |
| --- | --- |
| [ChipGroup](arkts-arkui-arkui-advanced-chipgroup-chipgroup-s.md) |  |
| [IconGroupSuffix](arkts-arkui-arkui-advanced-chipgroup-icongroupsuffix-s.md) | The **ChipGroup** component provides a set of chips for organizing and categorizing files or resource content. |

### Interfaces

| Name | Description |
| --- | --- |
| [ChipGroupItemOptions](arkts-arkui-arkui-advanced-chipgroup-chipgroupitemoptions-i.md) | Defines the specific attributes of individual chips. |
| [ChipGroupPaddingOptions](arkts-arkui-arkui-advanced-chipgroup-chipgrouppaddingoptions-i.md) | Defines the top and bottom padding of a **ChipGroup** component, which is used to control the overall height of the ChipGroup. |
| [ChipGroupSpaceOptions](arkts-arkui-arkui-advanced-chipgroup-chipgroupspaceoptions-i.md) | Defines the left and right padding of the chip group, and the spacing between chips. |
| [ChipItemStyle](arkts-arkui-arkui-advanced-chipgroup-chipitemstyle-i.md) | Defines the common attributes shared by all chips. |
| [IconItemOptions](arkts-arkui-arkui-advanced-chipgroup-iconitemoptions-i.md) | Defines the configuration for the trailing builder, with constraints applied to background size and color settings. |
| [IconOptions](arkts-arkui-arkui-advanced-chipgroup-iconoptions-i.md) | Defines the common attributes of icons. |
| [LabelOptions](arkts-arkui-arkui-advanced-chipgroup-labeloptions-i.md) | Defines the label configuration options. |
| [SuffixImageIconOptions](arkts-arkui-arkui-advanced-chipgroup-suffiximageiconoptions-i.md) | Defines the configuration options for suffix icons. |
| [SymbolItemOptions](arkts-arkui-arkui-advanced-chipgroup-symbolitemoptions-i.md) | Suffix icon option type of ChipGroup. |

## Examples

```TypeScript
### Example 1: Implementing a Chip Group Without a Builder-defined Suffix

This example shows how to implement a chip group without a builder-defined suffix.


```

```TypeScript
### Example 2: Implementing a Chip Group with a Builder-defined Suffix

This example shows how to implement a chip group with a builder-defined suffix.


```

```TypeScript
### Example 3: Setting the Symbol Icon

This example implements IconGroupSuffix and ChipGroup with SymbolGlyph resources.


```

```TypeScript
### Example 4: Implementing the Screen Reader Feature for the Single-Selection Scenario

This example demonstrates how to implement the screen reader feature for a chip group with and without a suffix area in single-selection mode. The content to be read is the value of the accessibilityText attribute.
```

```TypeScript
### Example 5: Implementing the Screen Reader Feature for the Multi-selection Scenario

This example demonstrates how to implement the screen reader feature for a chip group with and without a suffix area in multi-selection mode. The content to be read is the value of the accessibilityText attribute.
```

```TypeScript
### Example 6: Setting System Material Style

This example implements the system material style by configuring backgroundSystemMaterial and iconBackgroundSystemMaterial, and enables the auto-invert feature so that the text color adapts to the background color.

Starting from API version 26.0.0, the backgroundSystemMaterial attribute is added to [ChipGroup](#chipgroup-1), and the iconBackgroundSystemMaterial attribute is added to [IconGroupSuffix](arkts-arkui-arkui-advanced-chipgroup-icongroupsuffix-s.md).


```

```TypeScript
### Example 7: Setting the System Material Style for the Selected State of a Component

This example configures selectedBackgroundSystemMaterial to implement the system material style for the selected state of the component, and enables auto invert color so that the text color adapts to the background color.

Since API version 26.0.0, [ChipGroup](#chipgroup-1) adds the selectedBackgroundSystemMaterial attribute.
```
