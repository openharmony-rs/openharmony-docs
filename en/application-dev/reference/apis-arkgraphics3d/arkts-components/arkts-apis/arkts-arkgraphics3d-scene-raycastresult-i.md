# RaycastResult

Describes a result object from raycasting, containing details about the 3D object hit by the ray.

@typedef RaycastResult

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## centerDistance

```TypeScript
centerDistance: number
```

Distance from the center of the hit object's bounding box to the camera center, in scene units of the world coordinate system (such as cm, m, km, etc.). The value range is greater than 0.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## hitPosition

```TypeScript
hitPosition: Position3
```

Exact world coordinates of the collision point between the ray and the object ({x: number, y: number, z: number}), in scene units of the world coordinate system (such as cm, m, km, etc.).

**Type:** [Position3](arkts-arkgraphics3d-position3-t.md)

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## node

```TypeScript
node: Node
```

3D scene node hit by the ray. You can use this node to manipulate the target object (for example, moving, rotating, or hiding the object).

**Type:** [Node](arkts-arkgraphics3d-scenenodes-node-i.md)

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D
