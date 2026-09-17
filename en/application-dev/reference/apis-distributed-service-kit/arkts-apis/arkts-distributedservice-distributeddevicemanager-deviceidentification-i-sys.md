# DeviceIdentification (System API)

Struct for distributed device identification.

@interface DeviceIdentification

**Since:** 24

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

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.
