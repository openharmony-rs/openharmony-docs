# UnionMode（系统接口）

设置融合效果模式。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## SMOOTH_UNION

```TypeScript
SMOOTH_UNION = 0
```

平滑的融合形变效果，适用于需要平滑过渡和自然连接的融合场景。

**说明：** 

设置该类型时，需后代组件设置[useUnionEffect](arkts-arkui-commonmethod-c-sys.md#useunioneffect)属性才能产生融合效果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## GRAVITY_UNION

```TypeScript
GRAVITY_UNION = 1
```

引力作用下的融合形变效果，适用于需要模拟引力吸引效果的融合场景，如元素间存在吸引和靠近趋势的视觉表现。

**说明：** 

设置该类型时，需配合[useUnionEffect](arkts-arkui-commonmethod-c-sys.md#useunioneffect)并设置[GravityCenterOptions](arkts-arkui-gravitycenteroptions-i-sys.md)的gravityCenter为true才能生效；不满足上述条件时，GRAVITY_UNION效果不生效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
