# Light

```TypeScript
export interface Light extends Node
```

Light node, which inherits from Node.

@extends Node @interface Light

**Inheritance/Implementation:** Light extends [Node](arkts-arkgraphics3d-scenenodes-node-i.md)

**Since:** 12

<!--Device-unnamed-export interface Light extends Node--><!--Device-unnamed-export interface Light extends Node-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## color

```TypeScript
color: Color
```

Color.

**Type:** [Color](arkts-arkgraphics3d-scenetypes-color-i.md)

**Since:** 12

<!--Device-Light-color: Color--><!--Device-Light-color: Color-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## enabled

```TypeScript
enabled: boolean
```

Whether the light is used. true if used, false otherwise.

**Type:** boolean

**Since:** 12

<!--Device-Light-enabled: boolean--><!--Device-Light-enabled: boolean-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## intensity

```TypeScript
intensity: number
```

Light density in candelas (cd) with a value range of real numbers greater than 0.

**Type:** number

**Since:** 12

<!--Device-Light-intensity: double--><!--Device-Light-intensity: double-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## lightType

```TypeScript
readonly lightType: LightType
```

Light type.

**Type:** [LightType](arkts-arkgraphics3d-scenenodes-lighttype-e.md)

**Since:** 12

<!--Device-Light-readonly lightType: LightType--><!--Device-Light-readonly lightType: LightType-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## shadowEnabled

```TypeScript
shadowEnabled: boolean
```

Whether the shadow effect is enabled. true if enabled, false otherwise.

**Type:** boolean

**Since:** 12

<!--Device-Light-shadowEnabled: boolean--><!--Device-Light-shadowEnabled: boolean-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D
