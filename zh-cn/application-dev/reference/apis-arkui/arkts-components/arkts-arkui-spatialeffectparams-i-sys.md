# SpatialEffectParams（系统接口）

空间效果选项。@interface SpatialEffectParams

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## occlusionWeight

```TypeScript
occlusionWeight?: number
```

空间效果的遮挡权重。 取值范围:[0, 1]。默认值:0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## position

```TypeScript
position: SpatialPosition | number
```

由角点或深度值定义的空间位置。

**类型：** [SpatialPosition](arkts-arkui-spatialposition-i-sys.md) \| number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
