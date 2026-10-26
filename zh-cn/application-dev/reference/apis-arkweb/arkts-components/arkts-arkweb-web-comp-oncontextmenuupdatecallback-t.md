# OnContextMenuUpdateCallback

```TypeScript
type OnContextMenuUpdateCallback = (menuItemId: WebContextMenuItemId, options?: WebContextMenuOptions) => void
```

上下文菜单项状态更新的回调类型。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-type OnContextMenuUpdateCallback = (menuItemId: WebContextMenuItemId, options?: WebContextMenuOptions) => void--><!--Device-unnamed-type OnContextMenuUpdateCallback = (menuItemId: WebContextMenuItemId, options?: WebContextMenuOptions) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| menuItemId | [WebContextMenuItemId](arkts-arkweb-web-comp-webcontextmenuitemid-e.md) | 是 | 上下文菜单项的ID。 |
| options | [WebContextMenuOptions](arkts-arkweb-web-comp-webcontextmenuoptions-i.md) | 否 | 上下文菜单项的选项。<br>默认值：见options的默认值。 |

**示例**

完整示例代码请参考[onContextMenuUpdate](./arkts-basic-components-web-events.md#oncontextmenuupdate)。
