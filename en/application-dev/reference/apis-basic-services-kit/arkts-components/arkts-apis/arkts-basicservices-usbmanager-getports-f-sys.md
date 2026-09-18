# getPorts (System API)

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## getPorts

```TypeScript
function getPorts(): Array<USBPort>
```

Obtains the list of all physical USB ports. This API can be used to enumerate USB ports, perform port management, diagnose the device connection status, or query the port configuration information. When the developer mode is disabled, **undefined** is returned if no device is connected. Check whether the return value of the API is empty.

**Since:** 9

**Deprecated since:** 12

**Substitutes:** [getPortList](arkts-basicservices-usbmanager-getportlist-f-sys.md)()

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[USBPort](arkts-basicservices-usbmanager-usbport-i-sys.md)&gt; | List of physical USB ports. |
