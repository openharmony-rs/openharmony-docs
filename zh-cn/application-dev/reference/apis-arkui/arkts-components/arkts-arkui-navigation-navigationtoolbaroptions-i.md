# NavigationToolbarOptions

工具栏选项。

**起始版本：** 11

<!--Device-unnamed-declare interface NavigationToolbarOptions--><!--Device-unnamed-declare interface NavigationToolbarOptions-End-->

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

<!--Device-NavigationToolbarOptions-backgroundBlurStyle?: BlurStyle--><!--Device-NavigationToolbarOptions-backgroundBlurStyle?: BlurStyle-End-->

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

<!--Device-NavigationToolbarOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-NavigationToolbarOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

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

<!--Device-NavigationToolbarOptions-backgroundColor?: ResourceColor--><!--Device-NavigationToolbarOptions-backgroundColor?: ResourceColor-End-->

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

<!--Device-NavigationToolbarOptions-backgroundEffect?: BackgroundEffectOptions--><!--Device-NavigationToolbarOptions-backgroundEffect?: BackgroundEffectOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## barStyle

```TypeScript
barStyle?: BarStyle
```

设置工具栏布局方式。

默认值：BarStyle.STANDARD

**类型：** BarStyle

**默认值：** BarStyle.STANDARD

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationToolbarOptions-barStyle?: BarStyle--><!--Device-NavigationToolbarOptions-barStyle?: BarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hideItemValue

```TypeScript
hideItemValue?: boolean
```

设置是否隐藏工具栏的文本，默认显示文本。

true：隐藏工具栏的文本；false：不隐藏工具栏的文本。

默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationToolbarOptions-hideItemValue?: boolean--><!--Device-NavigationToolbarOptions-hideItemValue?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## moreButtonOptions

```TypeScript
moreButtonOptions?: MoreButtonOptions
```

工具栏更多图标的菜单选项。

**类型：** MoreButtonOptions

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationToolbarOptions-moreButtonOptions?: MoreButtonOptions--><!--Device-NavigationToolbarOptions-moreButtonOptions?: MoreButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

