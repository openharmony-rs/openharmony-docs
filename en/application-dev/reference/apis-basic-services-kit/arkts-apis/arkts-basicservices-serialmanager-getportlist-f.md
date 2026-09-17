# getPortList

## Modules to Import

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## getPortList

```TypeScript
function getPortList(): Readonly<SerialPort>[]
```

Obtains the serial port device list, including the device name and port number. Generally, this API is called when the application is started, a device is connected, or available serial port devices need to be detected.

**Since:** 19

**System capability:** SystemCapability.USB.USBManager.Serial

**Return value:**

| Type | Description |
| --- | --- |
| Readonly&lt;[SerialPort](arkts-basicservices-serialmanager-serialport-i.md)&gt;[] | List of available serial port devices. Each element contains attributes such as the port number and device name of the serial port. This parameter can be used to obtain all serial port devices in the system, and users can choose one to operate. |

**Examples**

```TypeScript
> NOTE
> 
> The following sample code shows the basic process for calling the getPortList API and it needs to be executed in a specific method. In actual calling, you must comply with the device-related protocols.
```
