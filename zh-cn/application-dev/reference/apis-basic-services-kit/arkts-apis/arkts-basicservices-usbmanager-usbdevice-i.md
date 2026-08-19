# USBDevice

USB设备信息。

**起始版本：** 23

<!--Device-usbManager-interface USBDevice--><!--Device-usbManager-interface USBDevice-End-->

**系统能力：** SystemCapability.USB.USBManager

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## busNum

```TypeScript
busNum: int
```

总线地址。

**类型：** int

**起始版本：** 23

<!--Device-USBDevice-busNum: int--><!--Device-USBDevice-busNum: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## clazz

```TypeScript
clazz: int
```

设备类型代码。

**类型：** int

**起始版本：** 23

<!--Device-USBDevice-clazz: int--><!--Device-USBDevice-clazz: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## configs

```TypeScript
configs: Array<USBConfiguration>
```

设备配置描述符信息。

**类型：** Array&lt;[USBConfiguration](arkts-basicservices-usbmanager-usbconfiguration-i.md)&gt;

**起始版本：** 23

<!--Device-USBDevice-configs: Array<USBConfiguration>--><!--Device-USBDevice-configs: Array<USBConfiguration>-End-->

**系统能力：** SystemCapability.USB.USBManager

## devAddress

```TypeScript
devAddress: int
```

设备地址。

**类型：** int

**起始版本：** 23

<!--Device-USBDevice-devAddress: int--><!--Device-USBDevice-devAddress: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## manufacturerName

```TypeScript
manufacturerName: string
```

设备厂商名称。

**类型：** string

**起始版本：** 23

<!--Device-USBDevice-manufacturerName: string--><!--Device-USBDevice-manufacturerName: string-End-->

**系统能力：** SystemCapability.USB.USBManager

## name

```TypeScript
name: string
```

设备名称。

**类型：** string

**起始版本：** 23

<!--Device-USBDevice-name: string--><!--Device-USBDevice-name: string-End-->

**系统能力：** SystemCapability.USB.USBManager

## productId

```TypeScript
productId: int
```

产品ID。

**类型：** int

**起始版本：** 23

<!--Device-USBDevice-productId: int--><!--Device-USBDevice-productId: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## productName

```TypeScript
productName: string
```

设备产品名称。

**类型：** string

**起始版本：** 23

<!--Device-USBDevice-productName: string--><!--Device-USBDevice-productName: string-End-->

**系统能力：** SystemCapability.USB.USBManager

## protocol

```TypeScript
protocol: int
```

设备协议代码。

**类型：** int

**起始版本：** 23

<!--Device-USBDevice-protocol: int--><!--Device-USBDevice-protocol: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## serial

```TypeScript
serial: string
```

序列号。三方应用无法获取此字段的设备序列号信息（该字段对三方应用不可用），如需获取序列号需在申请设备访问权限后自行发起控制传输。

**类型：** string

**起始版本：** 23

<!--Device-USBDevice-serial: string--><!--Device-USBDevice-serial: string-End-->

**系统能力：** SystemCapability.USB.USBManager

## subClass

```TypeScript
subClass: int
```

设备子类型代码。

**类型：** int

**起始版本：** 23

<!--Device-USBDevice-subClass: int--><!--Device-USBDevice-subClass: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## vendorId

```TypeScript
vendorId: int
```

厂商ID。

**类型：** int

**起始版本：** 23

<!--Device-USBDevice-vendorId: int--><!--Device-USBDevice-vendorId: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## version

```TypeScript
version: string
```

设备版本号。

**类型：** string

**起始版本：** 23

<!--Device-USBDevice-version: string--><!--Device-USBDevice-version: string-End-->

**系统能力：** SystemCapability.USB.USBManager

