# context_menu(openMenu)

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ContextMenu](arkts-arkui-contextmenu-c.md) | The [Menu](../../../ui/arkts-popup-and-menu-components-menu.md) component is a great option for creating menus, but it relies on a bound UI component to work. Since API version 18, however, the global API [openMenu](arkts-arkui-arkui-uicontext-promptaction-c.md#openmenu) offers a more flexible solution. This API can be used directly or encapsulated in scenarios where no bound UI components are available, making it ideal for use cases such as event callbacks or when integrating with external systems. |

## Examples

This example demonstrates how to use ContextMenu.close to close the menu bound through bindContextMenu when dragging starts.

> NOTE
> 
> You are advised to use the [getContextMenuController](../arkts-apis-uicontext-uicontext.md#getcontextmenucontroller) API in [UIContext](../arkts-apis-uicontext-uicontext.md) to specify the UI execution context.

```TypeScript
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
