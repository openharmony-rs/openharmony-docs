# USBPort (System API)

```TypeScript
interface USBPort
```

Represents a USB port.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## id

```TypeScript
id: number
```

Unique identifier of a USB port.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

## status

```TypeScript
status: USBPortStatus
```

USB port role information. **currentMode** must be within the range of **supportedModes**.

**Type:** [USBPortStatus](arkts-basicservices-usbmanager-usbportstatus-i-sys.md)

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

## supportedModes

```TypeScript
supportedModes: PortModeType
```

Numeric mask combination for the supported mode list. **status.currentMode** must be supported.

**Type:** [PortModeType](arkts-basicservices-usbmanager-portmodetype-e-sys.md)

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.
