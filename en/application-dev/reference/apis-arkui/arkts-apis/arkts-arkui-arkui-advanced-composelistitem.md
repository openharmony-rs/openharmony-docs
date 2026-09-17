# @ohos.arkui.advanced.ComposeListItem

## Child Components

Not supported

## Events

The universal events are not supported.

## Modules to Import

```TypeScript
import { ComposeListItem, ContentItem, IconType, OperateButton, OperateCheck, OperateIcon, OperateItem } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ContentItem](arkts-arkui-arkui-advanced-composelistitem-contentitem-c.md) | Defines elements for the left and center areas of the **ComposeListItem** component. |
| [OperateButton](arkts-arkui-arkui-advanced-composelistitem-operatebutton-c.md) | Defines the type of the button element on the right of the **ComposeListItem** component. |
| [OperateCheck](arkts-arkui-arkui-advanced-composelistitem-operatecheck-c.md) | Defines the type where the element on the right of the **ComposeListItem** component is **Switch**, **CheckBox**, or **Radio**. |
| [OperateIcon](arkts-arkui-arkui-advanced-composelistitem-operateicon-c.md) | Defines the type of the icon element on the right of the **ComposeListItem** component. |
| [OperateItem](arkts-arkui-arkui-advanced-composelistitem-operateitem-c.md) | Defines the type of the element on the right of the **ComposeListItem** component. |

### Structs

| Name | Description |
| --- | --- |
| [ComposeListItem](arkts-arkui-arkui-advanced-composelistitem-composelistitem-s.md) | The **ComposeListItem** component is a container that presents a series of items arranged in a column with the same width. You can use it to present data of the same type in a multiple and coherent row style, for example, images or text. |

### Enums

| Name | Description |
| --- | --- |
| [IconType](arkts-arkui-arkui-advanced-composelistitem-icontype-e.md) | Defines the icon type of the element on the left of the **ComposeListItem** component. |

## Examples

```TypeScript
### Example 1: Configuring a Simple List Item

This example demonstrates how to create a simple list item that includes a primary text, a secondary text, a description, and a button with accompanying text on the right.


```

```TypeScript
### Example 2: Implementing Screen Reader Announcement for Right-Side Elements

This example shows how to use the accessibilityText, accessibilityDescription, and accessibilityLevel properties to customize the screen reader announcements for different right-side elements such as icons, buttons, and radio buttons in a list item. This functionality is supported since API version 18.


```

```TypeScript
### Example 3: Setting the Symbol Icon

This example demonstrates how to use symbolStyle in ContentItem, OperateItem, and OperateIcon to set custom symbol icons. This functionality is supported since API version 18.
```
