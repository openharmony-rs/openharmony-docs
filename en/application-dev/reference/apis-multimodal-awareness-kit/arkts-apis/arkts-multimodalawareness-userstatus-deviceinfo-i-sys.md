# DeviceInfo (System API)

```TypeScript
export interface DeviceInfo
```

Defines device information.

**Since:** 26.0.0

<!--Device-userStatus-export interface DeviceInfo--><!--Device-userStatus-export interface DeviceInfo-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## deviceId

```TypeScript
deviceId: string
```

Device ID. A unique device identifier used to identify and distinguish different devices. The string length ranges from 0 to 64.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceInfo-deviceId: string--><!--Device-DeviceInfo-deviceId: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## deviceName

```TypeScript
deviceName: string
```

Device name. A user-defined device display name used to show device information in the UI. The string length ranges from 0 to 64.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceInfo-deviceName: string--><!--Device-DeviceInfo-deviceName: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## deviceType

```TypeScript
deviceType: DeviceType
```

Device type.

**Type:** [DeviceType](arkts-multimodalawareness-userstatus-devicetype-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceInfo-deviceType: DeviceType--><!--Device-DeviceInfo-deviceType: DeviceType-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## networkId

```TypeScript
networkId: string
```

Device network ID. A unique network identifier used for device networking and cross-device communication. The string length ranges from 0 to 64.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceInfo-networkId: string--><!--Device-DeviceInfo-networkId: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.
