# VignetteSettings

Describes the settings for vignette effects.

@typedef VignetteSettings

**Since:** 22

**System capability:** SystemCapability.ArkUi.Graphics3D

## intensity

```TypeScript
intensity?: number
```

Effect strength. The value range is [0, 1]. The value 0 indicates no vignetting effect, and the value 1 indicates maximum vignetting intensity. The default value is 0.4.

**Type:** number

**Default:** 0.4

**Since:** 22

**System capability:** SystemCapability.ArkUi.Graphics3D

## roundness

```TypeScript
roundness?: number
```

Application scope. The value range is [0, 1]. When the value is 0, the application scope is minimized. When the value is 1, the application scope is global. The default value is sqrt(0.5).

**Type:** number

**Default:** sqrt(0.5)

**Since:** 22

**System capability:** SystemCapability.ArkUi.Graphics3D
