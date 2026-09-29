# FieldRegion

```TypeScript
declare interface FieldRegion
```

用于设置粒子场的区域信息。

**起始版本：** 22

<!--Device-unnamed-declare interface FieldRegion--><!--Device-unnamed-declare interface FieldRegion-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position?: PositionT<number>
```

粒子场的区域中心位置。坐标单位为vp。

默认值：{x:0, y:0}

**类型：** [PositionT](arkts-arkui-particle-comp-positiont-t.md)&lt;number&gt;

**默认值：** {x:0,y:0}

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-FieldRegion-position?: PositionT<number>--><!--Device-FieldRegion-position?: PositionT<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shape

```TypeScript
shape?: DisturbanceFieldShape
```

粒子场的区域形状。

默认值：DisturbanceFieldShape.RECT

**类型：** [DisturbanceFieldShape](arkts-arkui-particle-comp-disturbancefieldshape-e.md)

**默认值：** DisturbanceFieldShape.RECT

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-FieldRegion-shape?: DisturbanceFieldShape--><!--Device-FieldRegion-shape?: DisturbanceFieldShape-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: SizeT<number>
```

粒子场的区域大小。值的单位为vp。

默认值：{width:0, height:0}

取值范围：

width：[0, +∞)

height：[0, +∞)

当size的width（或height）设置为负值时取width（或height）的默认值。

**类型：** [SizeT](arkts-arkui-particle-comp-sizet-t.md)&lt;number&gt;

**默认值：** {width:0,height:0}

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-FieldRegion-size?: SizeT<number>--><!--Device-FieldRegion-size?: SizeT<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
