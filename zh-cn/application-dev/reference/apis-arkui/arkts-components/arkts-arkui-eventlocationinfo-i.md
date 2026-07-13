# EventLocationInfo

用于点击手势获取点击位置坐标。

**起始版本：** 20

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getCurrentLocalPosition

```TypeScript
getCurrentLocalPosition?(): Coordinate2D
```

获取点击位置相对于当前组件实时位置的左上角坐标。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Coordinate2D | - 点击位置相对于当前组件实时位置的左上角坐标。 |

## displayX

```TypeScript
displayX: number
```

相对于屏幕的左上角X坐标。

取值范围：[0, +∞)

单位：vp

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayY

```TypeScript
displayY: number
```

相对于屏幕的左上角Y坐标。

取值范围：[0, +∞)

单位：vp

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayX

```TypeScript
globalDisplayX?: number
```

相对于主屏幕左上角为原点的坐标系中的X坐标。

单位：vp

取值范围：[0, +∞)

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayY

```TypeScript
globalDisplayY?: number
```

相对于主屏幕左上角为原点的坐标系中的Y坐标。

单位：vp

取值范围：[0, +∞)

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowX

```TypeScript
windowX: number
```

相对于窗口的左上角X坐标。

取值范围：[0, +∞)

单位：vp

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowY

```TypeScript
windowY: number
```

相对于窗口的左上角Y坐标。

取值范围：[0, +∞)

单位：vp

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x: number
```

相对于组件左上角的X坐标。

取值范围：[0, +∞)

单位：vp

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y: number
```

相对于组件左上角的Y坐标。

取值范围：[0, +∞)

单位：vp

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

