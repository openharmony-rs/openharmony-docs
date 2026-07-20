# VelocityFieldOptions

用于描述粒子速度场信息的参数。

**起始版本：** 22

<!--Device-unnamed-declare interface VelocityFieldOptions--><!--Device-unnamed-declare interface VelocityFieldOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## region

```TypeScript
region?: FieldRegion
```

The region influenced by the velocity field.

**类型：** FieldRegion

**默认值：** {shape:DisturbanceFieldShape.RECT,position:{x:0,y:0},size:{width:0,height:0}}

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-VelocityFieldOptions-region?: FieldRegion--><!--Device-VelocityFieldOptions-region?: FieldRegion-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## velocity

```TypeScript
velocity?: Vector2T<number>
```

The velocity values in each direction of the velocity field. Particles only acquire this velocity when within the range of the velocity field; once they leave the range of the velocity field, they are no longer influenced by it and do not gain this additional velocity.

**类型：** Vector2T&lt;number&gt;

**默认值：** {x:0,y:0}

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-VelocityFieldOptions-velocity?: Vector2T<number>--><!--Device-VelocityFieldOptions-velocity?: Vector2T<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

