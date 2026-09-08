# ContextMenu
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=86be1cec9251f60c95a43a01528b94e8f3ec0068 translatedAt=2026-08-28T01:40:49.405Z pushedAt=2026-09-01T07:23:05.215Z -->

The menu bound to a component through [bindContextMenu](./ts-universal-attributes-menu.md#bindcontextmenu12) on a page can be closed as needed.

>  **NOTE**
>
> The initial APIs of this module are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.

## ContextMenu.close<sup>(deprecated)</sup>

static close()

Closes the menu bound through [bindContextMenu](./ts-universal-attributes-menu.md#bindcontextmenu12) on a page. It is commonly used in interaction scenarios where the displayed menu needs to be actively closed, such as page navigation and drag start.

>  **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 18. You are advised to use [getContextMenuController](../arkts-apis-uicontext-uicontext.md#getcontextmenucontroller12) in [UIContext](../arkts-apis-uicontext-uicontext.md) to obtain a [ContextMenuController](../arkts-apis-uicontext-contextmenucontroller.md) instance, and then call the alternative method [close](../arkts-apis-uicontext-contextmenucontroller.md#close12) through this instance.
>
> The two methods provide the same functionality. The difference is that **ContextMenu.close()** is a static method, which may not explicitly specify the menu of which window to close in multi-window scenarios. In contrast, calling **close()** through the **ContextMenuController** instance obtained from **UIContext** can be associated with a specific **UIContext**, thereby explicitly specifying the UI context of the operation. You are advised to use the **UIContext** approach in API version 12 and later.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## Example

This example demonstrates how to use **ContextMenu.close** to close the menu bound through **bindContextMenu** when dragging starts.

>  **NOTE**
>
> You are advised to use the [getContextMenuController](../arkts-apis-uicontext-uicontext.md#getcontextmenucontroller12) API in [UIContext](../arkts-apis-uicontext-uicontext.md) to specify the UI execution context.

<!--deprecated_code_no_check-->

```ts
// xxx.ets
@Entry
@Component
struct Index {
  @Builder MenuBuilder() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button('ContextMenu1')
      Divider().strokeWidth(2).margin(5).color(Color.Black)
      Button('ContextMenu2')
      Divider().strokeWidth(2).margin(5).color(Color.Black)
      Button('ContextMenu3')
    }
    .width(200)
    .height(160)
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Column() {
        Text('Long press to show ContextMenu')
          .fontSize(20)
          .width('100%')
          .height(500)
          .backgroundColor(0xAFEEEE)
          .textAlign(TextAlign.Center)
      }
      .bindContextMenu(this.MenuBuilder, ResponseType.LongPress)
      .onDragStart(() => {
        // Close the menu when the component is dragged.
        ContextMenu.close() // You are advised to use this.getUIContext().getContextMenuController().close() to obtain the UI context.
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

![contextmenu_close.gif](figures/contextmenu_close.gif)