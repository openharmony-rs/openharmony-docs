# USBInterface

一个[USBConfiguration](arkts-basicservices-usbmanager-usbconfiguration-i.md)中可以含有多个USBInterface，每个USBInterface提供一个功能。

**起始版本：** 9

<!--Device-usbManager-interface USBInterface--><!--Device-usbManager-interface USBInterface-End-->

**系统能力：** SystemCapability.USB.USBManager

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## alternateSetting

```TypeScript
alternateSetting: number
```

在同一个接口中的多个描述符中进行切换设置。值的大小表示支持可选模式个数，其中0表示不支持可选模式。

**类型：** number

**起始版本：** 9

<!--Device-USBInterface-alternateSetting: int--><!--Device-USBInterface-alternateSetting: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## clazz

```TypeScript
clazz: number
```

设备类型。

**类型：** number

**起始版本：** 9

<!--Device-USBInterface-clazz: int--><!--Device-USBInterface-clazz: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## endpoints

```TypeScript
endpoints: Array<USBEndpoint>
```

当前接口所包含的端点。

**类型：** Array<USBEndpoint>

**起始版本：** 9

<!--Device-USBInterface-endpoints: Array<USBEndpoint>--><!--Device-USBInterface-endpoints: Array<USBEndpoint>-End-->

**系统能力：** SystemCapability.USB.USBManager

## id

```TypeScript
id: number
```

接口的唯一标识。

**类型：** number

**起始版本：** 9

<!--Device-USBInterface-id: int--><!--Device-USBInterface-id: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## name

```TypeScript
name: string
```

接口名称。

**类型：** string

**起始版本：** 9

<!--Device-USBInterface-name: string--><!--Device-USBInterface-name: string-End-->

**系统能力：** SystemCapability.USB.USBManager

## protocol

```TypeScript
protocol: number
```

接口的协议。

**类型：** number

**起始版本：** 9

<!--Device-USBInterface-protocol: int--><!--Device-USBInterface-protocol: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## subClass

```TypeScript
subClass: number
```

设备子类。

**类型：** number

**起始版本：** 9

<!--Device-USBInterface-subClass: int--><!--Device-USBInterface-subClass: int-End-->

**系统能力：** SystemCapability.USB.USBManager

