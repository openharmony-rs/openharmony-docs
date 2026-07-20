# USBInterface

一个[USBConfig](arkts-basicservices-usb-usbconfig-i.md)中可以含有多个USBInterface，每个USBInterface提供一个功能。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [USBInterface](arkts-basicservices-usbmanager-usbinterface-i.md)

<!--Device-usb-interface USBInterface--><!--Device-usb-interface USBInterface-End-->

**系统能力：** SystemCapability.USB.USBManager

## 导入模块

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## alternateSetting

```TypeScript
alternateSetting: number
```

在同一个接口中的多个描述符中进行切换设置。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [alternateSetting](arkts-basicservices-usbmanager-usbinterface-i.md#alternatesetting)

<!--Device-USBInterface-alternateSetting: number--><!--Device-USBInterface-alternateSetting: number-End-->

**系统能力：** SystemCapability.USB.USBManager

## clazz

```TypeScript
clazz: number
```

设备类型。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [clazz](arkts-basicservices-usbmanager-usbinterface-i.md#clazz)

<!--Device-USBInterface-clazz: number--><!--Device-USBInterface-clazz: number-End-->

**系统能力：** SystemCapability.USB.USBManager

## endpoints

```TypeScript
endpoints: Array<USBEndpoint>
```

当前接口所包含的端点。

**类型：** Array&lt;USBEndpoint&gt;

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [endpoints](arkts-basicservices-usbmanager-usbinterface-i.md#endpoints)

<!--Device-USBInterface-endpoints: Array<USBEndpoint>--><!--Device-USBInterface-endpoints: Array<USBEndpoint>-End-->

**系统能力：** SystemCapability.USB.USBManager

## id

```TypeScript
id: number
```

接口的唯一标识。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [id](arkts-basicservices-usbmanager-usbinterface-i.md#id)

<!--Device-USBInterface-id: number--><!--Device-USBInterface-id: number-End-->

**系统能力：** SystemCapability.USB.USBManager

## name

```TypeScript
name: string
```

接口名称。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [name](arkts-basicservices-usbmanager-usbinterface-i.md#name)

<!--Device-USBInterface-name: string--><!--Device-USBInterface-name: string-End-->

**系统能力：** SystemCapability.USB.USBManager

## protocol

```TypeScript
protocol: number
```

接口的协议。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [protocol](arkts-basicservices-usbmanager-usbinterface-i.md#protocol)

<!--Device-USBInterface-protocol: number--><!--Device-USBInterface-protocol: number-End-->

**系统能力：** SystemCapability.USB.USBManager

## subClass

```TypeScript
subClass: number
```

设备子类。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [subClass](arkts-basicservices-usbmanager-usbinterface-i.md#subclass)

<!--Device-USBInterface-subClass: number--><!--Device-USBInterface-subClass: number-End-->

**系统能力：** SystemCapability.USB.USBManager

