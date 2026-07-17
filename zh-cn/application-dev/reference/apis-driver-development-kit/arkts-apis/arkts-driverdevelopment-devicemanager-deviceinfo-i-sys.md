# DeviceInfo（系统接口）

设备详细信息。

**起始版本：** 12

<!--Device-deviceManager-interface DeviceInfo--><!--Device-deviceManager-interface DeviceInfo-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
```

## deviceId

```TypeScript
deviceId: number
```

设备ID。

**类型：** number

**起始版本：** 12

<!--Device-DeviceInfo-deviceId: long--><!--Device-DeviceInfo-deviceId: long-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**系统接口：** 此接口为系统接口。

## driverUid

```TypeScript
driverUid?: string
```

设备匹配的驱动UID。

**类型：** string

**起始版本：** 12

<!--Device-DeviceInfo-driverUid?: string--><!--Device-DeviceInfo-driverUid?: string-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**系统接口：** 此接口为系统接口。

## isDriverMatched

```TypeScript
isDriverMatched: boolean
```

设备是否匹配到驱动。`true`：匹配到驱动；`false`：未匹配到驱动。

**类型：** boolean

**起始版本：** 12

<!--Device-DeviceInfo-isDriverMatched: boolean--><!--Device-DeviceInfo-isDriverMatched: boolean-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**系统接口：** 此接口为系统接口。

