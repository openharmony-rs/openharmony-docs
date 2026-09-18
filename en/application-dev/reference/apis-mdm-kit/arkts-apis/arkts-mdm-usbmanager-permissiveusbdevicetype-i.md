# PermissiveUsbDeviceType

USB device type information. Partial field matching is supported.

- Compared with [UsbDeviceType](arkts-mdm-usbmanager-usbdevicetype-i.md), the **subClass**, **protocol**, and **descriptor**  
parameters in this API are optional, allowing for more flexible USB device disabling policies.  
- Only the matching based on the **baseClass** parameter is supported.  
- Multiple parameters can be configured. All parameters must be satisfied simultaneously for a match.  
- You can obtain the list of USB devices connected to the host device through the [getDevices](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-usbmanager-getdevices-f.md) API, and then find the type of the current device in the returned list.

**Since:** 26.0.0

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { usbManager } from '@kit.MDMKit';
```

## baseClass

```TypeScript
baseClass: number
```

Type code. The value range is [0, 255]. If **descriptor** is **DEVICE**, this parameter takes the value of the **USBDevice.clazz** parameter; if **descriptor** is **INTERFACE**, this parameter takes the value of the **USBDevice.configs.interfaces.clazz** parameter.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## descriptor

```TypeScript
descriptor?: Descriptor
```

USB descriptor. If **USBDevice.clazz** is **0**, locate the value of **USBDevice.configs.interfaces.clazz** in the **Base Class** column of the [defined-class-codes](https://www.usb.org/defined-class-codes) table. The **Descriptor Usage** column of the corresponding row indicates the descriptor type to be passed. (If **Descriptor Usage** is **Both**, either type can be passed. You can pass **DEVICE** for device-level disabling, or **INTERFACE** for interface- level disabling.) If **USBDevice.clazz** is other than **0**, locate that value in the **Base Class** column of the [defined-class-codes](https://www.usb.org/defined-class-codes) table. The **Descriptor Usage** column of the corresponding row indicates the descriptor type to be passed. (If **Descriptor Usage** is **Both**, either type can be passed. Pass **DEVICE** for device-level disabling, or **INTERFACE** for interface-level disabling.).

**Type:** [Descriptor](arkts-mdm-usbmanager-descriptor-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## protocol

```TypeScript
protocol?: number
```

Protocol code. The value range is [0, 255]. If **descriptor** is **DEVICE**, this parameter takes the value of the **USBDevice.protocol** parameter; if **descriptor** is **INTERFACE**, this parameter takes the value of the **USBDevice.configs.interfaces.protocol** parameter.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## subClass

```TypeScript
subClass?: number
```

Subtype code. The value range is [0, 255]. If **descriptor** is **DEVICE**, this parameter takes the value of the **USBDevice.subClass** parameter; if **descriptor** is **INTERFACE**, this parameter takes the value of the **USBDevice.configs.interfaces.subClass** parameter.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
