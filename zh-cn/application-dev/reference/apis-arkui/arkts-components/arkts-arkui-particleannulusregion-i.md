# ParticleAnnulusRegion

用于设置环形发射器区域的配置信息。

> **说明：** 
> 
> - outerRadius、innerRadius小于零或使用百分比单位时，会按零进行处理。
> 
> - 当outerRadius小于innerRadius时（即外圆半径小于内圆半径时），会将当前较小的值作为新的内圆半径，将较大的值作为新的外圆半径。
> 
> - 当endAngle小于startAngle时（即结束角度小于起始角度时），会将当前较小的值作为新的起始角度，将较大的值作为新的结束角度。
> 
> ![](../../../reference/apis-arkui/arkui-ts/figures/annulus.png)

**起始版本：** 20

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## center

```TypeScript
center?: PositionT<LengthMetrics>
```

圆环的圆心坐标，组件的左上角为坐标原点。默认值：{x:LengthMetrics.percent(0.5),y:LengthMetrics.percent(0.5)}

**类型：** [PositionT](arkts-arkui-positiont-t.md)&lt;[LengthMetrics](../arkts-apis/arkts-arkui-lengthmetrics-t.md)&gt;

**默认值：** {x:LengthMetrics.percent(0.5),y:LengthMetrics.percent(0.5)}

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## endAngle

```TypeScript
endAngle?: number
```

圆环的结束角度。

单位：度（°）

取值范围：(-∞, +∞)

默认值：360

**类型：** number

**默认值：** 360

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## innerRadius

```TypeScript
innerRadius: LengthMetrics
```

圆环的内圆半径。小于零或使用百分比单位时按零进行处理。当outerRadius小于innerRadius时，会将当前较小的值作为新的内圆半径，将较大的值作为新的外圆半径。

**类型：** [LengthMetrics](../arkts-apis/arkts-arkui-lengthmetrics-t.md)

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## outerRadius

```TypeScript
outerRadius: LengthMetrics
```

圆环的外圆半径。小于零或使用百分比单位时按零进行处理。当outerRadius小于innerRadius时，会将当前较小的值作为新的内圆半径，将较大的值作为新的外圆半径。

**类型：** [LengthMetrics](../arkts-apis/arkts-arkui-lengthmetrics-t.md)

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## startAngle

```TypeScript
startAngle?: number
```

圆环的起始角度。

单位：度（°）

取值范围：(-∞, +∞)

默认值：0

**类型：** number

**默认值：** 0

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
