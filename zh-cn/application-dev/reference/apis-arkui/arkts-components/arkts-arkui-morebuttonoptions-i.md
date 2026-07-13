# MoreButtonOptions

更多图标的菜单选项。

**起始版本：** 19

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

更多图标的菜单背景模糊样式，不设置时关闭背景模糊效果。

**类型：** BlurStyle

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

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

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

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

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

