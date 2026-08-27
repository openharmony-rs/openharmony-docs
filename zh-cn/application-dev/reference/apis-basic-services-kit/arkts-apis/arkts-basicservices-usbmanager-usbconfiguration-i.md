# USBConfiguration

USB配置，一个[USBDevice](arkts-basicservices-usbmanager-usbdevice-i.md)中可以含有多个配置。

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## attributes

```TypeScript
attributes: number
```

配置的属性，取值遵循USB配置描述符规范，用于表示配置的供电方式、远程唤醒能力等特性。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## id

```TypeScript
id: number
```

配置的唯一标识。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## interfaces

```TypeScript
interfaces: Array<USBInterface>
```

配置支持的接口列表。

**类型：** Array&lt;USBInterface&gt;

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## isRemoteWakeup

```TypeScript
isRemoteWakeup: boolean
```

检查当前配置是否支持远程唤醒。true表示支持，false表示不支持。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## isSelfPowered

```TypeScript
isSelfPowered: boolean
```

检查当前配置是否支持独立电源。true表示支持，false表示不支持。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## maxPower

```TypeScript
maxPower: number
```

最大功耗，（单位：毫安）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## name

```TypeScript
name: string
```

配置的名称，可以为空字符串。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager
