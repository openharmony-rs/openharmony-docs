# Cursor Control
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=9430c77017ca73641537d932a3d7d8a4c99c078b translatedAt=2026-09-01T12:20:37.480Z -->

Mouse cursor control is used to set the display style of the mouse cursor. It supports setting multiple preset cursor styles and restoring the default arrow style. It is applicable to scenarios where the cursor style needs to be switched based on the component state or interaction area, resolving the issue that the default cursor style cannot match the interaction intent, and helping improve the user's interaction recognition and operation feedback experience.

>  **NOTE**
>
> - This feature is supported since API version 11. New APIs added in later versions are marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - Directly using cursorControl may lead to the issue of [ambiguous UI context](../../../ui/arkts-global-interface.md#ambiguous-ui-context). To avoid this, obtain the [UIContext](../arkts-apis-uicontext-uicontext.md) instance using getUIContext(), and then use [getCursorController](../arkts-apis-uicontext-uicontext.md#getcursorcontroller12) to obtain the cursorControl bound to the instance.


## cursorControl

### setCursor

setCursor(value: PointerStyle): void

A global API that can be used in component methods or event callbacks. Calling this API sets the current mouse cursor style, for example, displaying an I-beam cursor when hovering over a text editing area, displaying a move cursor on a draggable element, or displaying a pointing-hand cursor when hovering over a map marker.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ----- | ------ | ---- | ---- |
| value | [PointerStyle](#pointerstyle) | Yes | Mouse cursor style to set. |

### restoreDefault

restoreDefault(): void

A global API that can be used in component methods or event callbacks. Calling this API restores the mouse cursor to the default arrow style, for example, restoring the default cursor when the mouse leaves a hover area, when a component loses focus, or when an interaction ends.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## PointerStyle

type PointerStyle = import('../api/@ohos.multimodalInput.pointer').default.PointerStyle

Mouse cursor style.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

|Type|Description|
| -- | -- |
|import('../api/@ohos.multimodalInput.pointer').default.[PointerStyle](../../apis-input-kit/js-apis-pointer.md#pointerstyle) |Mouse cursor style.|

## Example

This example sets the mouse cursor style using setCursor.

```ts
// xxx.ets
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct CursorControlExample {
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
            cursorControl.setCursor(pointer.PointerStyle.EAST);
          } else {
            // You are advised to use this.getUIContext().getCursorController().restoreDefault().
            cursorControl.restoreDefault();
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
            cursorControl.setCursor(pointer.PointerStyle.WEST);
          } else {
            // You are advised to use this.getUIContext().getCursorController().restoreDefault().
            cursorControl.restoreDefault();
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
