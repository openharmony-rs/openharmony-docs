# ComposeTitleBarV2

ComposeTitleBarV2组件是一种标题栏，支持设置标题、头像（可选）和副标题（可选），可用于一级页面、二级及其以上界面配置返回键。该组件基于[状态管理（V2）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)实现，相较于 [状态管理（V1）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组 件层级。借助状态管理（V2），开发者可以通过该组件更灵活地控制普通标题栏的数据和状态，实现更高效的用户界面刷新。

> **说明：**
> 
> - 该组件仅可在Stage模型下使用。
> 
> - 如果ComposeTitleBarV2设置通用属性和
> 通用事件，编译工具链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到
> ComposeTitleBarV2本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议ComposeTitleBarV2设置通用属性和通用事件。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ComposeTitleBarV2, ComposeTitleBarV2MenuItem, ComposeTitleBarV2MenuItemParams } from '@kit.ArkUI';
```

## item

```TypeScript
item?: ComposeTitleBarV2MenuItem
```

用于左侧头像的单个菜单项。

**类型：** [ComposeTitleBarV2MenuItem](arkts-arkui-arkui-advanced-composetitlebarv2-composetitlebarv2menuitem-c.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## menuItems

```TypeScript
menuItems?: Array<ComposeTitleBarV2MenuItem>
```

右侧菜单项列表。

**类型：** Array&lt;[ComposeTitleBarV2MenuItem](arkts-arkui-arkui-advanced-composetitlebarv2-composetitlebarv2menuitem-c.md)&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## subtitle

```TypeScript
subtitle?: ResourceStr
```

副标题。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title: ResourceStr
```

标题。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
