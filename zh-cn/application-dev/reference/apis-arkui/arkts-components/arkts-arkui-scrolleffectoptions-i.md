# ScrollEffectOptions

定义标题栏的滑动模糊效果选项。

**起始版本：** 26.0.0

<!--Device-unnamed-declare interface ScrollEffectOptions--><!--Device-unnamed-declare interface ScrollEffectOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## blurEffectiveEndOffset

```TypeScript
blurEffectiveEndOffset?: LengthMetrics
```

达到标题栏最终模糊样式的最大滑动距离。当用户滑动距离达到该值时，模糊效果达到最终状态。 默认值： 8vp。

**类型：** LengthMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollEffectOptions-blurEffectiveEndOffset?: LengthMetrics--><!--Device-ScrollEffectOptions-blurEffectiveEndOffset?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## blurEffectiveStartOffset

```TypeScript
blurEffectiveStartOffset?: LengthMetrics
```

启用标题栏滚动模糊效果的最小滑动距离。当用户滑动距离超过该值时，开始应用模糊效果。 默认值： 0vp。

**类型：** LengthMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollEffectOptions-blurEffectiveStartOffset?: LengthMetrics--><!--Device-ScrollEffectOptions-blurEffectiveStartOffset?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scrollEffectType

```TypeScript
scrollEffectType?: ScrollEffectType
```

标题栏滚动模糊效果类型。 默认值： ScrollEffectType.COMMON_BLUR。

**类型：** [ScrollEffectType](arkts-arkui-scrolleffecttype-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollEffectOptions-scrollEffectType?: ScrollEffectType--><!--Device-ScrollEffectOptions-scrollEffectType?: ScrollEffectType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

