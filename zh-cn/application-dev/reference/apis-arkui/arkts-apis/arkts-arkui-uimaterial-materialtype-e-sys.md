# MaterialType

系统材质类型枚举。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 0
```

无系统材质效果。对应的效果为背景色backgroundColor为透明色，边框颜色borderColor为透明色，边框宽度borderWidth为0，无阴影shadow。

**系统接口：** 此接口为系统接口。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## SEMI_TRANSPARENT

```TypeScript
SEMI_TRANSPARENT = 1
```

半透明系统材质效果。对应的效果为：

背景色backgroundColor：浅色模式为"#f2f1f3f5"，深色模式为"#f2303131"。

边框颜色borderColor为theme.colors.compForegroundPrimary的[token](../../../ui/theme_skinning.md#系统缺省token色值)值以10%透明度（alpha值）进行混合叠加。

边框宽度borderWidth为1vp。

阴影shadow为ShadowStyle.OUTER_DEFAULT_SM。

**系统接口：** 此接口为系统接口。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
