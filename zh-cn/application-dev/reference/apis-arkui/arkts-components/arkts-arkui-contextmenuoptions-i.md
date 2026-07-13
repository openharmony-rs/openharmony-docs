# ContextMenuOptions

菜单项的信息。

**表1：同时设置offset与placement时菜单的偏移位置**

| placement设置的值 | 菜单的偏移量说明 |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Placement.TopLeft、Placement.Top、Placement.TopRight | offset的x为正数，菜单相对组件向右进行偏移，offset的y为正数，菜单相对组件向上进行偏移。 |
| Placement.BottomLeft、Placement.Bottom、Placement.BottomRight | offset的x为正数，菜单相对组件向左进行偏移，offset的y为正数，菜单相对组件向下进行偏移。 |
| Placement.RightTop、Placement.Right、Placement.RightBottom | offset的x为正数，菜单相对组件向右进行偏移，offset的y为正数，菜单相对组件向下进行偏移。 |

**表2：同时设置arrowOffset与placement时菜单箭头的默认位置**

| placement设置的值 | 菜单箭头的位置说明 |
| ------------------------------------------- | ------------------------------------------------------------ |
| Placement.Top、Placement.Bottom | 箭头显示在水平方向且默认居中，且距离菜单左侧边缘距离为箭头安全距离。 |
| Placement.Left、Placement.Right | 箭头显示在垂直方向且默认居中，且距离菜单上侧距离为箭头安全距离。 |
| Placement.TopLeft、Placement.BottomLeft | 箭头默认显示在水平方向，且距离菜单左侧边缘距离为箭头安全距离。 |
| Placement.TopRight、Placement.BottomRight | 箭头默认显示在水平方向，且距离菜单右侧距离为箭头安全距离。 |
| Placement.LeftTop、Placement.RightTop | 箭头默认显示在垂直方向，且距离菜单上侧距离为箭头安全距离。 |
| Placement.LeftBottom、Placement.RightBottom | 箭头默认显示在垂直方向，且距离菜单下侧距离为箭头安全距离。 |

