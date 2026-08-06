# EditableTitleBarV2

编辑型标题栏，适用于多选界面或内容编辑界面，一般采取左叉右勾的形式。 该组件基于\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_实现，相较于 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组 件层级。借助状态管理（V2），开发者可以通过该组件更灵活地控制编辑型标题栏的数据和状态，实现更高效的用户界面刷新。 > **说明：** > > - 该组件仅可在Stage模型下使用。 > > - 如果EditableTitleBarV2设置[通用属性]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_和 > [通用事件]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_，编译工具链会额外生成节点\_\_Common\_\_，并将通用属性或通用事件挂载在\_\_Common\_\_上，而不是直接应用到 > EditableTitleBarV2本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议EditableTitleBarV2设置通用属性和通用事件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @ComponentV2

<!--Device-unnamed-export declare struct EditableTitleBarV2--><!--Device-unnamed-export declare struct EditableTitleBarV2-End-->

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

<!--Device-EditableTitleBarV2-build(): void--><!--Device-EditableTitleBarV2-build(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageItem

```TypeScript
imageItem?: EditableTitleBarItemV2
```

用于左侧头像的单个菜单项。需要在标题栏左侧显示头像时传入此参数，不传入时取默认值，不显示头像。 默认值：undefined。 **说明：** 左侧头像不支持配置无障碍属性。

**类型：** EditableTitleBarItemV2

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleBarV2-imageItem?: EditableTitleBarItemV2--><!--Device-EditableTitleBarV2-imageItem?: EditableTitleBarItemV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## leftIcon

```TypeScript
leftIcon?: EditableLeftIconV2
```

左侧图标配置。需要在标题栏左侧显示返回或取消图标时传入此参数，不传入时取默认值，不显示左侧图标。 默认值：undefined。

**类型：** EditableLeftIconV2

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleBarV2-leftIcon?: EditableLeftIconV2--><!--Device-EditableTitleBarV2-leftIcon?: EditableLeftIconV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## menuItems

```TypeScript
menuItems?: Array<EditableTitleBarMenuItemV2>
```

右侧菜单项列表。需要在标题栏右侧显示自定义操作按钮时传入此参数，不传入时取默认值，不显示右侧菜单项列表。 **说明：** 最多支持配置3个菜单项，如果同时配置保存按钮，则最多支持2个菜单项。 默认值：undefined。

**类型：** Array&lt;EditableTitleBarMenuItemV2&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleBarV2-menuItems?: Array<EditableTitleBarMenuItemV2>--><!--Device-EditableTitleBarV2-menuItems?: Array<EditableTitleBarMenuItemV2>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: EditableTitleBarStyleV2
```

标题栏样式和布局配置。需要自定义标题栏背景、安全区域、边距等样式时传入此参数。 默认值：new EditableTitleBarStyleV2()。

**类型：** EditableTitleBarStyleV2

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleBarV2-options: EditableTitleBarStyleV2--><!--Device-EditableTitleBarV2-options: EditableTitleBarStyleV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## saveButton

```TypeScript
saveButton?: EditableSaveButtonV2
```

保存按钮配置。需要对标题栏右侧保存按钮的控制显示或隐藏状态、设置默认焦点、或者设置保存回调函数时传入此参数，不传入时取默认值，显示保存按钮。 默认值：undefined，显示保存按钮。

**类型：** EditableSaveButtonV2

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleBarV2-saveButton?: EditableSaveButtonV2--><!--Device-EditableTitleBarV2-saveButton?: EditableSaveButtonV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title: ResourceStr | EditableTitleV2
```

标题内容，支持字符串或对象形式配置。传入字符串时仅显示主标题，传入EditableTitleV2对象时可同时配置主标题和副标题。 默认值：new EditableTitleV2()，表示标题内容为空。

**类型：** ResourceStr \| EditableTitleV2

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Param、@Require

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleBarV2-title: ResourceStr | EditableTitleV2--><!--Device-EditableTitleBarV2-title: ResourceStr | EditableTitleV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

