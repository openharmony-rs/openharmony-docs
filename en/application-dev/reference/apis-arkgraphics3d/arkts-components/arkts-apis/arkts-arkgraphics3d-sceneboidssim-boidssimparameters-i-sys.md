# BoidsSimParameters (System API)

```TypeScript
export interface BoidsSimParameters
```

Boids simulation parameters used to configure the behavioral attributes of each individual.

> **NOTE:** 
> 
> A simulation frame refers to the update cycle executed at a fixed time step in the Boids simulation, similar to FixedUpdate in Unity.
> The default time step is 16 ms (approximately 62.5 FPS). The simulation is driven by accumulating real time and consuming it in fixed steps.
> The default values of some parameters below are calculated based on this time step:
> - maxVelocityMag: 0.01 / 0.016 ≈ 0.625 (m/s).
> - maxAccelerationMag: maxVelocityMag / 0.016 ≈ 39.06 (m/s²).
> - maxTurnRate: π × 0.75 × 0.016 ≈ 0.0377 (rad/simulation frame).

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## alignmentDistance

```TypeScript
alignmentDistance?: number
```

Perception radius of the alignment rule. Unit is m. Neighboring individuals within this distance (inclusive) contribute to the alignment force. Value &gt;= 0. Default value: 0.0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## alignmentWeight

```TypeScript
alignmentWeight?: number
```

Weight of the alignment rule. The intensity with which the individual steers toward the average heading of neighboring individuals within the alignmentDistance. Value &gt;= 0. Default value: 0.0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## boundaryDistance

```TypeScript
boundaryDistance?: number
```

Effective distance of the boundary constraint force. Unit is m. The individual is subject to a repulsive force when its distance to the boundary wall is within this distance. Value &gt;= 0. Default value: 0.0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## boundaryMaxPos

```TypeScript
boundaryMaxPos?: Vec3
```

Maximum corner of the axis-aligned bounding box that constrains the individual's movement range. Each component unit is m. Default value: (0, 0, 0).

**Type:** [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## boundaryMinPos

```TypeScript
boundaryMinPos?: Vec3
```

Minimum corner of the axis-aligned bounding box that constrains the individual's movement range. Each component unit is m. When any component of boundaryMinPos is greater than or equal to the corresponding component of boundaryMaxPos, the individual is considered to have no boundary constraint. Default value: (0, 0, 0).

**Type:** [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## boundaryWeight

```TypeScript
boundaryWeight?: number
```

Weight of the boundary constraint force. The intensity with which the individual is pushed back by the boundary wall within the boundaryDistance. Value &gt;= 0. Default value: 0.0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## cohesionDistance

```TypeScript
cohesionDistance?: number
```

Perception radius of the cohesion rule. Unit is m. Neighboring individuals within this distance (inclusive) contribute to the cohesion force. Value &gt;= 0. Default value: 0.0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## cohesionWeight

```TypeScript
cohesionWeight?: number
```

Weight of the cohesion rule. The intensity with which the individual is attracted toward the average position of neighboring individuals within the cohesionDistance. Value &gt;= 0. Default value: 0.0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## gravityWeight

```TypeScript
gravityWeight?: number
```

Attraction intensity of the attraction field on this individual. Value &gt;= 0. Default value: 0.0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## initialPosition

```TypeScript
initialPosition?: Vec3
```

Initial position of each individual. Each component unit is m. If not set, the current entity position is retained. Default value: (NaN, NaN, NaN).

**Type:** [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## initialRotation

```TypeScript
initialRotation?: Quaternion
```

Quaternion of the initial rotation direction of each individual. If not set, the quaternion of the current entity rotation direction is retained. Default value: (NaN, NaN, NaN, NaN).

**Type:** [Quaternion](arkts-arkgraphics3d-scenetypes-quaternion-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## initialVelocity

```TypeScript
initialVelocity?: Vec3
```

Initial velocity vector of each individual. Each component unit is m/s. Default value: (0, 0, 0).

**Type:** [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## maxAccelerationMag

```TypeScript
maxAccelerationMag?: number
```

Maximum acceleration that the individual can reach per simulation frame. Unit is m/s². Value &gt;= 0. Default value is approximately 39.06.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## maxTurnRate

```TypeScript
maxTurnRate?: Vec3
```

Maximum turn rate per axis per simulation frame. Each component unit is rad/simulation frame. Each component value &gt;= 0. Default value for each component is approximately 0.0377.

**Type:** [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## maxVelocityMag

```TypeScript
maxVelocityMag?: number
```

Maximum velocity that the individual can reach per simulation frame. Unit is m/s. Value &gt;= 0. Default value is approximately 0.625.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## repulsionWeight

```TypeScript
repulsionWeight?: number
```

Repulsion intensity of the repulsion field on this individual. Value &gt;= 0. Default value: 0.0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## separationDistance

```TypeScript
separationDistance?: number
```

Perception radius of the separation rule. Unit is m. Only neighboring individuals strictly within this distance contribute to the separation force (boundary force is 0). Value &gt;= 0. Default value: 0.0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## separationWeight

```TypeScript
separationWeight?: number
```

Weight of the separation rule. The intensity with which the individual is repelled by neighboring individuals within the separationDistance. Value &gt;= 0. Default value: 0.0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.
