# DeviceBasicInfo

分布式设备基本信息。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

## 导入模块

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
```

## deviceId

```TypeScript
deviceId: string
```

设备标识符。实际值为udid-hash与appid和盐值基于sha256方式进行混淆后的值。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

## deviceName

```TypeScript
deviceName: string
```

设备名称。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

## deviceType

```TypeScript
deviceType: string
```

[设备类型](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getdevicetype)。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

## networkId

```TypeScript
networkId?: string
```

设备网络标识。未提供时默认为空字符串。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.DistributedHardware.DeviceManager
