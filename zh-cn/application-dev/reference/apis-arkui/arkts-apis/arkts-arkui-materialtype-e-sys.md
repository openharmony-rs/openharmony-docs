# MaterialType（系统接口）

系统材质类型枚举。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## NONE

```TypeScript
NONE = 0
```

无系统材质效果。对应的效果为背景色
[backgroundColor](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor)为
透明色，边框颜色[borderColor](../arkts-components/arkts-arkui-commonmethod-c.md#bordercolor-1)为透明色，边框宽度[borderWidth](../arkts-components/arkts-arkui-commonmethod-c.md#borderwidth-1)为0，无阴影
[shadow](../arkts-components/arkts-arkui-commonmethod-c.md#shadow-1)。

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

背景色
[backgroundColor](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor)：
浅色模式为"#f2f1f3f5"，深色模式为"#f2303131"。

边框颜色[borderColor](../arkts-components/arkts-arkui-commonmethod-c.md#bordercolor-1)为混合10%的透明度的theme.colors.compForegroundPrimary的
[token](../../../../ui/theme_skinning.md#系统缺省token色值)值。

边框宽度[borderWidth](../arkts-components/arkts-arkui-commonmethod-c.md#borderwidth-1)为1vp。

阴影[shadow](../arkts-components/arkts-arkui-commonmethod-c.md#shadow-1)为ShadowStyle.OUTER_DEFAULT_SM。

**系统接口：** 此接口为系统接口。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

