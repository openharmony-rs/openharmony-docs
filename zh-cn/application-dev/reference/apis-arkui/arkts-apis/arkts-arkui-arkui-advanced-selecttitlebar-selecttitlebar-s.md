# SelectTitleBar

下拉菜单标题栏是一个包含下拉菜单的标题栏组件，支持页面间的快速切换，可配置返回按钮和右侧菜单项。该组件适用于需要在不同视图或页面间进行导航切换的场景，支持一级页面、二级及其以上界面。使用该组件可以方便用户快速访问和切换不同的内容视图， 提升页面导航的便捷性和用户体验。 > **说明：** > > - 该组件仅可在Stage模型下使用。 > > - 如果SelectTitleBar设置通用属性和通用事件，编 > 译工具链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到SelectTitleBar本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议 > SelectTitleBar设置通用属性和通用事件。

**起始版本：** 10

<!--Device-unnamed-export declare struct SelectTitleBar--><!--Device-unnamed-export declare struct SelectTitleBar-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SelectTitleBar, SelectTitleBarMenuItem } from '@kit.ArkUI';
```

## badgeValue

```TypeScript
badgeValue?: number
```

新事件标记，用于在标题栏右侧菜单图标上显示数量。 取值范围：[-2147483648,2147483647]，超出范围时会加上或减去4294967296，使得值仍在范围内，非整数时会舍去小数部分取整数部分，如5.5取5。 **说明：** 不传入时或小于等于0时，不显示事件标记。 最大消息数99，超过最大消息时仅显示99+。超大数值属于异常值，不显示事件标记。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectTitleBar-badgeValue?: number--><!--Device-SelectTitleBar-badgeValue?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hidesBackButton

```TypeScript
hidesBackButton?: boolean
```

是否隐藏左侧的返回箭头。 默认值：false。true：隐藏，false：显示。

**类型：** boolean

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectTitleBar-hidesBackButton?: boolean--><!--Device-SelectTitleBar-hidesBackButton?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## menuItems

```TypeScript
menuItems?: Array<SelectTitleBarMenuItem>
```

右侧菜单项列表，定义标题栏右侧的菜单项。需要在右侧添加菜单项时传入此参数，缺省时不显示右侧菜单区域。

**类型：** Array&lt;[SelectTitleBarMenuItem](arkts-arkui-arkui-advanced-selecttitlebar-selecttitlebarmenuitem-c.md)&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectTitleBar-menuItems?: Array<SelectTitleBarMenuItem>--><!--Device-SelectTitleBar-menuItems?: Array<SelectTitleBarMenuItem>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onSelected

```TypeScript
onSelected?: ((index: number) => void)
```

下拉菜单项选中触发的回调函数，传入选中项的索引。下拉菜单选中后需要处理特定业务逻辑时传入此参数，无特定业务逻辑时可缺省此参数。

**类型：** ((index: number) =&gt; void)

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-SelectTitleBar-onSelected?: ((index: number) => void)--><!--Device-SelectTitleBar-onSelected?: ((index: number) => void)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: Array<SelectOption>
```

下拉菜单中的项。

**类型：** Array&lt;[SelectOption](../../apis-na/arkts-apis/arkts-na-select-selectoption-i.md)&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectTitleBar-options: Array<SelectOption>--><!--Device-SelectTitleBar-options: Array<SelectOption>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
@Prop
  selected: number
```

当前选中项的索引。 第一项的索引为0，默认值为0。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectTitleBar-@Prop  selected: number--><!--Device-SelectTitleBar-@Prop  selected: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## subtitle

```TypeScript
subtitle?: ResourceStr
```

子标题。用于显示补充信息，需要显示子标题时传入，缺省时不显示子标题区域。

**类型：** [ResourceStr](../../apis-na/arkts-apis/arkts-na-resourcestr-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectTitleBar-subtitle?: ResourceStr--><!--Device-SelectTitleBar-subtitle?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

