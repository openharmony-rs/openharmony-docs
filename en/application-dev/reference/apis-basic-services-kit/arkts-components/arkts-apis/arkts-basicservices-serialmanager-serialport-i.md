# SerialPort

Represents the parameters of a serial port.

**Since:** 19

**System capability:** SystemCapability.USB.USBManager.Serial

## Modules to Import

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## deviceName

```TypeScript
deviceName: string
```

Name of a serial port device, which is used to display and identify a specific serial port device. It can be used to display device information on the UI, helping users distinguish between different serial port devices.

**Type:** string

**Since:** 19

**System capability:** SystemCapability.USB.USBManager.Serial

## portId

```TypeScript
portId: number
```

Serial port number, which uniquely identifies a serial port device. The value is obtained from the **SerialPort** object returned by **getPortList** and is used to specify the serial port device to be operated.

**Type:** number

**Since:** 19

**System capability:** SystemCapability.USB.USBManager.Serial
