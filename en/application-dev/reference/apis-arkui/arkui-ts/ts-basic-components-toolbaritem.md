# ToolBarItem
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=39ca26def5c22dc659f3dc0b76ef62a29421e77a translatedAt=2026-09-03T13:00:55.801Z -->

You can use the **ToolBarItem** component to add toolbar items to the title bar using the [toolbar](ts-universal-attributes-toolbar.md#toolbar) universal attribute.

>  **NOTE**
>
>  - This component is supported since API version 20. Newly added content in later versions will be marked with a superscript to indicate the version in which it was introduced.
>
>  - The APIs of this module can be used only in the stage model.
>
>  - This component is generally used together with the [toolbar](ts-universal-attributes-toolbar.md#toolbar) universal attribute.


## Child Components

This component can contain a single child component.

## APIs

### ToolBarItem

ToolBarItem(options?: ToolBarItemOptions)

Creates a toolbar item at the beginning of the corresponding column in the title bar by default. The column position is determined by the component's [toolbar](ts-universal-attributes-toolbar.md#toolbar) attribute configuration.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                             | Mandatory| Description                                                        |
| ------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| options | [ToolBarItemOptions](#toolbaritemoptions) | No | Optional parameters for ToolBarItem. This object contains the placement parameter of the [ToolBarItemPlacement](#toolbaritemplacement) enum type.<br>Default value: placement: ToolBarItemPlacement.TOP_BAR_LEADING |

## Attributes

The [universal attributes](ts-component-general-attributes.md) are not supported.

## ToolBarItemOptions

Provides optional parameters for **ToolBarItem** configuration.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type                                                 | Read-Only| Optional| Description                                                        |
| --------- | -------------------------------------------- | --------- | ---- | ------------------------------------------------------------ |
| placement | [ToolBarItemPlacement](#toolbaritemplacement) | No | Yes | Placement of the toolbar item.<br>Default value: ToolBarItemPlacement.TOP_BAR_LEADING<br>When set to ToolBarItemPlacement.TOP_BAR_LEADING, the toolbar item is placed at the beginning of the corresponding top bar.<br>When set to ToolBarItemPlacement.TOP_BAR_TRAILING, the toolbar item is placed at the end of the corresponding top bar.<br> |

## ToolBarItemPlacement

Enumerates the placement options for toolbar items in the title bar.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name            | Value  | Description                                      |
| ---------------- | ---- | ------------------------------------------ |
| TOP_BAR_LEADING  | 0    | Places the item at the start of the top bar.|
| TOP_BAR_TRAILING | 1    | Places the item at the end of the top bar.|

## Example

See [toolbar](ts-universal-attributes-toolbar.md#example).