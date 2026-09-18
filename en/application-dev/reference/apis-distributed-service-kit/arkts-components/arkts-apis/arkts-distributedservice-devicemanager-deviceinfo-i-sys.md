# DeviceInfo (System API)

Defines device information.

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [DeviceBasicInfo](arkts-distributedservice-distributeddevicemanager-devicebasicinfo-i.md)

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { deviceManager } from '@kit.DistributedServiceKit';
```

## authForm

```TypeScript
authForm: AuthForm
```

Authentication type of the device.

**Type:** [AuthForm](arkts-distributedservice-devicemanager-authform-e-sys.md)

**Since:** 10

**Deprecated since:** 11

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## deviceId

```TypeScript
deviceId: string
```

Unique identifier of the device.

**Type:** string

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [deviceId](arkts-distributedservice-distributeddevicemanager-devicebasicinfo-i.md#deviceid)

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## deviceName

```TypeScript
deviceName: string
```

Device name.

**Type:** string

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [deviceName](arkts-distributedservice-distributeddevicemanager-devicebasicinfo-i.md#devicename)

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## deviceType

```TypeScript
deviceType: DeviceType
```

Device type.

**Type:** [DeviceType](arkts-distributedservice-devicemanager-devicetype-e-sys.md)

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [deviceType](arkts-distributedservice-distributeddevicemanager-devicebasicinfo-i.md#devicetype)

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## networkId

```TypeScript
networkId: string
```

Network ID of the device.

**Type:** string

**Since:** 8

**Deprecated since:** 11

**Substitutes:** [networkId](arkts-distributedservice-distributeddevicemanager-devicebasicinfo-i.md#networkid)

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## range

```TypeScript
range: number
```

Distance between the discovered device and the device that initiates device discovery.

**Type:** number

**Since:** 9

**Deprecated since:** 11

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.
