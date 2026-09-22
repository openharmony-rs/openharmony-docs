# RowSplit

The **RowSplit** component lays out child components horizontally and inserts a vertical divider between every two child components. It is suitable for scenarios that require horizontal multi-area layout and support dynamic adjustment of child component widths, such as the left and right panes of a file manager and the two-column layout of a settings page. Through draggable dividers, users can flexibly adjust the width of each area.

## Child Components

Supported

The **RowSplit** component limits the width of its child components through dividers. During initialization, the divider positions are calculated based on the width of its child components. After initialization, dynamically modifying the width of a child component does not change the divider positions, which remain unchanged. You can drag a divider to change the width of the child components.

> **NOTE:** 
> 
> After initialization, dynamically modifying the [margin](arkts-arkui-common-comp-commonmethod-c.md#margin),
> [border](arkts-arkui-common-comp-commonmethod-c.md#border), or [padding](arkts-arkui-common-comp-commonmethod-c.md#padding) universal attributes may cause the
> width of a child component to be greater than the spacing between adjacent dividers. In this exceptional case,
> dragging a divider to change the width of the child components is not supported. This is because the divider
> positions are determined during initialization, and dynamically modifying attributes such as margin, border, and
> padding breaks the original layout calculation, preventing the dividers from correctly responding to drag
> operations. You are advised to set the size and margin attributes of the child components properly during
> initialization.

## RowSplit

```TypeScript
RowSplit()
```

Creates a horizontal split layout container with dividers between child components.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Summary

## Examples

This example shows the basic usage of RowSplit, which implements a horizontally laid-out layout with a draggable divider.

```TypeScript
// xxx.ets
@Entry
@Component
struct RowSplitExample {
  build() {
    Column() {
      Text('The second line can be dragged').fontSize(9).fontColor(0xCCCCCC).width('90%')
      // Create a RowSplit component to implement horizontal layout.
      RowSplit() {
        Text('1').width('10%').height(100).backgroundColor(0xF5DEB3).textAlign(TextAlign.Center)
        Text('2').width('10%').height(100).backgroundColor(0xD2B48C).textAlign(TextAlign.Center)
        Text('3').width('10%').height(100).backgroundColor(0xF5DEB3).textAlign(TextAlign.Center)
        Text('4').width('10%').height(100).backgroundColor(0xD2B48C).textAlign(TextAlign.Center)
        Text('5').width('10%').height(100).backgroundColor(0xF5DEB3).textAlign(TextAlign.Center)
      }
      .resizeable(true) // Draggable.
      .width('90%').height(100)
    }.width('100%').margin({ top: 5 })
  }
}
```
