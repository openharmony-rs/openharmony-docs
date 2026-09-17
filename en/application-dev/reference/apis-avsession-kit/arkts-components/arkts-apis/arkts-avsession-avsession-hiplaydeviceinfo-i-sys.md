# HiPlayDeviceInfo (System API)

HiPlay Device Information Definition

**Since:** 24

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## castMode

```TypeScript
castMode?: number
```

HiPlay device cast mode. 1: DEVICE_LEVEL_CAST 2: APP_LEVEL_CAST

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

## castUid

```TypeScript
castUid?: number
```

HiPlay device current cast uid.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

## supportCastMode

```TypeScript
supportCastMode?: number
```

HiPlay device supports cast mode. when device both support device level cast and app level cast, support cast mode is DEVICE_LEVEL_CAST| APP_LEVEL_CAST 1: DEVICE_LEVEL_CAST 2: APP_LEVEL_CAST

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.
