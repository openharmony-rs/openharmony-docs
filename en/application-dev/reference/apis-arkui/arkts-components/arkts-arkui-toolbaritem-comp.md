# ToolBarItem(Defines toolbar attributes.)

You can use the **ToolBarItem** component to add toolbar items to the title bar using the [toolbar](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-toolbar.md#toolbar) universal attribute.

> **NOTE** > > This component is typically used with the > [toolbar](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-toolbar.md#toolbar) universal attribute.

## Child Components

This component can contain a single child component.

## ToolBarItem

```TypeScript
ToolBarItem(options?: ToolBarItemOptions)
```

Creates a toolbar item at the beginning of the corresponding column in the title bar by default. The column position is determined by the component's [toolbar](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-toolbar.md#toolbar) attribute configuration.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ToolBarItemOptions](arkts-arkui-toolbaritem-comp-toolbaritemoptions-i.md) | No | Optional parameters for **ToolBarItem**, including the **placement** parameter of the [ToolBarItemPlacement](arkts-arkui-toolbaritem-comp-toolbaritemplacement-e.md) type.<br>Default value: **placement: ToolBarItemPlacement.TOP_BAR_LEADING** |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ToolBarItemOptions](arkts-arkui-toolbaritem-comp-toolbaritemoptions-i.md) | Provides optional parameters for **ToolBarItem** configuration. |

### Enums

| Name | Description |
| --- | --- |
| [ToolBarItemPlacement](arkts-arkui-toolbaritem-comp-toolbaritemplacement-e.md) | Enumerates the placement options for toolbar items in the title bar. |
