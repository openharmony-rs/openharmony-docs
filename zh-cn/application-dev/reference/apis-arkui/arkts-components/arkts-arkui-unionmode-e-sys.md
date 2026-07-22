# UnionMode（系统接口）

融合效果枚举。

**起始版本：** 26.0.0

<!--Device-unnamed-declare enum UnionMode--><!--Device-unnamed-declare enum UnionMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## SMOOTH_UNION

```TypeScript
SMOOTH_UNION = 0
```

平滑的融合形变效果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UnionMode-SMOOTH_UNION = 0--><!--Device-UnionMode-SMOOTH_UNION = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## GRAVITY_UNION

```TypeScript
GRAVITY_UNION = 1
```

引力作用下的融合形变效果。

**说明：**

设置该类型时，需要结合[useUnionEffect](arkts-arkui-commonmethod-c-sys.md#useunioneffect)并设置[GravityCenterOptions](arkts-arkui-gravitycenteroptions-i-sys.md)的gravityCenter为true才能生效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UnionMode-GRAVITY_UNION = 1--><!--Device-UnionMode-GRAVITY_UNION = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

