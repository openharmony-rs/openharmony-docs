# USBRequestTargetType

Enumerates request target types.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## USB_REQUEST_TARGET_DEVICE

```TypeScript
USB_REQUEST_TARGET_DEVICE = 0
```

The control request target is set to the USB device, which is used to control the entire device, for example, setting the device address or obtaining the device descriptor.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## USB_REQUEST_TARGET_INTERFACE

```TypeScript
USB_REQUEST_TARGET_INTERFACE = 1
```

The control request target is set to an interface of the USB device, which is used to control the interface, for example, setting the interface features or obtaining the interface descriptor.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## USB_REQUEST_TARGET_ENDPOINT

```TypeScript
USB_REQUEST_TARGET_ENDPOINT = 2
```

The control request target is set to an endpoint of the USB device, which is used to control the endpoint, for example, clearing the endpoint stop state or obtaining the endpoint status.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## USB_REQUEST_TARGET_OTHER

```TypeScript
USB_REQUEST_TARGET_OTHER = 3
```

The control request target is set to another unit, which is used to control the unit of a non-standard device, interface, or endpoint.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager
