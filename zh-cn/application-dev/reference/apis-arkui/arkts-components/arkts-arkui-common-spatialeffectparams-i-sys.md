# SpatialEffectParams（系统接口）

空间效果选项。

**起始版本：** 26.0.0

<!--Device-unnamed-declare interface SpatialEffectParams--><!--Device-unnamed-declare interface SpatialEffectParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## occlusionWeight

```TypeScript
occlusionWeight?: number
```

空间效果的遮挡权重。<br>取值范围:[0, 1]。默认值:0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SpatialEffectParams-occlusionWeight?: double--><!--Device-SpatialEffectParams-occlusionWeight?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## position

```TypeScript
position: SpatialPosition | number
```

由角点或深度值定义的空间位置。

**类型：** SpatialPosition | number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SpatialEffectParams-position: SpatialPosition | double--><!--Device-SpatialEffectParams-position: SpatialPosition | double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

