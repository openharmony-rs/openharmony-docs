# BoidsSimParameters（系统接口）

群组模拟参数，用于配置每个个体的行为属性。

> **说明：**
> 
> 模拟帧是指群组模拟中按固定时间步长执行的更新周期，类似Unity中的FixedUpdate。默认时间步长为16ms（约62.5FPS），模拟通过累积真实时间并按固定步长消耗来驱动。
> 下文部分参数的默认值基于该时间步长计算：
> - maxVelocityMag： 0.01 / 0.016 ≈ 0.625（m/s）。
> - maxAccelerationMag： maxVelocityMag / 0.016 ≈ 39.06（m/s²）。
> - maxTurnRate： π × 0.75 × 0.016 ≈ 0.0377（rad/模拟帧）。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## alignmentDistance

```TypeScript
alignmentDistance?: number
```

对齐规则的感知半径，单位为m。在该距离内（含边界）的邻近个体对对齐力有贡献。取值 &gt;= 0。默认值为0.0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## alignmentWeight

```TypeScript
alignmentWeight?: number
```

对齐规则权重。个体在alignmentDistance范围内朝向邻近个体平均航向的强度。取值 &gt;= 0。默认值为0.0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## boundaryDistance

```TypeScript
boundaryDistance?: number
```

边界约束力生效距离，单位为m。个体距边界墙面在该距离内时受到排斥力。取值 &gt;= 0。默认值为0.0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## boundaryMaxPos

```TypeScript
boundaryMaxPos?: Vec3
```

约束个体运动范围的轴对齐包围盒最大角点，各分量单位为m。默认值为(0, 0, 0)。

**类型：** [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## boundaryMinPos

```TypeScript
boundaryMinPos?: Vec3
```

约束个体运动范围的轴对齐包围盒最小角点，各分量单位为m。 当boundaryMinPos的任一分量大于或等于boundaryMaxPos对应分量时，该个体视为无边界约束。默认值为(0, 0, 0)。

**类型：** [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## boundaryWeight

```TypeScript
boundaryWeight?: number
```

边界约束力权重。个体在boundaryDistance范围内被边界墙推回的强度。取值 &gt;= 0。默认值为0.0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## cohesionDistance

```TypeScript
cohesionDistance?: number
```

凝聚规则的感知半径，单位为m。在该距离内（含边界）的邻近个体对凝聚力有贡献。取值 &gt;= 0。默认值为0.0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## cohesionWeight

```TypeScript
cohesionWeight?: number
```

凝聚规则权重。个体在cohesionDistance范围内朝向邻近个体平均位置吸引的强度。取值 &gt;= 0。默认值为0.0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## gravityWeight

```TypeScript
gravityWeight?: number
```

引力场权重。引力场对该个体的吸引强度。取值 &gt;= 0。默认值为0.0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## initialPosition

```TypeScript
initialPosition?: Vec3
```

每个个体的初始位置，各分量单位为m。未设置时保留当前实体位置。默认值为(NaN, NaN, NaN)。

**类型：** [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## initialRotation

```TypeScript
initialRotation?: Quaternion
```

每个个体的初始旋转方向的四元数。未设置时保留当前实体旋转方向的四元数。默认值为(NaN, NaN, NaN, NaN)。

**类型：** [Quaternion](arkts-arkgraphics3d-scenetypes-quaternion-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## initialVelocity

```TypeScript
initialVelocity?: Vec3
```

每个个体的初始速度向量，各分量单位为m/s。默认值为(0, 0, 0)。

**类型：** [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## maxAccelerationMag

```TypeScript
maxAccelerationMag?: number
```

个体每模拟帧可达到的最大加速度，单位为m/s²。取值 &gt;= 0。默认值约为39.06。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## maxTurnRate

```TypeScript
maxTurnRate?: Vec3
```

每模拟帧每轴最大转向速率，各分量单位为rad/模拟帧。每个分量取值 &gt;= 0。默认值各分量约为0.0377。

**类型：** [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## maxVelocityMag

```TypeScript
maxVelocityMag?: number
```

个体每模拟帧可达到的最大速度，单位为m/s。取值 &gt;= 0。默认值约为0.625。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## repulsionWeight

```TypeScript
repulsionWeight?: number
```

斥力场权重。斥力场对该个体的排斥强度。取值 &gt;= 0。默认值为0.0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## separationDistance

```TypeScript
separationDistance?: number
```

分离规则的感知半径，单位为m。仅严格在该距离内的邻近个体对分离力有贡献（边界处力为0）。取值 &gt;= 0。默认值为0.0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## separationWeight

```TypeScript
separationWeight?: number
```

分离规则权重。个体在separationDistance范围内受邻近个体排斥的强度。取值 &gt;= 0。默认值为0.0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。
