# USBConfig

USB配置，一个[USBDevice](arkts-basicservices-usb-usbdevice-i.md)中可以含有多个配置。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [USBConfiguration](arkts-basicservices-usbmanager-usbconfiguration-i.md)

<!--Device-usb-interface USBConfig--><!--Device-usb-interface USBConfig-End-->

**系统能力：** SystemCapability.USB.USBManager

## 导入模块

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## attributes

```TypeScript
attributes: number
```

配置的属性。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [attributes](arkts-basicservices-usbmanager-usbconfiguration-i.md#attributes)

<!--Device-USBConfig-attributes: number--><!--Device-USBConfig-attributes: number-End-->

**系统能力：** SystemCapability.USB.USBManager

## id

```TypeScript
id: number
```

配置的唯一标识。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [id](arkts-basicservices-usbmanager-usbconfiguration-i.md#id)

<!--Device-USBConfig-id: number--><!--Device-USBConfig-id: number-End-->

**系统能力：** SystemCapability.USB.USBManager

## interfaces

```TypeScript
interfaces: Array<USBInterface>
```

配置支持的接口属性。

**类型：** Array<USBInterface>

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [interfaces](arkts-basicservices-usbmanager-usbconfiguration-i.md#interfaces)

<!--Device-USBConfig-interfaces: Array<USBInterface>--><!--Device-USBConfig-interfaces: Array<USBInterface>-End-->

**系统能力：** SystemCapability.USB.USBManager

## isRemoteWakeup

```TypeScript
isRemoteWakeup: boolean
```

检查当前配置是否支持远程唤醒。

**类型：** boolean

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isRemoteWakeup](arkts-basicservices-usbmanager-usbconfiguration-i.md#isremotewakeup)

<!--Device-USBConfig-isRemoteWakeup: boolean--><!--Device-USBConfig-isRemoteWakeup: boolean-End-->

**系统能力：** SystemCapability.USB.USBManager

## isSelfPowered

```TypeScript
isSelfPowered: boolean
```

检查当前配置是否支持独立电源。

**类型：** boolean

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isSelfPowered](arkts-basicservices-usbmanager-usbconfiguration-i.md#isselfpowered)

<!--Device-USBConfig-isSelfPowered: boolean--><!--Device-USBConfig-isSelfPowered: boolean-End-->

**系统能力：** SystemCapability.USB.USBManager

## maxPower

```TypeScript
maxPower: number
```

最大功耗，以毫安为单位。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [maxPower](arkts-basicservices-usbmanager-usbconfiguration-i.md#maxpower)

<!--Device-USBConfig-maxPower: number--><!--Device-USBConfig-maxPower: number-End-->

**系统能力：** SystemCapability.USB.USBManager

## name

```TypeScript
name: string
```

配置的名称，可以为空。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [name](arkts-basicservices-usbmanager-usbconfiguration-i.md#name)

<!--Device-USBConfig-name: string--><!--Device-USBConfig-name: string-End-->

**系统能力：** SystemCapability.USB.USBManager

