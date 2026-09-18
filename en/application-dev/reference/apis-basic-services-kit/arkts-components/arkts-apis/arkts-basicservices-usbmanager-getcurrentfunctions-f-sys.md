# getCurrentFunctions (System API)

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## getCurrentFunctions

```TypeScript
function getCurrentFunctions(): FunctionType
```

Obtains the numeric mask combination for the USB function list in Device mode. This API can be used to check the USB function state, confirm the function configuration, or compare the status before and after function switching. When the developer mode is disabled, **undefined** is returned if no device is connected. Check whether the return value of the API is empty.

**Since:** 9

**Deprecated since:** 12

**Substitutes:** [getDeviceFunctions](arkts-basicservices-usbmanager-getdevicefunctions-f-sys.md)()

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [FunctionType](arkts-basicservices-usbmanager-functiontype-e-sys.md) | Numeric mask combination for the USB function list. When the developer mode is disabled and no device is connected, **undefined** is returned. Check whether the return value is empty. |
