# FieldRegion

用于设置粒子场的区域信息。

**起始版本：** 22

<!--Device-unnamed-declare interface FieldRegion--><!--Device-unnamed-declare interface FieldRegion-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position?: PositionT<number>
```

The coordinates of the center position of the field. The top-left corner of the component is the origin of the coordinate system. The coordinate unit is vp.

**类型：** PositionT&lt;number&gt;

**默认值：** {x:0,y:0}

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FieldRegion-position?: PositionT<number>--><!--Device-FieldRegion-position?: PositionT<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shape

```TypeScript
shape?: DisturbanceFieldShape
```

The shape of the field

**类型：** DisturbanceFieldShape

**默认值：** DisturbanceFieldShape.RECT

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FieldRegion-shape?: DisturbanceFieldShape--><!--Device-FieldRegion-shape?: DisturbanceFieldShape-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: SizeT<number>
```

The size of the field. The unit of value is vp.

**类型：** SizeT&lt;number&gt;

**默认值：** {width:0,height:0}

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FieldRegion-size?: SizeT<number>--><!--Device-FieldRegion-size?: SizeT<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

