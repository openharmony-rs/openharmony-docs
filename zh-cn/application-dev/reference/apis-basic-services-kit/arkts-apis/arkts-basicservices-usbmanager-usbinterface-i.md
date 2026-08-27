# USBInterface

一个[USBConfiguration](arkts-basicservices-usbmanager-usbconfiguration-i.md)中可以含有多个USBInterface，每个USBInterface提供一个功能。

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## alternateSetting

```TypeScript
alternateSetting: number
```

接口的替代设置索引号，用于在同一个接口的多个可选描述符中进行切换选择。0表示默认设置，其他值表示特定的替代设置。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## clazz

```TypeScript
clazz: number
```

设备类型。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## endpoints

```TypeScript
endpoints: Array<USBEndpoint>
```

当前接口所包含的端点。

**类型：** Array&lt;USBEndpoint&gt;

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## id

```TypeScript
id: number
```

接口的唯一标识。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## name

```TypeScript
name: string
```

接口名称。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## protocol

```TypeScript
protocol: number
```

接口的协议。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## subClass

```TypeScript
subClass: number
```

设备子类。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager
