# NavigationTitleOptions

标题栏选项。

**起始版本：** 11

<!--Device-unnamed-declare interface NavigationTitleOptions--><!--Device-unnamed-declare interface NavigationTitleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

标题栏背景模糊样式，不设置时关闭背景模糊效果。

**类型：** BlurStyle

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationTitleOptions-backgroundBlurStyle?: BlurStyle--><!--Device-NavigationTitleOptions-backgroundBlurStyle?: BlurStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

标题栏背景模糊选项。

**说明：**

只在设置了backgroundBlurStyle时生效。

不建议与backgroundEffect同时使用。

**类型：** BackgroundBlurStyleOptions

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationTitleOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-NavigationTitleOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

标题栏背景颜色，不设置时为系统默认颜色。

**类型：** ResourceColor

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationTitleOptions-backgroundColor?: ResourceColor--><!--Device-NavigationTitleOptions-backgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

设置标题栏背景属性包括：模糊半径，亮度，饱和度，颜色等。

**说明：**

不建议与backgroundBlurStyleOptions同时使用。

**类型：** BackgroundEffectOptions

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationTitleOptions-backgroundEffect?: BackgroundEffectOptions--><!--Device-NavigationTitleOptions-backgroundEffect?: BackgroundEffectOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## barStyle

```TypeScript
barStyle?: BarStyle
```

设置标题栏布局方式。

默认值：BarStyle.STANDARD

**类型：** BarStyle

**默认值：** BarStyle.STANDARD

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationTitleOptions-barStyle?: BarStyle--><!--Device-NavigationTitleOptions-barStyle?: BarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

是否响应悬停态。

使用规则：

1. 需满足Navigation为全屏大小；2. 标题栏显示模式为[Free](arkts-arkui-navigationtitlemode-e.md)时或者标题栏布局方式为[STANDARD](arkts-arkui-barstyle-e.md)时，此接口设置无效。

true：响应悬停态；false：不响应悬停态。

默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationTitleOptions-enableHoverMode?: boolean--><!--Device-NavigationTitleOptions-enableHoverMode?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mainTitleModifier

```TypeScript
mainTitleModifier?: TextModifier
```

主标题属性修改器。

1. 通过Modifier设置的属性会覆盖系统默认的属性（如果Modifier设置了fontSize，maxFontSize，minFontSize任一属性，则系统设置的大小相关属性不生效，以开发者的设置为准）；2. 不设该属性或者设置了异常值，则恢复系统默认设置；3. [Free](arkts-arkui-navigationtitlemode-e.md)模式下设置字体大小时，原有滑动改变标题大小的效果失效。

**类型：** TextModifier

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationTitleOptions-mainTitleModifier?: TextModifier--><!--Device-NavigationTitleOptions-mainTitleModifier?: TextModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## paddingEnd

```TypeScript
paddingEnd?: LengthMetrics
```

标题栏结束端内间距。

仅支持以下任一场景：

1. 使用非自定义菜单，即[菜单value](NavigationAttribute#menus(value: Array<NavigationMenuItem> | CustomBuilder))为Array<NavigationMenuItem>；2. 没有右上角菜单，且使用非自定义标题，即[标题value](NavigationAttribute#title)类型为ResourceStr或NavigationCommonTitle。

默认值：

LengthMetrics.resource(`$r('sys.float.margin_right')`)

**类型：** LengthMetrics

**默认值：** LengthMetrics.resource($r('sys.float.margin_right'))

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationTitleOptions-paddingEnd?: LengthMetrics--><!--Device-NavigationTitleOptions-paddingEnd?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## paddingStart

```TypeScript
paddingStart?: LengthMetrics
```

标题栏起始端内间距。

仅支持以下任一场景：

1. 显示返回图标，即[hideBackButton](NavigationAttribute#hideBackButton)为false；2. 使用非自定义标题，即[标题value](NavigationAttribute#title)类型为ResourceStr或NavigationCommonTitle。

默认值：

LengthMetrics.resource(`$r('sys.float.margin_left')`)。

**类型：** LengthMetrics

**默认值：** LengthMetrics.resource($r('sys.float.margin_left'))

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationTitleOptions-paddingStart?: LengthMetrics--><!--Device-NavigationTitleOptions-paddingStart?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scrollEffectOptions

```TypeScript
scrollEffectOptions?: ScrollEffectOptions
```

标题滑动模糊样式。

**类型：** ScrollEffectOptions

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationTitleOptions-scrollEffectOptions?: ScrollEffectOptions--><!--Device-NavigationTitleOptions-scrollEffectOptions?: ScrollEffectOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## subTitleModifier

```TypeScript
subTitleModifier?: TextModifier
```

子标题属性修改器。

1. 通过Modifier设置的属性会覆盖系统默认的属性（如果Modifier设置了fontSize，maxFontSize，minFontSize任一属性，则系统设置的大小相关属性不生效，以开发者的设置为准）；2. 不设该属性或者设置了异常值，则恢复系统默认设置。

**类型：** TextModifier

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationTitleOptions-subTitleModifier?: TextModifier--><!--Device-NavigationTitleOptions-subTitleModifier?: TextModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: Material
```

为标题栏设置系统样式的材质。不同的材料有不同的效果，会影响titleBar的背景颜色、边框、阴影和其他视觉属性。设备行为差异：相同材料在不同设备上的效果可能不同，具体取决于他们的计算能力。

**类型：** Material

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationTitleOptions-systemMaterial?: Material--><!--Device-NavigationTitleOptions-systemMaterial?: Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

