# ExposureMeteringMode

Enumerates the exposure metering modes.

**Since:** 24

**System capability:** SystemCapability.Multimedia.Camera.Core

## MATRIX

```TypeScript
MATRIX = 0
```

Matrix metering mode. A wide area of the screen is selected, which is ideal for shooting natural landscapes.

**Since:** 24

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core

## CENTER

```TypeScript
CENTER = 1
```

Center-weighted metering mode. Metering is performed on the entire image, with the center allocated with the maximum weight, which is ideal for shooting portraits.

**Since:** 24

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core

## SPOT

```TypeScript
SPOT = 2
```

Spot metering mode. Metering is performed around 2.5% of the metering points, focusing on the light in a specific small area, such as the eyes of the subject.

**Since:** 24

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core
