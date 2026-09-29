# DeviceIdentification (System API)

```TypeScript
interface DeviceIdentification
```

Struct for distributed device identification.

@interface DeviceIdentification

**Since:** 24

<!--Device-distributedDeviceManager-interface DeviceIdentification--><!--Device-distributedDeviceManager-interface DeviceIdentification-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
```

## deviceId

```TypeScript
deviceId: string
```

Anonymized device ID for application.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceIdentification-deviceId: string--><!--Device-DeviceIdentification-deviceId: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## udid

```TypeScript
udid: string
```

Unique device ID (UDID).

**Type:** string

**Since:** 24

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC and ohos.permission.ACCESS_SERVICE_DM and ohos.permission.sec.ACCESS_UDID

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceIdentification-udid: string--><!--Device-DeviceIdentification-udid: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.
