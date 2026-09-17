# USBControlParams

Control transfer parameters.

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [USBDeviceRequestParams](arkts-basicservices-usbmanager-usbdevicerequestparams-i.md)

**System capability:** SystemCapability.USB.USBManager

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## data

```TypeScript
data: Uint8Array
```

Buffer for writing or reading data.

**Type:** Uint8Array

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [USBDeviceRequestParams](arkts-basicservices-usbmanager-usbdevicerequestparams-i.md)

**System capability:** SystemCapability.USB.USBManager

## index

```TypeScript
index: number
```

Index value corresponding to the request parameter **value**, which is used to specify the target interface or endpoint of the control request.

**Type:** number

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [USBDeviceRequestParams](arkts-basicservices-usbmanager-usbdevicerequestparams-i.md)

**System capability:** SystemCapability.USB.USBManager

## reqType

```TypeScript
reqType: USBControlRequestType
```

Request control type.

**Type:** [USBControlRequestType](arkts-basicservices-usbmanager-usbcontrolrequesttype-e.md)

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [USBDeviceRequestParams](arkts-basicservices-usbmanager-usbdevicerequestparams-i.md)

**System capability:** SystemCapability.USB.USBManager

## request

```TypeScript
request: number
```

Request type, which indicates a specific USB control request command.

**Type:** number

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [USBDeviceRequestParams](arkts-basicservices-usbmanager-usbdevicerequestparams-i.md)

**System capability:** SystemCapability.USB.USBManager

## target

```TypeScript
target: USBRequestTargetType
```

Request target type.

**Type:** [USBRequestTargetType](arkts-basicservices-usbmanager-usbrequesttargettype-e.md)

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [USBDeviceRequestParams](arkts-basicservices-usbmanager-usbdevicerequestparams-i.md)

**System capability:** SystemCapability.USB.USBManager

## value

```TypeScript
value: number
```

Request parameter, which is used to transfer the parameters required by the control request to the USB device.

**Type:** number

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [USBDeviceRequestParams](arkts-basicservices-usbmanager-usbdevicerequestparams-i.md)

**System capability:** SystemCapability.USB.USBManager
