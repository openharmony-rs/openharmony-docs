# Class (ContextMenuController)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=d0611b26974cd3320fc5c6f33fb63f1a56638307 translatedAt=2026-10-29T09:01:04.473Z pushedAt=2026-10-29T12:18:18.607Z nl=1 -->

Provides the capability to control menu closing. You can use this API to proactively close a menu in specific scenarios, such as timed closing and closing by tapping outside the area.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 12.
>
> - The APIs of this module can be used only in the stage model.
>
> - In the following API examples, you must first use [getContextMenuController()](./arkts-apis-uicontext-uicontext.md#getcontextmenucontroller12) in **UIContext** to obtain a **ContextMenuController** instance, and then call the APIs using the obtained instance.

## close<sup>12+</sup>

close(): void

Closes the menu currently displayed through **bindContextMenu**. If no menu is displayed, calling this API has no effect.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

This example demonstrates how to trigger the **close()** API of **ContextMenuController** via a timer to close the menu automatically after a specified delay.

```ts
import { ContextMenuController } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  menu: ContextMenuController = this.getUIContext().getContextMenuController();

  @Builder MenuBuilder() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button('Test ContextMenu1 Close')
      Divider().strokeWidth(2).margin(5).color(Color.Black)
      Button('Test ContextMenu2')
      Divider().strokeWidth(2).margin(5).color(Color.Black)
      Button('Test ContextMenu3')
    }
    .width(200)
    .height(160)
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button('Start Timer').onClick(() => {
        // Call the close method to close the menu after a 10-second delay.
        setTimeout(() => {
          this.menu.close();
        }, 10000);
      })

      Column() {
        Text('Test ContextMenu close')
          .fontSize(20)
          .width('100%')
          .height(500)
          .backgroundColor(0xAFEEEE)
          .textAlign(TextAlign.Center)
      }
      // Bind the custom menu, triggered by a long press.
      .bindContextMenu(this.MenuBuilder, ResponseType.LongPress)
    }
    .width('100%')
    .height('100%')
  }
}
```

![contextMenuController_close](figures/contextMenuController_close.gif)