**表3：enableArrow为true且placement未设置或者值为非法值的菜单默认位置**
| 接口 | 菜单默认位置 |
|------|-------------|
| [bindMenu](arkts-arkui-commonmethod-c.md#bindmenu-1) | Placement.BottomLeft |
| [bindMenu<sup>11+</sup>](arkts-arkui-commonmethod-c.md#bindmenu-2) | Placement.BottomLeft |
| [bindContextMenu<sup>8+</sup>](arkts-arkui-commonmethod-c.md#bindcontextmenu-1) | Placement.Top |
| [bindContextMenu<sup>12+</sup>](arkts-arkui-commonmethod-c.md#bindcontextmenu-2) | Placement.BottomLeft |
| [bindContextMenuWithResponse<sup>23+</sup>](arkts-arkui-commonmethod-c.md#bindcontextmenuwithresponse-1) | Placement.Top |

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToAppear

```TypeScript
aboutToAppear?: () => void
```

菜单显示动效前的事件回调。

**类型：** () => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToDisappear

```TypeScript
aboutToDisappear?: () => void
```

菜单退出动效前的事件回调。

**类型：** () => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## anchorPosition

```TypeScript
anchorPosition?: Position
```

通过设定水平与垂直偏移量，控制菜单相对于绑定组件左上角的弹出位置，与单独使用offset接口不同的是可以覆盖显示在绑定组件上。

默认值：{ x: undefined, y: undefined }，不支持设置百分比。

**说明：**

1. 当菜单处于预览状态时，设定的偏移量将无法生效。
2. 预设的placement对齐参数将不再生效。
3. 叠加offset参数的偏移量，最终确定菜单的精确弹出位置。
4. 当水平与垂直偏移量均设为负值时，菜单重置到Placement.BottomLeft进行显示。
5. 当水平或垂直偏移量存在undefined或null时，效果等同于不设置anchorPosition，此时预设的placement对齐参数可以生效。

**类型：** Position

**默认值：** { x: 0, y: 0 }

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arrowOffset

```TypeScript
arrowOffset?: Length
```

箭头在菜单处的偏移。偏移量必须合法且转换为具体数值时大于0才会生效，另外该值生效时不会导致箭头超出菜单四周的安全距离。

默认值：0

单位：vp

**说明：**

箭头距菜单四周的安全距离为菜单圆角大小与箭头宽度的一半之和。

根据配置的placement来计算是在水平还是垂直方向上偏移。

箭头在菜单水平方向时，偏移量为箭头至最左侧箭头安全距离处的距离。箭头在菜单垂直方向时，偏移量为箭头至最上侧箭头安全距离处的距离。

根据配置的placement的不同，箭头展示的默认位置不同：

在菜单不发生避让的情况下，箭头最终位置与placement设置值的关系参见表2：同时设置arrowOffset与placement时菜单箭头的默认位置。

bindContextMenu从API version 10开始支持该属性；bindMenu从API version 12开始支持该属性。

**类型：** Length

**默认值：** 0vp

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## availableLayoutArea

```TypeScript
availableLayoutArea?: AvailableLayoutArea
```

设置预览图宽高的可布局区域，预览图的百分比依据此设置计算，最终可能因安全区限制而被压缩或裁剪。

**说明：**

未设置或设置为undefined时，百分比依据窗口大小计算。若设置为AvailableLayoutArea.SAFE_AREA，预览图的可布局区域为窗口大小减去上下左右的安全边距。

**类型：** AvailableLayoutArea

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

菜单背板模糊材质。

默认值：BlurStyle.COMPONENT_ULTRA_THICK。

**类型：** BlurStyle

**默认值：** BlurStyle.COMPONENT_ULTRA_THICK

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

背景模糊效果。

**类型：** BackgroundBlurStyleOptions

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

菜单背板颜色。

默认值：Color.Transparent。

**类型：** ResourceColor

**默认值：** Color.Transparent

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

背景效果参数。

**类型：** BackgroundEffectOptions

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: Length | BorderRadiuses | LocalizedBorderRadiuses
```

设置菜单的边框圆角半径。

默认值：2in1设备上默认值8vp，其他设备上默认值20vp。

**说明：**

支持百分比。

当水平方向两个圆角半径之和的最大值超出菜单宽度或垂直方向两个圆角半径之和的最大值超出菜单高度时，采用菜单默认圆角半径值。

当设置Length类型且传参为异常值时，菜单圆角取默认值。

当设置BorderRadiuses或LocalizedBorderRadiuses类型且传参为异常值时，菜单默认没有圆角。

**类型：** Length | BorderRadiuses | LocalizedBorderRadiuses

**默认值：** 8vp for 2-in-1 devices and 20vp for other devices

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colorMode

```TypeScript
colorMode?: AnchoredColorMode
```

设置菜单深浅色模式，默认跟随绑定组件深浅色模式。

默认值：AnchoredColorMode.FOLLOW_TARGET

**说明：**

1. 仅当绑定组件使用了[WithTheme](../../../../reference/apis-arkui/arkui-ts/ts-container-with-theme.md#接口)标签时，该属性才会生效。
2. 该属性仅影响组件的默认样式，以及开发者设置的涉及深浅色资源的属性。
3. 设置为AnchoredColorMode.FOLLOW_SYSTEM时，模糊材质可以跟随，文字颜色以及涉及深浅色资源的属性仍保持跟随绑定组件的深浅色配置。

**类型：** AnchoredColorMode

**默认值：** AnchoredColorMode.FOLLOW_TARGET

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableArrow

```TypeScript
enableArrow?: boolean
```

是否显示箭头。如果菜单的大小和位置不足以放置箭头时，不会显示箭头。

默认值：false，不显示箭头。

**说明：**

enableArrow为true时，placement未设置或者值为非法值，默认在目标物上方显示（此时菜单默认位置与接口的关系参见表3：enableArrow为true且placement未设置或者值为非法值的菜单默认位置），否则
按照placement的位置优先显示。当前位置显示不下时，会自动调整位置，enableArrow为undefined时，不显示箭头。bindContextMenu从API version 10开始支持该属性；bindMenu从
API version 12开始支持该属性。

**类型：** boolean

**默认值：** false

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

菜单组件是否响应悬停态（半折叠状态）变化，即在悬停态下是否触发避让折痕区域。

默认值：false，2in1设备默认为true。未设置或者值为非法值时，生效默认值。

**说明：**

1. 如果菜单的弹出位置在悬停态折痕区域，菜单组件不会响应悬停态。
2. 2in1设备从API version 20开始生效。
3. 2in1设备仅在窗口瀑布模式下生效。

**类型：** boolean

**默认值：** true for 2-in-1 devices and false for other devices

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## gridStyle

```TypeScript
gridStyle?: MenuGridStyleOptions
```

设置菜单的栅格样式。仅固定样式菜单生效，例如在
[bindMenu](arkts-arkui-commonmethod-c.md#bindmenu-1)、
[bindContextMenu](arkts-arkui-commonmethod-c.md#bindcontextmenu-1)
、[bindContextMenuByResponseType](arkts-arkui-commonmethod-c.md#bindcontextmenubyresponsetype-1)、
[bindContextMenuByIsShow](arkts-arkui-commonmethod-c.md#bindcontextmenubyisshow-1)、
[bindContextMenuWithResponse](arkts-arkui-commonmethod-c.md#bindcontextmenuwithresponse-1)
中使用[MenuElement](arkts-arkui-menuelement-i.md)或在[MenuItem](arkts-arkui-menuitem.md)中使用MenuItemOptions。

**类型：** MenuGridStyleOptions

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hapticFeedbackMode

```TypeScript
hapticFeedbackMode?: HapticFeedbackMode
```

菜单弹出时振动效果。

默认值：HapticFeedbackMode.DISABLED，菜单弹出时不振动。

**说明：**

只有一级菜单可配置弹出时振动效果。

仅当用户启用系统触感反馈且在工程的[module.json5](../../../../quick-start/module-configuration-file.md)中配置requestPermissions字段开启
ohos.permission.VIBRATE振动权限时，方可生效。配置如下：

![menuEnableHapticFeedback](../../../../reference/apis-arkui/arkui-ts/figures/menuEnableHapticFeedback.png)

**类型：** HapticFeedbackMode

**默认值：** HapticFeedbackMode.DISABLED

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## keyboardAvoidMode

```TypeScript
keyboardAvoidMode?: MenuKeyboardAvoidMode
```

设置菜单是否避让软键盘。

**说明：**

未设置或设置为undefined时，按照MenuKeyboardAvoidMode.NONE处理。

**类型：** MenuKeyboardAvoidMode

**默认值：** MenuKeyboardAvoidMode.NONE

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## layoutRegionMargin

```TypeScript
layoutRegionMargin?: Margin
```

设置预览图与菜单布局时距上下左右边界的最小边距。

**说明：**

仅支持vp、px、fp、lpx、百分比。

当margin设置异常值或负值时，按默认值处理。

若preview为CustomBuilder，设置margin.left或margin.right时，预览图取消最大栅格的宽度限制。

注意应避免设置过大的margin导致布局区域变小，使得预览图和菜单无法正常布局。

当水平方向上margin之和超过布局最大宽度时，margin.left和margin.right均不生效，按默认值处理。

当垂直方向上margin之和超过布局最大高度时，margin.top和margin.bottom均不生效，按默认值处理。

边距默认值为左右边距16vp，上边距16vp, 下边距为4vp。

**类型：** Margin

**默认值：** 12vp for left and right, 16vp for top and bottom

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本13开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mask

```TypeScript
mask?: boolean | MenuMaskType
```

设置菜单是否有蒙层及蒙层样式。

true：有蒙层；false：没有蒙层；MenuMaskType：自定义蒙层的样式。

默认值：菜单有预览图时默认显示蒙层，否则不显示。

**说明：**

当设备配置不显示菜单蒙层时，该接口不生效。如当前在2in1设备上该接口不生效。

**类型：** boolean | MenuMaskType

**默认值：** true when preview is enabled, or is false

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxHeight

```TypeScript
maxHeight?: LengthMetrics
```

设置菜单显示的最大高度。

**说明：** 默认最大高度是可用高度的80%。

设置为0或负数以及设置为undefined时，按照默认最大高度处理。设置的菜单最大高度不能超过可用高度的100%。

预览图场景下不支持此能力，菜单按默认最大高度显示。

如果菜单所有选项的实际高度之和小于设定的高度，菜单的高度按实际高度显示。

**类型：** LengthMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## minKeyboardAvoidDistance

```TypeScript
minKeyboardAvoidDistance?: LengthMetrics
```

设置菜单避让软键盘的最小距离。

**说明：**

未设置、设置为负数或undefined时，按照8vp处理。仅在keyboardAvoidMode设置为避让软键盘时生效。

**类型：** LengthMetrics

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## modalMode

```TypeScript
modalMode?: ModalMode
```

设置菜单的模态模式。

**说明：**

默认值：ModalMode.AUTO

**类型：** ModalMode

**默认值：** ModalMode.AUTO

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Position
```

菜单弹出位置的偏移量，不会导致菜单显示超出屏幕范围。

默认值：{ x: 0, y: 0 }，不支持设置百分比。

**说明：**

菜单类型为相对父组件区域弹出时，自动根据菜单位置属性 (placement)将区域的宽或高计入偏移量中。

offset最终取值与placement设置值的关系参见表1：同时设置offset与placement时菜单的偏移位置。

未设置、异常值或者undefined时按默认{ x: 0, y: 0 }处理。若传入偏移量超出屏幕范围外，则会就近约束到屏幕范围内。

如果菜单调整了显示位置（与placement初始值主方向不一致），则偏移值 (offset) 失效。

**类型：** Position

**默认值：** - [since 10 - 10]
@default {x:0,y:0} - Percentage values are not supported. [since 11]

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onAppear

```TypeScript
onAppear?: () => void
```

菜单弹出后的事件回调。

**类型：** () => void

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidAppear

```TypeScript
onDidAppear?: Callback<void>
```

菜单弹出后的事件回调。

**说明：**

1. 正常时序依次为：aboutToAppear>>onWillAppear>>onAppear>>onDidAppear>>aboutToDisappear>>onWillDisappear>>onDisappear>>onDidDisappear。
2. 快速点击弹出，消失菜单时，存在onWillDisappear在onDidAppear前生效。
3. 当菜单入场动效未完成时关闭菜单，该回调不会触发。

4.onAppear和onDidAppear触发时机相同，onDidAppear在onAppear后生效。

**类型：** Callback<void>

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: Callback<void>
```

菜单消失后的事件回调。

**说明：**

1. 正常时序依次为：aboutToAppear>>onWillAppear>>onAppear>>onDidAppear>>aboutToDisappear>>onWillDisappear>>onDisappear>>onDidDisappear。
2. onDisappear和onDidDisappear触发时机相同，onDidDisappear在onDisappear后生效。

**类型：** Callback<void>

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDisappear

```TypeScript
onDisappear?: () => void
```

菜单消失后的事件回调。

**类型：** () => void

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: Callback<void>
```

菜单显示动效前的事件回调。

**说明：**

1. 正常时序依次为：aboutToAppear>>onWillAppear>>onAppear>>onDidAppear>>aboutToDisappear>>onWillDisappear>>onDisappear>>onDidDisappear。
2. aboutToAppear是初始化时触发调用，onWillAppear是在动画执行前触发调用，onWillAppear在aboutToAppear之后执行。

**类型：** Callback<void>

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: Callback<void>
```

菜单退出动效前的事件回调。

**说明：**

1. 正常时序依次为：aboutToAppear>>onWillAppear>>onAppear>>onDidAppear>>aboutToDisappear>>onWillDisappear>>onDisappear>>onDidDisappear。
2. 快速点击弹出，消失菜单时，存在onWillDisappear在onDidAppear前生效。
3. aboutToDisappear和onWillDisappear触发时机相同，onWillDisappear在aboutToDisappear后生效。

**类型：** Callback<void>

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## outlineColor

```TypeScript
outlineColor?: ResourceColor | EdgeColors
```

设置菜单边框外描边颜色。

**说明：**

默认值：'#19ffffff'

**类型：** ResourceColor | EdgeColors

**默认值：** '#19ffffff'

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## outlineWidth

```TypeScript
outlineWidth?: Dimension | EdgeOutlineWidths
```

设置菜单边框外描边宽度。

默认值：0vp

**说明：**

不支持百分比，若需要外描边效果，outlineWidth为必填项。

**类型：** Dimension | EdgeOutlineWidths

**默认值：** 0vp - Percentage values are not supported.

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placement

```TypeScript
placement?: Placement
```

菜单组件优先显示的位置，当前位置显示不下时，会自动调整位置。

**说明：**

1. 作为[bindMenu](arkts-arkui-commonmethod-c.md#bindmenu-2)入参时，默认值为Placement.BottomLeft。
2. 作为[bindContextMenu<sup>8+</sup>](arkts-arkui-commonmethod-c.md#bindcontextmenu-1)或[bindContextMenuWithResponse<sup>23+</sup>](arkts-arkui-commonmethod-c.md#bindcontextmenuwithresponse-1)入参时，默认效果为菜单跟随点击位置弹出。
3. 作为[bindContextMenu<sup>12+</sup>](arkts-arkui-commonmethod-c.md#bindcontextmenu-2)入参时，默认值为Placement.BottomLeft。
4. placement值设置为undefined、null或缺省时，按默认值处理。

**类型：** Placement

**默认值：** - [since 10 - 10]
@default Placement.BottomLeft [since 11]

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## preview

```TypeScript
preview?: MenuPreviewMode | CustomBuilder
```

长按悬浮菜单或使用
[bindContextMenu<sup>12+</sup>](arkts-arkui-commonmethod-c.md#bindcontextmenu-2)
显示菜单的预览内容样式，可以为目标组件的截图，也可以为用户自定义的内容。

默认值：MenuPreviewMode.NONE，无预览内容。

**说明：**

- 不支持responseType为ResponseType.RightClick时触发，如果responseType为ResponseType.RightClick，则不会显示预览内容。
- 当未设置preview参数或preview参数设置为MenuPreviewMode.NONE时，enableArrow参数生效。
- 当preview参数设置为MenuPreviewMode.IMAGE或CustomBuilder时，enableArrow为true时也不显示箭头。

**类型：** MenuPreviewMode | CustomBuilder

**默认值：** MenuPreviewMode.NONE

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## previewAnimationOptions

```TypeScript
previewAnimationOptions?: ContextMenuAnimationOptions
```

控制长按预览的显示效果。

默认值：{ scale: [0.95, 1.1], transition: undefined, hoverScale: undefined }。

**说明：**

倍率设置参数小于等于0时，不生效。

**类型：** ContextMenuAnimationOptions

**默认值：** { scale: [0.95, 1.1], transition: undefined, hoverScale: undefined } [since 12]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## previewBorderRadius

```TypeScript
previewBorderRadius?: BorderRadiusType
```

设置预览图边框圆角半径。

默认值：16vp

**说明：**

当水平方向上两个圆角半径之和的最大值超过预览图的宽度，或者垂直方向上两个圆角半径之和的最大值超过预览图的高度时，应采用预览图所能允许的最大圆角半径值。

圆角设置越大，圆角动画变化越快。

**类型：** BorderRadiusType

**默认值：** 16vp

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## previewScaleMode

```TypeScript
previewScaleMode?: PreviewScaleMode
```

预览图缩放方式。

默认值：PreviewScaleMode.AUTO

**说明：**

布局空间不足时，控制预览图的缩放方式。未设置或设置undefined按照PreviewScaleMode.AUTO处理。当设置成PreviewScaleMode.CONSTANT时，如果预览图过大，剩余的空间不足以放置菜单时，菜单
将重叠显示在预览图之下。

预览图的最大宽高不会超过预览图最大可布局区域（窗口大小减去上下左右的安全边距）。

**类型：** PreviewScaleMode

**默认值：** PreviewScaleMode.AUTO

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scrollBar

```TypeScript
scrollBar?: BarState
```

设置菜单滚动条状态。

默认值：BarState.Auto

未设置或者设置为undefined时，按照BarState.Auto处理。

**类型：** BarState

**默认值：** BarState.Auto

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## targetSpace

```TypeScript
targetSpace?: LengthMetrics
```

设置菜单与目标组件之间的间距。

**说明：**

- 同时使用targetSpace与offset时，两者会叠加生效。推荐使用targetSpace设置菜单与目标的间距，使用offset设置菜单弹出位置的偏移量。
- 二级菜单会避让targetSpace范围。
- 设置为负数或undefined时，菜单与目标组件之间的间距为默认8vp，且子菜单不避让targetSpace。
- targetSpace属性在存在默认placement时可直接生效，无默认placement的场景，需配合placement属性使用才可生效。
- anchorPosition的优先级要高于targetSpace。
- 不支持设置百分比。

**类型：** LengthMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition?: TransitionEffect
```

设置菜单显示和退出的过渡效果。

**说明：**

菜单退出动效过程中，进行横竖屏切换，菜单会避让。二级菜单不继承自定义动效。弹出过程可以点击二级菜单，退出动效执行过程不允许点击二级菜单。

详细描述见[TransitionEffect](arkts-arkui-transitioneffect-c.md)对象说明。

动效曲线使用弹簧曲线，在动效退出时，由于弹簧曲线的回弹震荡，菜单消失后有较长的拖尾，使得其他事件无法响应。

当设置transition自定义动效时，菜单的默认显示和退出动效不生效。

**类型：** TransitionEffect

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

