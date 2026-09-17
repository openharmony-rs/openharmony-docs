# DeviceInfo (System API)

Defines the detailed information about a device.

**Since:** 12

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

**System capability:** SystemCapability.Driver.ExternalDevice

**System API:** This is a system API.

## driverUid

```TypeScript
driverUid?: string
```

UID of the driver matching the device.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Driver.ExternalDevice

**System API:** This is a system API.

## isDriverMatched

```TypeScript
isDriverMatched: boolean
```

Whether the device matches the driver. The value `true` indicates the device matches the driver, and the value `false` indicates the opposite.

**Type:** boolean

**Since:** 12

**System capability:** SystemCapability.Driver.ExternalDevice

**System API:** This is a system API.
