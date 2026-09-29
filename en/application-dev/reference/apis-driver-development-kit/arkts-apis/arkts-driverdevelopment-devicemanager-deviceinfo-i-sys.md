# DeviceInfo (System API)

```TypeScript
interface DeviceInfo
```

Defines the detailed information about a device.

**Since:** 12

<!--Device-deviceManager-interface DeviceInfo--><!--Device-deviceManager-interface DeviceInfo-End-->

**System capability:** SystemCapability.Driver.ExternalDevice

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
```

## deviceId

```TypeScript
deviceId: number
```

Device ID.

**Type:** number

**Since:** 12

<!--Device-DeviceInfo-deviceId: long--><!--Device-DeviceInfo-deviceId: long-End-->

**System capability:** SystemCapability.Driver.ExternalDevice

**System API:** This is a system API.

## driverUid

```TypeScript
driverUid?: string
```

UID of the driver matching the device.

**Type:** string

**Since:** 12

<!--Device-DeviceInfo-driverUid?: string--><!--Device-DeviceInfo-driverUid?: string-End-->

**System capability:** SystemCapability.Driver.ExternalDevice

**System API:** This is a system API.

## isDriverMatched

```TypeScript
isDriverMatched: boolean
```

Whether the device matches the driver. The value `true` indicates the device matches the driver, and the value `false` indicates the opposite.

**Type:** boolean

**Since:** 12

<!--Device-DeviceInfo-isDriverMatched: boolean--><!--Device-DeviceInfo-isDriverMatched: boolean-End-->

**System capability:** SystemCapability.Driver.ExternalDevice

**System API:** This is a system API.
