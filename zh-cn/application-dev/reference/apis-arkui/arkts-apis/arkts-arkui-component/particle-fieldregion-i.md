# FieldRegion

用于设置粒子场的区域信息。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

<!--Device-unnamed-export declare interface FieldRegion--><!--Device-unnamed-export declare interface FieldRegion-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position?: PositionT<double>
```

The coordinates of the center position of the field. The top-left corner of the component is the origin of the coordinate system. The coordinate unit is vp.

**类型：** PositionT&lt;double&gt;

**默认值：** {x:0,y:0}

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FieldRegion-position?: PositionT<double>--><!--Device-FieldRegion-position?: PositionT<double>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shape

```TypeScript
shape?: DisturbanceFieldShape
```

The shape of the field

**类型：** DisturbanceFieldShape

**默认值：** DisturbanceFieldShape.RECT

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FieldRegion-shape?: DisturbanceFieldShape--><!--Device-FieldRegion-shape?: DisturbanceFieldShape-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: SizeT<double>
```

The size of the field. The unit of value is vp.

**类型：** SizeT&lt;double&gt;

**默认值：** {width:0,height:0}

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FieldRegion-size?: SizeT<double>--><!--Device-FieldRegion-size?: SizeT<double>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

