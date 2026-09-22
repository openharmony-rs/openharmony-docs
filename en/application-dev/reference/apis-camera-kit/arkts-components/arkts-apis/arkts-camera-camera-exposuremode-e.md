# ExposureMode

```TypeScript
enum ExposureMode
```

Enumerates the exposure modes.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Camera.Core

## EXPOSURE_MODE_UNSPECIFIED

```TypeScript
EXPOSURE_MODE_UNSPECIFIED = -1
```

Unspecified exposure.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core

## EXPOSURE_MODE_LOCKED

```TypeScript
EXPOSURE_MODE_LOCKED = 0
```

Exposure locked. The metering point cannot be set.

After this mode is used, the exposure will be locked by default for each photo capture.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

## EXPOSURE_MODE_AUTO

```TypeScript
EXPOSURE_MODE_AUTO = 1
```

Auto exposure. The metering point can be set by calling [AutoExposure.setMeteringPoint](arkts-camera-camera-autoexposure-i.md#setmeteringpoint).

After this mode is used, it takes effect only for the first photo capture.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

## EXPOSURE_MODE_CONTINUOUS_AUTO

```TypeScript
EXPOSURE_MODE_CONTINUOUS_AUTO = 2
```

Continuous auto exposure. The metering point cannot be set.

After this mode is used, the camera system automatically adjusts the exposure based on the environment changes each time.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

## EXPOSURE_MODE_MANUAL

```TypeScript
EXPOSURE_MODE_MANUAL = 3
```

Manual exposure. The exposure duration can be set.

In this mode, you can set the exposure duration by calling [ManualExposure.setExposureDuration](../../../reference/apis-camera-kit/arkts-apis-camera-ManualExposure.md#setexposureduration24).

**Since:** 24

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core
