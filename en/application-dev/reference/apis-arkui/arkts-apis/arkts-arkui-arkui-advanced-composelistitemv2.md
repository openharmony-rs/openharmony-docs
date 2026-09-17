# @ohos.arkui.advanced.ComposeListItemV2

## Modules to Import

```TypeScript
import { ComposeListItemV2, ContentItemV2, ContentItemV2Options, IconTypeV2, OperateButtonV2, OperateButtonV2Options, OperateCheckV2, OperateCheckV2Options, OperateIconV2, OperateIconV2Options, OperateItemV2, OperateItemV2Options } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ContentItemV2](arkts-arkui-arkui-advanced-composelistitemv2-contentitemv2-c.md) | Declare ContentItemV2 |
| [OperateButtonV2](arkts-arkui-arkui-advanced-composelistitemv2-operatebuttonv2-c.md) | Declare type OperateButtonV2 |
| [OperateCheckV2](arkts-arkui-arkui-advanced-composelistitemv2-operatecheckv2-c.md) | Declare type OperateCheckV2 |
| [OperateIconV2](arkts-arkui-arkui-advanced-composelistitemv2-operateiconv2-c.md) | Declare type OperateIconV2 |
| [OperateItemV2](arkts-arkui-arkui-advanced-composelistitemv2-operateitemv2-c.md) | Declare OperateItemV2 |

### Structs

| Name | Description |
| --- | --- |
| [ComposeListItemV2](arkts-arkui-arkui-advanced-composelistitemv2-composelistitemv2-s.md) | Declare ComposeListItemV2 |

### Interfaces

| Name | Description |
| --- | --- |
| [ContentItemV2Options](arkts-arkui-arkui-advanced-composelistitemv2-contentitemv2options-i.md) | Declare interface ContentItemV2Options |
| [OperateButtonV2Options](arkts-arkui-arkui-advanced-composelistitemv2-operatebuttonv2options-i.md) | Declare interface OperateButtonV2Options |
| [OperateCheckV2Options](arkts-arkui-arkui-advanced-composelistitemv2-operatecheckv2options-i.md) | Declare interface OperateCheckV2Options |
| [OperateIconV2Options](arkts-arkui-arkui-advanced-composelistitemv2-operateiconv2options-i.md) | Declare interface OperateIconV2Options |
| [OperateItemV2Options](arkts-arkui-arkui-advanced-composelistitemv2-operateitemv2options-i.md) | Declare interface OperateItemV2Options |

### Enums

| Name | Description |
| --- | --- |
| [IconTypeV2](arkts-arkui-arkui-advanced-composelistitemv2-icontypev2-e.md) | Declare enum IconTypeV2 |

### Types

| Name | Description |
| --- | --- |
| [OnActionCallback](arkts-arkui-onactioncallback-t.md) | Callback function when operate the icon. |
| [OnChangeCallback](arkts-arkui-onchangecallback-t.md) | Callback function when operate the checkbox/switch/radio. |

## Examples

```TypeScript
### Example 1: Setting a Simple List Item

Since API version 26.0.0, a simple list item with a primary title, secondary title, description, right button, and text can be implemented through the ComposeListItemV2 component API.
```

```TypeScript
### Example 2: Setting Custom Announcements for Different Right Elements of the List Item

Since API version 26.0.0, custom screen reader announcement text can be implemented for the right icons, buttons, and radio buttons of a list item by setting the accessibilityText, accessibilityDescription, and accessibilityLevel attributes.
```

```TypeScript
### Example 3: Setting Symbol Icons

Since API version 26.0.0, you can set symbol icon parameters through the attribute API symbolStyle of ContentItemV2, OperateItemV2, and OperateIconV2.
```
