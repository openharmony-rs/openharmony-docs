# BoidsSimParameters（系统接口）

每个boid绑定的群组模拟参数.

**起始版本：** 26.0.0

<!--Device-unnamed-export interface BoidsSimParameters--><!--Device-unnamed-export interface BoidsSimParameters-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## alignmentDistance

```TypeScript
alignmentDistance?: number
```

对齐规则的感知半径。此距离范围内的boid会对齐航向。取值范围：[0, +∞)。默认值：0.0

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimParameters-alignmentDistance?: double--><!--Device-BoidsSimParameters-alignmentDistance?: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## alignmentWeight

```TypeScript
alignmentWeight?: number
```

boid在alignmentDistance范围内匹配邻近个体平均航向的强度。取值范围：[0, +∞)。默认值：0.0

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimParameters-alignmentWeight?: double--><!--Device-BoidsSimParameters-alignmentWeight?: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## boundaryDistance

```TypeScript
boundaryDistance?: number
```

边界斥力生效的距离。取值范围：[0, +∞)。默认值：0.0

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimParameters-boundaryDistance?: double--><!--Device-BoidsSimParameters-boundaryDistance?: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## boundaryMaxPos

```TypeScript
boundaryMaxPos?: Vec3
```

约束boid运动的轴对齐包围盒最大角点. 默认值：(0, 0, 0).

**类型：** Vec3

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimParameters-boundaryMaxPos?: Vec3--><!--Device-BoidsSimParameters-boundaryMaxPos?: Vec3-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## boundaryMinPos

```TypeScript
boundaryMinPos?: Vec3
```

约束boid运动的轴对齐包围盒最小角点。当boundaryMinPos的任何分量大于等于对应boundaryMaxPos分量时，该boid被视为无边界。默认值：(0, 0, 0)。

**类型：** Vec3

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimParameters-boundaryMinPos?: Vec3--><!--Device-BoidsSimParameters-boundaryMinPos?: Vec3-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## boundaryWeight

```TypeScript
boundaryWeight?: number
```

boid在boundaryDistance范围内被边界墙推回的强度。取值范围：[0, +∞)。默认值：0.0

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimParameters-boundaryWeight?: double--><!--Device-BoidsSimParameters-boundaryWeight?: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## cohesionDistance

```TypeScript
cohesionDistance?: number
```

凝聚规则的感知半径。此距离范围内的boid会相互聚集。取值范围：[0, +∞)。默认值：0.0

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimParameters-cohesionDistance?: double--><!--Device-BoidsSimParameters-cohesionDistance?: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## cohesionWeight

```TypeScript
cohesionWeight?: number
```

boid在cohesionDistance范围内朝向邻近个体平均位置的强度。取值范围：[0, +∞)。默认值：0.0

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimParameters-cohesionWeight?: double--><!--Device-BoidsSimParameters-cohesionWeight?: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## gravityWeight

```TypeScript
gravityWeight?: number
```

引力场对该boid的吸引强度。取值范围：[0, +∞)。默认值：0.0

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimParameters-gravityWeight?: double--><!--Device-BoidsSimParameters-gravityWeight?: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## initialPosition

```TypeScript
initialPosition?: Vec3
```

boid的初始位置. 未设置时，使用实体的当前变换位置.默认值：(NaN, NaN, NaN).

**类型：** Vec3

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimParameters-initialPosition?: Vec3--><!--Device-BoidsSimParameters-initialPosition?: Vec3-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## initialRotation

```TypeScript
initialRotation?: Quaternion
```

boid的初始旋转. 未设置时，使用实体的当前变换旋转.默认值：(NaN, NaN, NaN, NaN).

**类型：** Quaternion

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimParameters-initialRotation?: Quaternion--><!--Device-BoidsSimParameters-initialRotation?: Quaternion-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## initialVelocity

```TypeScript
initialVelocity?: Vec3
```

boid的初始速度. 默认值：(0, 0, 0).

**类型：** Vec3

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimParameters-initialVelocity?: Vec3--><!--Device-BoidsSimParameters-initialVelocity?: Vec3-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## maxAccelerationMag

```TypeScript
maxAccelerationMag?: number
```

boid每模拟帧可达到的最大加速度. 取值范围：[0, +∞). 默认值：约为39.06.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimParameters-maxAccelerationMag?: double--><!--Device-BoidsSimParameters-maxAccelerationMag?: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## maxTurnRate

```TypeScript
maxTurnRate?: Vec3
```

每模拟帧每轴最大转向速率. 取值范围：[0, +∞) per axis.默认值：每轴约为0.0377.

**类型：** Vec3

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimParameters-maxTurnRate?: Vec3--><!--Device-BoidsSimParameters-maxTurnRate?: Vec3-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## maxVelocityMag

```TypeScript
maxVelocityMag?: number
```

boid每模拟帧可达到的最大速度. 取值范围：[0, +∞). 默认值：约为0.625.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimParameters-maxVelocityMag?: double--><!--Device-BoidsSimParameters-maxVelocityMag?: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## repulsionWeight

```TypeScript
repulsionWeight?: number
```

斥力场对该boid的排斥强度。取值范围：[0, +∞)。默认值：0.0

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimParameters-repulsionWeight?: double--><!--Device-BoidsSimParameters-repulsionWeight?: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## separationDistance

```TypeScript
separationDistance?: number
```

分离规则的感知半径。此距离范围内的boid会产生分离力（边界处力为零）。取值范围：[0, +∞)。默认值：0.0

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimParameters-separationDistance?: double--><!--Device-BoidsSimParameters-separationDistance?: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## separationWeight

```TypeScript
separationWeight?: number
```

boid在separationDistance范围内避开邻近个体的强度。取值范围：[0, +∞)。默认值：0.0

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimParameters-separationWeight?: double--><!--Device-BoidsSimParameters-separationWeight?: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

