# ColumnSplit

The **ColumnSplit** component lays out child components vertically and inserts a horizontal divider between every two child components. It is suitable for scenarios that require a vertical multi-area layout with dynamic area resizing, such as dashboard UIs and adjustable top-bottom split layouts. Through draggable dividers, users can flexibly adjust the height of each area, enhancing UI interactivity and user experience.

## Child Components

Supported

**ColumnSplit** limits the height of child components through dividers. During initialization, the divider positions are calculated based on the heights of the child components. After initialization, dynamically modifying the height of child components does not take effect, and the divider positions remain unchanged. After **resizeable** is set to **true**, the height of child components can be changed by dragging adjacent dividers.

After initialization, when dynamic modification of the [margin](arkts-arkui-common-comp-commonmethod-c.md#margin), [border](arkts-arkui-common-comp-commonmethod-c.md#border), or [padding](arkts-arkui-common-comp-commonmethod-c.md#padding) universal attributes causes a child component size to exceed the spacing between adjacent dividers, dragging the divider to change the child component height is not supported.

## ColumnSplit

```TypeScript
ColumnSplit()
```

Creates a vertical split layout container with dividers between child components.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ColumnSplitDividerStyle](arkts-arkui-columnsplit-comp-columnsplitdividerstyle-i.md) | Sets the distance between the child component and the upper and lower dividers. |

## Examples

### Example 1: Setting the Resizable ColumnSplit Component

This example shows how to set the resizable ColumnSplit component and its effect.



```TypeScript
// xxx.ets
@Entry
@Component
struct ColumnSplitExample {
  build() {
    Column() {
      Text('The dividing line can be dragged').fontSize(9).fontColor(0xCCCCCC).width('90%')
      ColumnSplit() {
        Text('1').width('100%').height(50).backgroundColor(0xF5DEB3).textAlign(TextAlign.Center)
        Text('2').width('100%').height(50).backgroundColor(0xD2B48C).textAlign(TextAlign.Center)
        Text('3').width('100%').height(50).backgroundColor(0xF5DEB3).textAlign(TextAlign.Center)
        Text('4').width('100%').height(50).backgroundColor(0xD2B48C).textAlign(TextAlign.Center)
        Text('5').width('100%').height(50).backgroundColor(0xF5DEB3).textAlign(TextAlign.Center)
      }
      .borderWidth(1)
      .resizeable(true) // Set the divider draggable.
      .width('90%').height('60%')
    }.width('100%')
  }
}
```

### Example 2: Setting the ColumnSplit Component with Spacing

This example shows how to set the ColumnSplit component with spacing and its effect.

```TypeScript
// xxx.ets
@Entry
@Component
struct ColumnSplitDividerExample {
  build() {
    Column() {
      Text('The dividing line can be dragged').fontSize(9).fontColor(0xCCCCCC).width('90%')
      ColumnSplit() {
        Text('1').width('100%').height(50).backgroundColor(0xF5DEB3).textAlign(TextAlign.Center)
        Text('2').width('100%').height(50).backgroundColor(0xD2B48C).textAlign(TextAlign.Center)
        Text('3').width('100%').height(50).backgroundColor(0xF5DEB3).textAlign(TextAlign.Center)
        Text('4').width('100%').height(50).backgroundColor(0xD2B48C).textAlign(TextAlign.Center)
        Text('5').width('100%').height(50).backgroundColor(0xF5DEB3).textAlign(TextAlign.Center)
      }
      .borderWidth(1)
      .divider({ startMargin: 5, endMargin: 5 }) // Set the distance between the divider and child components.
      .width('90%')
      .height('60%')
    }.width('100%')
  }
}
```
