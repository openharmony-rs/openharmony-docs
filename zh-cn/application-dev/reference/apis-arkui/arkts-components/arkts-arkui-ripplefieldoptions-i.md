# RippleFieldOptions

用于描述粒子波动场信息的参数。

**起始版本：** 22

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## amplitude

```TypeScript
amplitude?: number
```

描述粒子波动场波的幅值。幅值越大，波动场的力越大，粒子在波动场作用下产生的位移变化越明显，波纹扩散效果越强烈。

取值范围：[0, +∞)

默认值：0

设置为负值时取默认值。

**类型：** number

**默认值：** 0

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attenuation

```TypeScript
attenuation?: number
```

描述粒子波动场波的衰减系数。衰减系数越大，则随时间的变化，波的衰减越快，粒子受到的波动场力随时间迅速减弱，波纹扩散效果逐渐消失。

取值范围：[0, 1]

默认值：0.0

设置的数值不在范围内时取默认值。

**类型：** number

**默认值：** 0

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## center

```TypeScript
center?: PositionT<number>
```

粒子波动场产生力的中心位置。组件的左上角为坐标原点。坐标单位为vp。

默认值：{x:0, y:0}

**类型：** [PositionT](arkts-arkui-positiont-t.md)&lt;number&gt;

**默认值：** {x:0,y:0}

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## region

```TypeScript
region?: FieldRegion
```

粒子波动场影响的区域信息，其中区域信息包括区域形状、区域大小以及区域中心位置。

默认值：{shape:DisturbanceFieldShape.RECT, position:{x:0, y:0}, size:{width:0, height:0}}

**类型：** [FieldRegion](arkts-arkui-fieldregion-i.md)

**默认值：** {shape:DisturbanceFieldShape.RECT,position:{x:0,y:0},size:{width:0,height:0}}

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## wavelength

```TypeScript
wavelength?: number
```

描述粒子波动场的波长，即一个波周期的变化距离。波长越大，则随距离的变化，波的变化越慢，波动越不明显，粒子受波动影响的周期变长。

取值范围：[0, +∞)

默认值：0

设置为负值时取默认值。

**类型：** number

**默认值：** 0

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## waveSpeed

```TypeScript
waveSpeed?: number
```

描述粒子波动场的波速。波速越大，则随时间的变化，波的变化越快，波动越明显，粒子受波动影响的响应越迅速。单位：vp/s。

取值范围：[0, +∞)

默认值：0

设置为负值时取默认值。

**类型：** number

**默认值：** 0

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
