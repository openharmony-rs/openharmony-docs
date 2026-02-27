# Cursor Control
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

You can control the display style of the mouse cursor.

>  **NOTE**
>
>  This feature is supported since API version 11. Updates will be marked with a superscript to indicate their earliest API version.


## cursorControl

### setCursor

setCursor(value: PointerStyle): void

Sets the current mouse cursor style. This API can be used globally in method statements.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ----- | ------ | ---- | ---- |
| value | [PointerStyle](#pointerstyle) | All consistent  | Cursor style.|

### restoreDefault

restoreDefault(): void

Restores the mouse cursor to the default arrow style. This API can be used globally in method statements.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## PointerStyle

type PointerStyle = pointer.PointerStyle

Defines the pointer style.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

|Type|Description|
| -- | -- |
|[pointer.PointerStyle](../../apis-input-kit/js-apis-pointer.md#pointerstyle) |Pointer style.|

> **NOTE**
> 
> Directly using **cursorControl** can lead to the issue of [ambiguous UI context](../../../ui/arkts-global-interface.md). To avoid this, obtain the [UIContext](../arkts-apis-uicontext-uicontext.md) object using the **getUIContext()** API and then call the [getCursorController](../arkts-apis-uicontext-uicontext.md#getcursorcontroller12) API through this object.

## Example

This example demonstrates how to change the mouse cursor style using **setCursor**.

```ts
// xxx.ets
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct CursorControlExample {
  @State text: string = '';
  controller: TextInputController = new TextInputController()

  build() {
    Column() {
      Row()
        .height(200)
        .width(200)
        .backgroundColor(Color.Green)
        .position({ x: 60, y: 70 })
        .onHover((flag) => {
          if (flag) {
            // You are advised to use this.getUIContext().getCursorController().setCursor().
            cursorControl.setCursor(pointer.PointerStyle.EAST)
          } else {
            // You are advised to use this.getUIContext().getCursorController().restoreDefault().
            cursorControl.restoreDefault()
          }
        })
      Row()
        .height(200)
        .width(200)
        .backgroundColor(Color.Blue)
        .position({ x: 130, y: 120 })
        .onHover((flag) => {
          if (flag) {
            // You are advised to use this.getUIContext().getCursorController().setCursor().
            cursorControl.setCursor(pointer.PointerStyle.WEST)
          } else {
            // You are advised to use this.getUIContext().getCursorController().restoreDefault().
            cursorControl.restoreDefault()
          }
        })
    }.width('100%')
  }
}
```
Diagrams:

When the mouse hovers over the blue area, it displays a west-pointing arrow cursor style.

![cursor_blue](figures/cursor_blue.jpg)

When the mouse hovers over the green area, it displays an east-pointing arrow cursor style.

![cursor_green](figures/cursor_green.jpg)
