# FolderStack

**FolderStack** extends the [Stack](../../apis-default/arkts-apis/arkts-lib-es5-error-i.md#stack) container, adding the <!--RP1-->foldable phone hover<!--RP1End--> capability. Child components specified in the **upperItems** array of [FolderStackOptions](arkts-arkui-folderstackoptions-i.md) automatically avoid the screen crease area and reposition to the upper display. > **NOTE** > > The hover capability is designed for and only works on <!--RP2-->dual-fold devices<!--RP2End-->. > > When the component's parent is an > [if/else conditional render](../../../ui/rendering-control/arkts-rendering-control-ifelse.md) node, the foldable > hover feature is disabled. > > **Child Components** > > Multiple child components are supported.

## FolderStack

```TypeScript
FolderStack(options?: FolderStackOptions)
```

Defines the constructor of FolderStack component.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [FolderStackOptions](arkts-arkui-folderstackoptions-i.md) | No | Configuration of the **FolderStack** component. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [FolderStackOptions](arkts-arkui-folderstackoptions-i.md) |  |
| [HoverEventParam](arkts-arkui-hovereventparam-i.md) | The param of hover event. |
| [OnFoldStatusChangeInfo](arkts-arkui-onfoldstatuschangeinfo-i.md) | Called when the folding state changes. This API takes effect only in landscape mode. |

### Types

| Name | Description |
| --- | --- |
| [OnFoldStatusChangeCallback](arkts-arkui-onfoldstatuschangecallback-t.md) | Current fold state of the device. |
| [OnHoverStatusChangeCallback](arkts-arkui-onhoverstatuschangecallback-t.md) | Defines the current callback invoked when the hover state of the device changes. |
| [WindowStatusType](arkts-arkui-windowstatustype-t.md) | Enumerates the window modes. |

## Examples

```TypeScript
### Example 1: Implementing the Foldable Device Hover Capability with FolderStack

This example implements the foldable device hover capability.

Figure 1 Expanded state in landscape modeFigure 2 Half-fold state in landscape mode
```

```TypeScript
### Example 2: Dynamically Setting Attributes and Methods of the FolderStack Component Using attributeModifier

This example demonstrates how to dynamically set the onFolderStateChange and onHoverStatusChange methods of the FolderStack component using attributeModifier.
```
