# ExpandedMenuOptions

扩展下拉菜单。继承自[MenuItemOptions](../arkts-components/arkts-arkui-menuitemoptions-i.md)。

**继承/实现关系：** ExpandedMenuOptions extends [MenuItemOptions](../arkts-components/arkts-arkui-menuitemoptions-i.md)

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { EditorEventInfo, EditorMenuOptions, ExpandedMenuOptions, SelectionMenu, SelectionMenuOptions } from '@kit.ArkUI';
```

## action

```TypeScript
action?: () => void
```

点击菜单项的事件回调。同时配置builder和action时，点击图标会同时响应。不设置时点击无响应。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
