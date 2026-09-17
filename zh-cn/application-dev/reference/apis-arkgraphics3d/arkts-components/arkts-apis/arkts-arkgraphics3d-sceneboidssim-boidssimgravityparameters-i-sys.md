# BoidsSimGravityParameters（系统接口）

引力场参数，用于配置场景中的引力场。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## accelerationMag

```TypeScript
accelerationMag?: number
```

施加于个体的吸引加速度大小，其方向指向引力场实体。取值 &gt;= 0。默认值为0.0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## radius

```TypeScript
radius?: number
```

引力场的作用半径。仅严格在该距离内的个体受到吸引（边界处力为0）。取值 &gt;= 0。默认值为0.0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。
