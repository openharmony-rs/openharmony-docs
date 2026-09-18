# USBControlRequestType

Enumerates control request types. Each type indicates a specific USB control request command such as obtaining the descriptor or setting the address.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## USB_REQUEST_TYPE_STANDARD

```TypeScript
USB_REQUEST_TYPE_STANDARD = 0
```

Standard request type, which is used to send standard control requests (such as the device descriptor, setting address, and setting configuration) defined by the USB protocol.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## USB_REQUEST_TYPE_CLASS

```TypeScript
USB_REQUEST_TYPE_CLASS = 1
```

Class request type, which is used to send class-specific control requests (such as HID and mass storage class requests).

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## USB_REQUEST_TYPE_VENDOR

```TypeScript
USB_REQUEST_TYPE_VENDOR = 2
```

Vendor request type, which is used to send vendor-defined control requests. The request content is defined by the vendor.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager
