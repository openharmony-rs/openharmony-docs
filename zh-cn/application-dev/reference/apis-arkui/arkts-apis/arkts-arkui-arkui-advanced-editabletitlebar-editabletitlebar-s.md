# EditableTitleBar

编辑型标题栏组件，提供标准的编辑界面标题栏实现，支持自定义左侧按钮类型（返回/取消）、头像显示、右侧菜单项、背景模糊样式等功能。适用于需要进行内容编辑、多选操作的场景，如相册多选编辑、文本编辑器、表单编辑等界面。该组件封装了编辑场景常 用的UI交互模式（左叉右勾），开发者无需自行实现标题栏布局和交互逻辑，可快速构建符合设计规范的编辑界面，提升开发效率并保证UI一致性。同时支持无障碍属性配置，满足可访问性要求。

> **说明：**
> 
> - 该组件仅可在Stage模型下使用。
> 
> - 如果EditableTitleBar设置通用属性和通用事件
> ，编译工具链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到EditableTitleBar本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议
> EditableTitleBar设置通用属性和通用事件。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { EditableLeftIconType, EditableTitleBar, EditableTitleBarMenuItem, EditableTitleBarItem, EditableTitleBarOptions } from '@kit.ArkUI';
```

## onCancel

```TypeScript
onCancel?: () => void
```

当左侧按钮类型为 Cancel，触发取消时的事件。需要自定义返回/取消操作逻辑时传入此参数，缺省时点击左侧按钮无响应。默认值：() =&gt; void。从API version 12开始，当左侧按钮类型为 Back，触发返回时的事件。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onSave

```TypeScript
onSave?: () => void
```

点击保存时的事件。需要自定义保存操作逻辑时传入此参数，缺省时点击按钮无响应。默认值：() =&gt; void。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentMargin

```TypeScript
contentMargin?: LocalizedMargin
```

标题栏外边距，不支持设置负数。默认值：{start: LengthMetrics.resource(`\$r('sys.float.margin_left')`), end: LengthMetrics.resource(`\$r('sys.float.margin_right')`)}。

**类型：** [LocalizedMargin](arkts-arkui-localizedmargin-t.md)

**默认值：** {start: LengthMetrics.resource($r('sys.float.margin_left')), 
 end: LengthMetrics.resource($r('sys.float.margin_right'))}

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageItem

```TypeScript
imageItem?: EditableTitleBarItem
```

用于左侧头像的单个菜单项目。需要在标题栏左侧显示头像时传入此参数，不传入时取默认值，不显示头像。默认值：undefined。  
**说明：** 左侧头像不支持配置无障碍属性。

**类型：** [EditableTitleBarItem](arkts-arkui-editabletitlebaritem-t.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isSaveIconRequired

```TypeScript
isSaveIconRequired: boolean
```

是否需要右侧的保存按钮。true表示需要右侧的保存按钮，false表示不需要右侧的保存按钮。默认值：true  
**说明：** 未使用@Require装饰，构造时不强制校验参数。当isSaveIconRequired为false时，不显示保存按钮，onSave回调不会触发。

**类型：** boolean

**默认值：** true

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## leftIconDefaultFocus

```TypeScript
leftIconDefaultFocus?: boolean
```

左侧图标是否为默认焦点。true表示是默认焦点，false表示不是默认焦点。默认值：false  
**说明：** 若同时有多个可操作区域设置为默认焦点，则设置过默认焦点的可操作区域中显示顺序的第一个为默认焦点。

**类型：** boolean

**默认值：** { false }

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## leftIconStyle

```TypeScript
leftIconStyle: EditableLeftIconType
```

左侧按钮类型。默认值：EditableLeftIconType.Back，表示返回。

**类型：** [EditableLeftIconType](arkts-arkui-arkui-advanced-editabletitlebar-editablelefticontype-e.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## menuItems

```TypeScript
menuItems?: Array<EditableTitleBarMenuItem>
```

右侧菜单项目列表。需要在标题栏右侧显示自定义操作按钮时传入此参数，不传入时取默认值，不显示右侧菜单项目列表。默认值：undefined。

**类型：** Array&lt;[EditableTitleBarMenuItem](arkts-arkui-arkui-advanced-editabletitlebar-editabletitlebarmenuitem-c.md)&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: EditableTitleBarOptions
```

标题样式。默认值：{safeAreaTypes: [SafeAreaType.SYSTEM],safeAreaEdges: [SafeAreaEdge.TOP],backgroundColor: '#00000000'}。  
**说明：** 未使用@Require装饰，构造时不强制校验参数。

**类型：** [EditableTitleBarOptions](arkts-arkui-arkui-advanced-editabletitlebar-editabletitlebaroptions-i.md)

**默认值：** {expandSafeAreaTypes: SafeAreaType.SYSTEM, expandSafeAreaEdges: SafeAreaEdge.TOP}

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## saveIconDefaultFocus

```TypeScript
saveIconDefaultFocus?: boolean
```

保存图标是否为默认焦点。true表示是默认焦点，false表示不是默认焦点。默认值：false  
**说明：** 需要右侧保存按钮（isSaveIconRequired为true）时此属性生效。若同时有多个可操作区域设置为默认焦点，则设置过默认焦点的可操作区域中显示顺序的第一个为默认焦点。

**类型：** boolean

**默认值：** { false }

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## subtitle

```TypeScript
subtitle?: ResourceStr
```

副标题。需要在标题下方显示补充说明信息时传入此参数，不传入时不显示。默认值：''，表示副标题内容为空。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title: ResourceStr
```

标题。默认值：''，表示标题内容为空。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
