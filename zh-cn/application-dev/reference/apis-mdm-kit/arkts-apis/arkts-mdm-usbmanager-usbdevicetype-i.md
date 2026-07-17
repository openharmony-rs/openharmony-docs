# UsbDeviceType

USB设备类型信息。

**起始版本：** 14

<!--Device-usbManager-export interface UsbDeviceType--><!--Device-usbManager-export interface UsbDeviceType-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { usbManager } from '@kit.MDMKit';
```

## baseClass

```TypeScript
baseClass: number
```

类型编码。

可通过[getDevices](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-usbmanager-getdevices-f.md#getdevices-1)接口获取已接入主设备的USB设备列表，需在返回值列表中查找当前设备，查看其值。

先根据此值确定descriptor应该传入的类型。若descriptor为DEVICE，则本字段取USBDevice.clazz字段值，若descriptor为INTERFACE，则本字段取USBDevice.configs.interfaces.clazz字段值。

若字段值为255，表示此设备的类型编码是厂商自定义编码，则使用[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#adddisallowedusbdevices-1)/[removeDisallowedUsbDevices](arkts-mdm-usbmanager-removedisallowedusbdevices-f.md#removedisallowedusbdevices-1)接口禁用/解禁该设备不生效；若字段值未在[defined-class-codes](https://www.usb.org/defined-class-codes)中定义，则使用[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#adddisallowedusbdevices-1)/[removeDisallowedUsbDevices](arkts-mdm-usbmanager-removedisallowedusbdevices-f.md#removedisallowedusbdevices-1)接口禁用/解禁该设备不生效。

**类型：** number

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UsbDeviceType-baseClass: number--><!--Device-UsbDeviceType-baseClass: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## descriptor

```TypeScript
descriptor: Descriptor
```

USB描述符。

可通过[getDevices](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-usbmanager-getdevices-f.md#getdevices-1)接口获取已接入主设备的USB设备列表，需在返回值列表中查找当前设备，查看其值。

若此值USBDevice.clazz字段值为0，则须在[defined-class-codes](https://www.usb.org/defined-class-codes)中的Base Class列查找此值USBDevice.configs.interfaces.clazz字段值，查找结果所在行所对应的Descriptor Usage列就表示当前应该传入的descriptor类型（若Descriptor Usage列为Both，表示两种类型都可以传入，需要设备级禁用时传入DEVICE，需要接口级禁用时传入INTERFACE）;

若此值USBDevice.clazz字段值为255，表示此设备的类型编码是厂商自定义编码，则使用[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#adddisallowedusbdevices-1)/[removeDisallowedUsbDevices](arkts-mdm-usbmanager-removedisallowedusbdevices-f.md#removedisallowedusbdevices-1)接口禁用/解禁该设备不生效；若此值USBDevice.clazz字段值为其他值，则须在[defined-class-codes](https://www.usb.org/defined-class-codes)中的Base Class列查找该值，查找结果所在行所对应的Descriptor Usage列就表示当前应该传入的descriptor类型（若Descriptor Usage列为Both，表示两种类型都可以传入，需要设备级禁用时传入DEVICE，需要接口级禁用时传入INTERFACE）。

**类型：** Descriptor

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UsbDeviceType-descriptor: Descriptor--><!--Device-UsbDeviceType-descriptor: Descriptor-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## protocol

```TypeScript
protocol: number
```

协议编码。

可通过[getDevices](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-usbmanager-getdevices-f.md#getdevices-1)接口获取已接入主设备的USB设备列表，需在返回值列表中查找当前设备，查看其值。

先根据baseClass的值确定descriptor应该传入的类型。若descriptor为DEVICE，则本字段取USBDevice.protocol字段值，若descriptor为INTERFACE，则本字段取USBDevice.configs.interfaces.protocol字段值。

若字段值为255，表示此设备的协议编码是厂商自定义编码，则使用[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#adddisallowedusbdevices-1)/[removeDisallowedUsbDevices](arkts-mdm-usbmanager-removedisallowedusbdevices-f.md#removedisallowedusbdevices-1)接口禁用/解禁该设备不生效；若字段值未在[defined-class-codes](https://www.usb.org/defined-class-codes)中定义，则使用[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#adddisallowedusbdevices-1)/[removeDisallowedUsbDevices](arkts-mdm-usbmanager-removedisallowedusbdevices-f.md#removedisallowedusbdevices-1)接口禁用/解禁该设备不生效。

**类型：** number

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UsbDeviceType-protocol: number--><!--Device-UsbDeviceType-protocol: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## subClass

```TypeScript
subClass: number
```

子类型编码。

可通过[getDevices](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-usbmanager-getdevices-f.md#getdevices-1)接口获取已接入主设备的USB设备列表，需在返回值列表中查找当前设备，查看其值。

先根据baseClass的值确定descriptor应该传入的类型。若descriptor为DEVICE，则本字段取USBDevice.subClass字段值，若descriptor为INTERFACE，则本字段取USBDevice.configs.interfaces.subClass字段值。

若字段值为255，表示此设备的子类型编码是厂商自定义编码，则使用[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#adddisallowedusbdevices-1)/[removeDisallowedUsbDevices](arkts-mdm-usbmanager-removedisallowedusbdevices-f.md#removedisallowedusbdevices-1)接口禁用/解禁该设备不生效；若字段值未在[defined-class-codes](https://www.usb.org/defined-class-codes)中定义，则使用[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#adddisallowedusbdevices-1)/[removeDisallowedUsbDevices](arkts-mdm-usbmanager-removedisallowedusbdevices-f.md#removedisallowedusbdevices-1)接口禁用/解禁该设备不生效。

**类型：** number

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UsbDeviceType-subClass: number--><!--Device-UsbDeviceType-subClass: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

