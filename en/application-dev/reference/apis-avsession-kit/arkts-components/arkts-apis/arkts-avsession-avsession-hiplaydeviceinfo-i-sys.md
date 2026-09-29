# HiPlayDeviceInfo (System API)

```TypeScript
interface HiPlayDeviceInfo
```

HiPlay Device Information Definition

**Since:** 24

<!--Device-avSession-interface HiPlayDeviceInfo--><!--Device-avSession-interface HiPlayDeviceInfo-End-->

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

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-HiPlayDeviceInfo-castMode?: int--><!--Device-HiPlayDeviceInfo-castMode?: int-End-->

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

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-HiPlayDeviceInfo-castUid?: int--><!--Device-HiPlayDeviceInfo-castUid?: int-End-->

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

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-HiPlayDeviceInfo-supportCastMode?: int--><!--Device-HiPlayDeviceInfo-supportCastMode?: int-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.
