# BoidsSimRepulsionParameters (System API)

Repulsion field parameters, used to configure the repulsion field in the scene.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## accelerationMag

```TypeScript
accelerationMag?: number
```

The magnitude of the repulsion acceleration applied to the individual, whose direction points away from the repulsion field entity. Value &gt;= 0. Default value is 0.0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## radius

```TypeScript
radius?: number
```

The radius of the repulsion field. Only individuals strictly within this distance are repelled (boundary force is 0). Value &gt;= 0. Default value is 0.0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.
