# MaterialType

系统材质类型枚举。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

<!--Device-uiMaterial-enum MaterialType--><!--Device-uiMaterial-enum MaterialType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 0
```

无系统材质效果。对应的效果为背景色 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_为 透明色，边框颜色[borderColor]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_为透明色，边框宽度[borderWidth]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_为0，无阴影 [shadow]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_。 **系统接口：** 此接口为系统接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-MaterialType-NONE = 0--><!--Device-MaterialType-NONE = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SEMI_TRANSPARENT

```TypeScript
SEMI_TRANSPARENT = 1
```

半透明系统材质效果。对应的效果为： 背景色 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_： 浅色模式为"#f2f1f3f5"，深色模式为"#f2303131"。 边框颜色[borderColor]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_为混合10%的透明度的theme.colors.compForegroundPrimary的 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_值。 边框宽度[borderWidth]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_为1vp。 阴影[shadow]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_为ShadowStyle.OUTER\_DEFAULT\_SM。 **系统接口：** 此接口为系统接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-MaterialType-SEMI_TRANSPARENT = 1--><!--Device-MaterialType-SEMI_TRANSPARENT = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## IMMERSIVE

```TypeScript
IMMERSIVE = 2
```

沉浸式材质类型。仅用于[MaterialInfo]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接口的type属性标识当前配置的材质类型，不映射到底层功能。实际材质效果通过 [ImmersiveMaterial]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_类实现。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MaterialType-IMMERSIVE = 2--><!--Device-MaterialType-IMMERSIVE = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

