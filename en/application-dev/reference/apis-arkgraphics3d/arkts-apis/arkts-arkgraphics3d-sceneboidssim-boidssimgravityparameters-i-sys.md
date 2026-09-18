# BoidsSimGravityParameters (System API)

Attraction field parameters, used to configure the attraction field in the scene.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## accelerationMag

```TypeScript
accelerationMag?: number
```

The magnitude of the attraction acceleration applied to the individual, with the direction pointing toward the attraction field entity. Value &gt;= 0. Default value: 0.0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## radius

```TypeScript
radius?: number
```

The radius of the attraction field. Only individuals strictly within this distance are attracted (boundary force is 0). Value &gt;= 0. Default value: 0.0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.
