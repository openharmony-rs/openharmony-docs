# DoorPositionResponse (System API)

```TypeScript
export interface DoorPositionResponse
```

Interface for indoor or outdoor identify result @interface DoorPositionResponse

**Since:** 23

<!--Device-spatialAwareness-export interface DoorPositionResponse--><!--Device-spatialAwareness-export interface DoorPositionResponse-End-->

**System capability:** SystemCapability.MultimodalAwareness.DistanceMeasurement

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { spatialAwareness } from '@kit.MultimodalAwarenessKit';
```

## deviceId

```TypeScript
deviceId: string
```

indicates the ID of the remote ranging device

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DoorPositionResponse-deviceId: string--><!--Device-DoorPositionResponse-deviceId: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.DistanceMeasurement

**System API:** This is a system API.

## doorLockCode

```TypeScript
doorLockCode: number
```

indicates random code for unlocking the door

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DoorPositionResponse-doorLockCode: int--><!--Device-DoorPositionResponse-doorLockCode: int-End-->

**System capability:** SystemCapability.MultimodalAwareness.DistanceMeasurement

**System API:** This is a system API.

## position

```TypeScript
position: PositionRelativeToDoor
```

indicates result inside and outside the door

**Type:** [PositionRelativeToDoor](arkts-multimodalawareness-spatialawareness-positionrelativetodoor-e-sys.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DoorPositionResponse-position: PositionRelativeToDoor--><!--Device-DoorPositionResponse-position: PositionRelativeToDoor-End-->

**System capability:** SystemCapability.MultimodalAwareness.DistanceMeasurement

**System API:** This is a system API.
