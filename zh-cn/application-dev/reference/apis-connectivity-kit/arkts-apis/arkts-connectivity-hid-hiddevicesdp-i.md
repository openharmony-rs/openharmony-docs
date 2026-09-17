# HidDeviceSdp

描述HID设备在服务发现协议（SDP）中的服务注册配置。该结构定义了HID设备的身份标识、能力描述和协议特征，是HID主机发现、识别和连接HID设备的关键参数。

**起始版本：** 23

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { hid } from '@kit.ConnectivityKit';
```

## description

```TypeScript
description: string
```

HID设备的描述信息，要求长度范围：[1, 50]，单位：Byte。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## descriptors

```TypeScript
descriptors: Uint8Array
```

用于标识蓝牙HID设备功能定义的描述符。描述符会为每个支持的报告分配一个唯一的ID， 并详细定义该ID下报告的长度、结构与各字段含义。填写时需要遵循USB HID规范。

**类型：** Uint8Array

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## name

```TypeScript
name: string
```

HID设备的名称，要求长度范围：[1, 50]，单位：Byte。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## provider

```TypeScript
provider: string
```

描述HID设备的制造商信息，要求长度范围：[1, 50]，单位：Byte。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## subclass

```TypeScript
subclass: Subclass
```

表示HID设备具体类型。

**类型：** [Subclass](arkts-connectivity-hid-subclass-e.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
