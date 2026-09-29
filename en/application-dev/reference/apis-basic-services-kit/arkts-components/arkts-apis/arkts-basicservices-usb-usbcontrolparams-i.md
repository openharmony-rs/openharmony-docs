# USBControlParams

```TypeScript
interface USBControlParams
```

Represents control transfer parameters.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [USBControlParams](arkts-basicservices-usbmanager-usbcontrolparams-i.md)

<!--Device-usb-interface USBControlParams--><!--Device-usb-interface USBControlParams-End-->

**System capability:** SystemCapability.USB.USBManager

## Modules to Import

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## data

```TypeScript
data: Uint8Array
```

Buffer for writing or reading data.

**Type:** Uint8Array

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [data](arkts-basicservices-usbmanager-usbcontrolparams-i.md#data)

<!--Device-USBControlParams-data: Uint8Array--><!--Device-USBControlParams-data: Uint8Array-End-->

**System capability:** SystemCapability.USB.USBManager

## index

```TypeScript
index: number
```

Index of the request parameter value.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [index](arkts-basicservices-usbmanager-usbcontrolparams-i.md#index)

<!--Device-USBControlParams-index: number--><!--Device-USBControlParams-index: number-End-->

**System capability:** SystemCapability.USB.USBManager

## reqType

```TypeScript
reqType: USBControlRequestType
```

Control request type.

**Type:** [USBControlRequestType](arkts-basicservices-usb-usbcontrolrequesttype-e.md)

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [reqType](arkts-basicservices-usbmanager-usbcontrolparams-i.md#reqtype)

<!--Device-USBControlParams-reqType: USBControlRequestType--><!--Device-USBControlParams-reqType: USBControlRequestType-End-->

**System capability:** SystemCapability.USB.USBManager

## request

```TypeScript
request: number
```

Request type.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [request](arkts-basicservices-usbmanager-usbcontrolparams-i.md#request)

<!--Device-USBControlParams-request: number--><!--Device-USBControlParams-request: number-End-->

**System capability:** SystemCapability.USB.USBManager

## target

```TypeScript
target: USBRequestTargetType
```

Request target type.

**Type:** [USBRequestTargetType](arkts-basicservices-usb-usbrequesttargettype-e.md)

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [target](arkts-basicservices-usbmanager-usbcontrolparams-i.md#target)

<!--Device-USBControlParams-target: USBRequestTargetType--><!--Device-USBControlParams-target: USBRequestTargetType-End-->

**System capability:** SystemCapability.USB.USBManager

## value

```TypeScript
value: number
```

Request parameter value.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [value](arkts-basicservices-usbmanager-usbcontrolparams-i.md#value)

<!--Device-USBControlParams-value: number--><!--Device-USBControlParams-value: number-End-->

**System capability:** SystemCapability.USB.USBManager
