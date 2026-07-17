# NetworkIdQueryFilter（系统接口）

设备网络ID过滤器选项。

**起始版本：** 18

<!--Device-distributedDeviceManager-interface NetworkIdQueryFilter--><!--Device-distributedDeviceManager-interface NetworkIdQueryFilter-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
```

## onlineStatus

```TypeScript
onlineStatus : number
```

设备在线状态，包括

- 0：表示设备处于离线状态。  
- 1：表示设备处于在线状态。

**类型：** number

**起始版本：** 18

<!--Device-NetworkIdQueryFilter-onlineStatus : int--><!--Device-NetworkIdQueryFilter-onlineStatus : int-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## wiseDeviceId

```TypeScript
wiseDeviceId : string
```

已注册设备标识。

**类型：** string

**起始版本：** 18

<!--Device-NetworkIdQueryFilter-wiseDeviceId : string--><!--Device-NetworkIdQueryFilter-wiseDeviceId : string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

