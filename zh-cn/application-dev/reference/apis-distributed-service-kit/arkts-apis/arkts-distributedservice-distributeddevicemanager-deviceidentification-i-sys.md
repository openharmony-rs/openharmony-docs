# DeviceIdentification（系统接口）

用于分布式设备识别的结构体。

**起始版本：** 24

<!--Device-distributedDeviceManager-interface DeviceIdentification--><!--Device-distributedDeviceManager-interface DeviceIdentification-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
```

## deviceId

```TypeScript
deviceId: string
```

应用获取的匿名化设备ID。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceIdentification-deviceId: string--><!--Device-DeviceIdentification-deviceId: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## udid

```TypeScript
udid: string
```

设备唯一标识。

**类型：** string

**起始版本：** 24

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC and ohos.permission.ACCESS_SERVICE_DM and ohos.permission.sec.ACCESS_UDID

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceIdentification-udid: string--><!--Device-DeviceIdentification-udid: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

