# MaterialType（系统接口）

系统材质类型枚举。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-uiMaterial-export enum MaterialType--><!--Device-uiMaterial-export enum MaterialType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## NONE

```TypeScript
NONE = 0
```

无系统材质效果。对应的效果为背景色 [backgroundColor](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor)为 透明色，边框颜色borderColor为透明色，边框宽度borderWidth为0，无阴影 shadow。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MaterialType-NONE = 0--><!--Device-MaterialType-NONE = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## SEMI_TRANSPARENT

```TypeScript
SEMI_TRANSPARENT = 1
```

半透明系统材质效果。对应的效果为： 背景色 [backgroundColor](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor)： 浅色模式为"#f2f1f3f5"，深色模式为"#f2303131"。 边框颜色borderColor为混合10%的透明度的theme.colors.compForegroundPrimary的 [token](../../../ui/theme_skinning.md#系统缺省token色值)值。 边框宽度borderWidth为1vp。 阴影shadow为ShadowStyle.OUTER_DEFAULT_SM。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MaterialType-SEMI_TRANSPARENT = 1--><!--Device-MaterialType-SEMI_TRANSPARENT = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

