# ComposeTitleBar

ComposeTitleBar是一种普通标题栏组件，支持设置标题、头像（可选）和副标题（可选），可用于一级页面、二级及其以上界面显示返回键。可快速构建统一风格的标题栏，简化页面开发，支持灵活的菜单项配置和图标自定义，帮助开发者快速实现 导航和操作入口。 > **说明：** > > - 该组件仅可在Stage模型下使用。 > > - 如果ComposeTitleBar设置通用属性和通用事件， > 编译工具链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到ComposeTitleBar本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议 > ComposeTitleBar设置通用属性和通用事件。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-unnamed-export declare struct ComposeTitleBar--><!--Device-unnamed-export declare struct ComposeTitleBar-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## item

```TypeScript
item?: ComposeTitleBarMenuItem
```

用于左侧头像的单个菜单项目。不设置时标题栏左侧不显示头像。

**类型：** [ComposeTitleBarMenuItem](arkts-arkui-arkui-advanced-composetitlebar-composetitlebarmenuitem-c.md)

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ComposeTitleBar-item?: ComposeTitleBarMenuItem--><!--Device-ComposeTitleBar-item?: ComposeTitleBarMenuItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## menuItems

```TypeScript
menuItems?: Array<ComposeTitleBarMenuItem>
```

右侧菜单项目列表。不设置时标题栏右侧不显示菜单项目。

**类型：** Array&lt;[ComposeTitleBarMenuItem](arkts-arkui-arkui-advanced-composetitlebar-composetitlebarmenuitem-c.md)&gt;

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ComposeTitleBar-menuItems?: Array<ComposeTitleBarMenuItem>--><!--Device-ComposeTitleBar-menuItems?: Array<ComposeTitleBarMenuItem>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## subtitle

```TypeScript
subtitle?: ResourceStr
```

副标题。不设置时不显示副标题。

**类型：** [ResourceStr](../../apis-na/arkts-apis/arkts-na-resourcestr-t.md)

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ComposeTitleBar-subtitle?: ResourceStr--><!--Device-ComposeTitleBar-subtitle?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title: ResourceStr
```

标题栏的标题文本。

**类型：** [ResourceStr](../../apis-na/arkts-apis/arkts-na-resourcestr-t.md)

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ComposeTitleBar-title: ResourceStr--><!--Device-ComposeTitleBar-title: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

