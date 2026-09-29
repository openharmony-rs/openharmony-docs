# DeviceBasicInfo

```TypeScript
interface DeviceBasicInfo
```

Represents the basic information about a distributed device.

**Since:** 10

<!--Device-distributedDeviceManager-interface DeviceBasicInfo--><!--Device-distributedDeviceManager-interface DeviceBasicInfo-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

## Modules to Import

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
```

## deviceId

```TypeScript
deviceId: string
```

Device ID. The value is the result of obfuscating the udid-hash (hash value of the UDID), **appid**, and salt using the SHA-256 algorithm.

**Type:** string

**Since:** 10

<!--Device-DeviceBasicInfo-deviceId: string--><!--Device-DeviceBasicInfo-deviceId: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

## deviceName

```TypeScript
deviceName: string
```

Device name.

**Type:** string

**Since:** 10

<!--Device-DeviceBasicInfo-deviceName: string--><!--Device-DeviceBasicInfo-deviceName: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

## deviceType

```TypeScript
deviceType: string
```

[Device type](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getdevicetype).

**Type:** string

**Since:** 10

<!--Device-DeviceBasicInfo-deviceType: string--><!--Device-DeviceBasicInfo-deviceType: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

## networkId

```TypeScript
networkId?: string
```

Network ID of the device.

**Type:** string

**Since:** 10

<!--Device-DeviceBasicInfo-networkId?: string--><!--Device-DeviceBasicInfo-networkId?: string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager
