# InterruptData

描述从主机收到的中断数据。

**起始版本：** 23

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { hid } from '@kit.ConnectivityKit';
```

## data

```TypeScript
data: Uint8Array
```

中断数据。其内容长度和解析方式必须严格匹配HID设备注册时通过[HidDeviceSdp](arkts-connectivity-hid-hiddevicesdp-i.md)提供的描述符中为该报告ID定义的格式。

**类型：** Uint8Array

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## id

```TypeScript
id: number
```

对应HID设备注册时通过[HidDeviceSdp](arkts-connectivity-hid-hiddevicesdp-i.md)提供的描述符中定义的报告ID，用于标识报告类型，对于不带ID的简单设备，此参数应设置为0。对于定义了多个报告ID的设备，此处应传入对应的ID值，该ID值必须与描述符中定义的值保持一致。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
