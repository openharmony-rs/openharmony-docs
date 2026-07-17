# HardwareDescriptor（系统接口）

表示分布式硬件的描述信息。

**起始版本：** 11

<!--Device-hardwareManager-interface HardwareDescriptor--><!--Device-hardwareManager-interface HardwareDescriptor-End-->

**系统能力：** SystemCapability.DistributedHardware.DistributedHardwareFWK

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { hardwareManager } from '@kit.DistributedServiceKit';
```

## srcNetworkId

```TypeScript
srcNetworkId?: string
```

表示源端设备，缺省时表示所有源端设备。

**类型：** string

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_DISTRIBUTED_HARDWARE

<!--Device-HardwareDescriptor-srcNetworkId?: string--><!--Device-HardwareDescriptor-srcNetworkId?: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DistributedHardwareFWK

**系统接口：** 此接口为系统接口。

## type

```TypeScript
type: DistributedHardwareType
```

分布式硬件类型。

**类型：** DistributedHardwareType

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_DISTRIBUTED_HARDWARE

<!--Device-HardwareDescriptor-type: DistributedHardwareType--><!--Device-HardwareDescriptor-type: DistributedHardwareType-End-->

**系统能力：** SystemCapability.DistributedHardware.DistributedHardwareFWK

**系统接口：** 此接口为系统接口。

