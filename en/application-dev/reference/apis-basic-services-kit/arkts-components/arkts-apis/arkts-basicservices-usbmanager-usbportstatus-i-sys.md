# USBPortStatus (System API)

```TypeScript
interface USBPortStatus
```

Enumerates USB port roles. **currentMode** indicates the current USB mode of the port. The value must be within the range of **supportedModes** of the USB port. **currentPowerRole** indicates the current power role, and **currentDataRole** indicates the current data transfer role. These fields are generally set as follows: In DFP mode, **dataRole** is **HOST**, and **powerRole** is **SOURCE**. In UFP mode, **dataRole** is **DEVICE**, and **powerRole** is **SINK**. The port status change is subject to hardware and system constraints. Some mode or role combinations may not be supported.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## currentDataRole

```TypeScript
currentDataRole: number
```

Current data transfer role of the device. For details, see [DataRoleType](arkts-basicservices-usbmanager-dataroletype-e-sys.md).

**Type:** number

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

## currentMode

```TypeScript
currentMode: number
```

Current USB mode. For details, see [PortModeType](arkts-basicservices-usbmanager-portmodetype-e-sys.md).

**Type:** number

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

## currentPowerRole

```TypeScript
currentPowerRole: number
```

Current power role of the device. For details, see [PowerRoleType](arkts-basicservices-usbmanager-powerroletype-e-sys.md).

**Type:** number

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.
