# DepthLightParams（系统接口）

光照参数。

**起始版本：** 26.0.0

<!--Device-unnamed-declare interface DepthLightParams--><!--Device-unnamed-declare interface DepthLightParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## color

```TypeScript
color: DepthColorRGB
```

光照颜色。

**类型：** DepthColorRGB

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DepthLightParams-color: DepthColorRGB--><!--Device-DepthLightParams-color: DepthColorRGB-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## direction

```TypeScript
direction: DepthVector3
```

光照方向向量。无单位，其值表示3D空间中的坐标。

**类型：** DepthVector3

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DepthLightParams-direction: DepthVector3--><!--Device-DepthLightParams-direction: DepthVector3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## intensity

```TypeScript
intensity: number
```

光照强度。无单位，取值范围[0, +∞)。

建议取值范围[0, 1]，当设置为0时，无光照。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DepthLightParams-intensity: double--><!--Device-DepthLightParams-intensity: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

