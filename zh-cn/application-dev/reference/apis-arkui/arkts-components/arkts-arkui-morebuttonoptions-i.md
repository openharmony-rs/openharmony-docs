# MoreButtonOptions

更多图标的菜单选项。设置后，可自定义更多按钮的背景模糊样式、背景效果等。

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**废弃版本：** -1

<!--Device-unnamed-declare interface MoreButtonOptions--><!--Device-unnamed-declare interface MoreButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

更多图标的菜单背景模糊样式，设置后，更多图标的菜单将应用指定的模糊样式；不设置时关闭背景模糊效果。

**类型：** BlurStyle

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-MoreButtonOptions-backgroundBlurStyle?: BlurStyle--><!--Device-MoreButtonOptions-backgroundBlurStyle?: BlurStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

更多图标的菜单背景模糊选项。 **说明：** 只在设置了backgroundBlurStyle时生效。 不建议与backgroundEffect同时使用。

**类型：** BackgroundBlurStyleOptions

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-MoreButtonOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-MoreButtonOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

设置更多图标的菜单背景属性包括：模糊半径，亮度，饱和度，颜色等。 **说明：** 不建议与backgroundBlurStyleOptions同时使用。

**类型：** BackgroundEffectOptions

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-MoreButtonOptions-backgroundEffect?: BackgroundEffectOptions--><!--Device-MoreButtonOptions-backgroundEffect?: BackgroundEffectOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

