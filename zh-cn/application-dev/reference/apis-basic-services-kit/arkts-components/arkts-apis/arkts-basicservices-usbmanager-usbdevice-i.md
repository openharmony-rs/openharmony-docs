# USBDevice

USB设备信息。

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## busNum

```TypeScript
busNum: number
```

总线地址。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## clazz

```TypeScript
clazz: number
```

设备类型代码。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## configs

```TypeScript
configs: Array<USBConfiguration>
```

设备配置描述符信息。

**类型：** Array&lt;[USBConfiguration](arkts-basicservices-usbmanager-usbconfiguration-i.md)&gt;

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## devAddress

```TypeScript
devAddress: number
```

设备地址。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## manufacturerName

```TypeScript
manufacturerName: string
```

设备厂商名称。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## name

```TypeScript
name: string
```

设备名称。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## productId

```TypeScript
productId: number
```

产品ID。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## productName

```TypeScript
productName: string
```

设备产品名称。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## protocol

```TypeScript
protocol: number
```

设备协议代码。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## serial

```TypeScript
serial: string
```

序列号。三方应用无法获取此字段的设备序列号信息（该字段对三方应用不可用），如需获取序列号需在申请设备访问权限后自行发起控制传输。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## subClass

```TypeScript
subClass: number
```

设备子类型代码。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## vendorId

```TypeScript
vendorId: number
```

厂商ID。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## version

```TypeScript
version: string
```

设备版本号。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager
