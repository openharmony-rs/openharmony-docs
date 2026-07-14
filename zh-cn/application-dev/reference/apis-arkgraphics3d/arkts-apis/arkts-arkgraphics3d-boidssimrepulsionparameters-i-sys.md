# BoidsSimRepulsionParameters（系统接口）

Boids模拟斥力场参数。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## accelerationMag

```TypeScript
accelerationMag?: number
```

施加于boid、方向远离实体的排斥加速度大小。取值范围：[0, +∞)。默认值：0.0

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## radius

```TypeScript
radius?: number
```

作用半径。实体在此距离范围内的boid会被推开（边界处力为零）。取值范围：[0, +∞)。默认值：0.0

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

