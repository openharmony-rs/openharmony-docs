# context_menu

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ContextMenu](arkts-arkui-contextmenu-c.md) | 在页面范围内关闭通过[bindContextMenu](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#bindcontextmenu-1)属性绑定的菜单。 |

## 示例

该示例演示ContextMenu.close的使用方法，在拖拽开始时关闭通过bindContextMenu绑定的菜单。

> 说明：
> 
> 推荐通过使用[UIContext](../arkts-apis-uicontext-uicontext.md)中的[getContextMenuController](../arkts-apis-uicontext-uicontext.md#getcontextmenucontroller)来明确UI的执行上下文。

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
        // 拖拽时关闭菜单
        ContextMenu.close() // 建议使用 this.getUIContext().getContextMenuController().close()
      })
    }
    .width('100%')
    .height('100%')
  }
}
```
