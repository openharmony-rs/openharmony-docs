# ComposeTitleBarV2

ComposeTitleBarV2组件是一种标题栏，支持设置标题、头像（可选）和副标题（可选），可用于一级页面、二级及其以上界面配置返回键。 该组件基于\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_实现，相较于 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组 件层级。借助状态管理（V2），开发者可以通过该组件更灵活地控制普通标题栏的数据和状态，实现更高效的用户界面刷新。 > **说明：** > > - 该组件仅可在Stage模型下使用。 > > - 如果ComposeTitleBarV2设置[通用属性]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_和 > [通用事件]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_，编译工具链会额外生成节点\_\_Common\_\_，并将通用属性或通用事件挂载在\_\_Common\_\_上，而不是直接应用到 > ComposeTitleBarV2本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议ComposeTitleBarV2设置通用属性和通用事件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @ComponentV2

<!--Device-unnamed-export declare struct ComposeTitleBarV2--><!--Device-unnamed-export declare struct ComposeTitleBarV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## build

```TypeScript
build(): void
```

构建组件的方法。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComposeTitleBarV2-build(): void--><!--Device-ComposeTitleBarV2-build(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## item

```TypeScript
item?: ComposeTitleBarV2MenuItem
```

用于左侧头像的单个菜单项。

**类型：** ComposeTitleBarV2MenuItem

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComposeTitleBarV2-item?: ComposeTitleBarV2MenuItem--><!--Device-ComposeTitleBarV2-item?: ComposeTitleBarV2MenuItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## menuItems

```TypeScript
menuItems?: Array<ComposeTitleBarV2MenuItem>
```

右侧菜单项列表。

**类型：** Array&lt;ComposeTitleBarV2MenuItem&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComposeTitleBarV2-menuItems?: Array<ComposeTitleBarV2MenuItem>--><!--Device-ComposeTitleBarV2-menuItems?: Array<ComposeTitleBarV2MenuItem>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## subtitle

```TypeScript
subtitle?: ResourceStr
```

副标题。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComposeTitleBarV2-subtitle?: ResourceStr--><!--Device-ComposeTitleBarV2-subtitle?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title: ResourceStr
```

标题。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComposeTitleBarV2-title: ResourceStr--><!--Device-ComposeTitleBarV2-title: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

