# InterfaceConflictInfo

```TypeScript
interface InterfaceConflictInfo
```

Describes the conflict information when the USB interface that has been exclusively claimed is claimed by another process in non-exclusive mode by calling [usbManager.claimInterfaceExclusive](arkts-basicservices-usbmanager-claiminterfaceexclusive-f.md).

> **NOTE:** 
> 
> This callback is triggered when another process calls
> [usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md) non-exclusively to claim the same USB interface. The exclusive holder of the interface can learn about potential access conflicts through this callback.

**Since:** 26.0.1

**System capability:** SystemCapability.USB.USBManager

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## busNum

```TypeScript
busNum: number
```

Bus address of the USB device. The value should be an integer.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.USB.USBManager

## devAddr

```TypeScript
devAddr: number
```

Device address of the USB device.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.USB.USBManager

## interfaceId

```TypeScript
interfaceId: number
```

ID of the USB interface that has been claimed by another process.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.USB.USBManager
