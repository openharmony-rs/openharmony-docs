# @ohos.arkui.advanced.ChipGroupV2

## Modules to Import

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2Item, ChipGroupV2Items, ChipGroupV2ItemStyleConfig, ChipGroupV2ItemStyle, ChipGroupV2SpaceConfig, ChipGroupV2Space, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2PaddingConfig, ChipGroupV2Padding, ChipGroupV2IconGroupSuffix, ChipGroupV2 } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ChipGroupV2Item](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2item-c.md) | Defines chip group item. |
| [ChipGroupV2Items](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2items-c.md) | Defines items of chip group. |
| [ChipGroupV2ItemStyle](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemstyle-c.md) | Defines ChipGroupV2 item style. |
| [ChipGroupV2Padding](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2padding-c.md) | Defines chip group padding. |
| [ChipGroupV2Space](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2space-c.md) | Defines chip group space. |

### Structs

| Name | Description |
| --- | --- |
| [ChipGroupV2](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2-s.md) | Defines chipGroupV2. |
| [ChipGroupV2IconGroupSuffix](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2icongroupsuffix-s.md) | Defines IconGroupSuffix. |

### Interfaces

| Name | Description |
| --- | --- |
| [ChipGroupV2IconItemConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2iconitemconfig-i.md) | Defines ChipGroupV2 IconItemConfig. |
| [ChipGroupV2ItemConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemconfig-i.md) | Defines chip item config. |
| [ChipGroupV2ItemStyleConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemstyleconfig-i.md) | Defines ChipGroupV2 item style. |
| [ChipGroupV2PaddingConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2paddingconfig-i.md) | Defines ChipGroupV2 padding config. |
| [ChipGroupV2SpaceConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2spaceconfig-i.md) | Defines chip group space config. |
| [ChipGroupV2SymbolItemConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2symbolitemconfig-i.md) | Defines symbol item config. |

## Examples

```TypeScript
### Example 1: Implementing ChipGroupV2 Without the Rightmost Custom Component

This example implements the effect of [ChipGroupV2](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2-s.md) without the rightmost custom component by not setting the suffix parameter.


```

```TypeScript
### Example 2: Setting the Rightmost Custom Component of ChipGroupV2

This example implements the rightmost custom component effect of [ChipGroupV2](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2-s.md) by setting the suffix parameter.

Since API version 26.0.0, ChipGroupV2 supports the suffix attribute.


```

```TypeScript
### Example 3: Setting Symbol Icons

This example uses [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier) to set symbol icons for [ChipGroupV2IconGroupSuffix](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2icongroupsuffix-s.md) and [ChipGroupV2](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2-s.md).

Since API version 26.0.0, ChipGroupV2IconGroupSuffix and ChipGroupV2 are added.


```

```TypeScript
### Example 4: Listening for Internal Attribute Changes of Object-Type Attributes in ChipGroupV2

Classes such as [ChipGroupV2Items](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2items-c.md), [ChipGroupV2Item](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2item-c.md), and [ChipGroupV2ItemStyle](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemstyle-c.md) are decorated with @ObservedV2, and the ChipGroupV2 component receives attribute parameters through @Param. For primitive-type attributes decorated with @Trace (such as itemSpace of ChipGroupV2Space), @Param can already observe attribute changes and trigger UI refresh without additional processing. However, for internal attributes of object-type attributes in these classes (such as the size of prefixIcon in ChipGroupV2Item), the object types themselves are not decorated with @ObservedV2, so their internal attribute changes cannot be perceived by @Param, causing the UI not to refresh automatically when internal attributes are modified. Using the makeObserved API to wrap object-type attributes can supplement deep observation capability for the internal attributes of the object. For details about the makeObserved API, see [makeObserved API: Changing Unobservable Data to Observable Data](../../../ui/state-management/arkts-new-makeObserved.md).

The following example compares two scenarios: when the Change itemSpace button is tapped to modify the itemSpace attribute of chipGroupSpace (a primitive-type attribute decorated with @Trace, which already supports observation), the UI refreshes automatically; when the Change icon size button is tapped to modify the internal attribute for size of prefixIcon in ChipGroupV2Item (an internal attribute of an object-type attribute, which is observable when size is wrapped with UIUtils.makeObserved), the UI also refreshes automatically.
```
