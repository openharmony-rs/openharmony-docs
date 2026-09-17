# DeviceNodeInfo (System API)

Defines the device node information, including the network ID, device name, device type ID, near-field status, and UDID.

**Since:** 26.1.0

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { conversation } from '@kit.DistributedServiceKit';
```

## deviceName

```TypeScript
deviceName: string
```

Device name.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.

## deviceTypeId

```TypeScript
deviceTypeId: number
```

Device type ID, which indicates the device type. The value is an integer, for example, **0x0E** is the mobile phone ID, **0x11** is the tablet ID, **0x9C** is the TV ID, and **0x0C** is the PC ID. The specific value is subject to the system definition.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.

## nearby

```TypeScript
nearby: boolean
```

Whether the device is in the near field. The value **true** indicates that the device is in the near field, and the value **false** indicates that the device is not in the near field.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.

## networkId

```TypeScript
networkId: string
```

Network ID of the device, which uniquely identifies a device on a distributed network and is used for device addressing during data sending. It is an alternative to UDID. Either of them can be used for data sending.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.

## udid

```TypeScript
udid: string
```

UDID of the device, which uniquely identifies a device and is used for device addressing during data sending. Different from the network ID, the UDID is a permanent and unique ID of a device and does not change with the network topology. They are alternative to each other and either of them can be used for data sending.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.
