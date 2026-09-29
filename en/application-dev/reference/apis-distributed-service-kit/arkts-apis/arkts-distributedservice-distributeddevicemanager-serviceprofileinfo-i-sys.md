# ServiceProfileInfo (System API)

```TypeScript
interface ServiceProfileInfo
```

Defines the service profile information. It is populated based on the data returned from the cloud.

**Since:** 15

<!--Device-distributedDeviceManager-interface ServiceProfileInfo--><!--Device-distributedDeviceManager-interface ServiceProfileInfo-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
```

## data

```TypeScript
data?: string
```

Service data. The value is a string of up to 1000 characters. This parameter is left unspecified by default.

**Type:** string

**Since:** 15

<!--Device-ServiceProfileInfo-data?: string--><!--Device-ServiceProfileInfo-data?: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## deviceId

```TypeScript
deviceId: string
```

Device ID.

**Type:** string

**Since:** 15

<!--Device-ServiceProfileInfo-deviceId: string--><!--Device-ServiceProfileInfo-deviceId: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## serviceId

```TypeScript
serviceId: string
```

Service ID.

**Type:** string

**Since:** 15

<!--Device-ServiceProfileInfo-serviceId: string--><!--Device-ServiceProfileInfo-serviceId: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## serviceType

```TypeScript
serviceType: string
```

Service type.

**Type:** string

**Since:** 15

<!--Device-ServiceProfileInfo-serviceType: string--><!--Device-ServiceProfileInfo-serviceType: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.
