# DeviceIconInfoFilterOptions（系统接口）

设备图标信息过滤选项。

**起始版本：** 18

<!--Device-distributedDeviceManager-interface DeviceIconInfoFilterOptions--><!--Device-distributedDeviceManager-interface DeviceIconInfoFilterOptions-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
```

## imageType

```TypeScript
imageType: string
```

图片类型。固定值为"ID"，表示产品实物图。

**类型：** string

**起始版本：** 18

<!--Device-DeviceIconInfoFilterOptions-imageType: string--><!--Device-DeviceIconInfoFilterOptions-imageType: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## internalModel

```TypeScript
internalModel?: string
```

设备所属产品的内部型号。默认为空。

**类型：** string

**起始版本：** 18

<!--Device-DeviceIconInfoFilterOptions-internalModel?: string--><!--Device-DeviceIconInfoFilterOptions-internalModel?: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## productId

```TypeScript
productId: string
```

设备所属产品ID。

**类型：** string

**起始版本：** 18

<!--Device-DeviceIconInfoFilterOptions-productId: string--><!--Device-DeviceIconInfoFilterOptions-productId: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## specName

```TypeScript
specName: string
```

图片规格名称。取值范围：

- lg：大图，尺寸为1016064px。  
- sm：小图，尺寸为65536px。

**类型：** string

**起始版本：** 18

<!--Device-DeviceIconInfoFilterOptions-specName: string--><!--Device-DeviceIconInfoFilterOptions-specName: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## subProductId

```TypeScript
subProductId?: string
```

设备所属产品子ID。默认为空。

**类型：** string

**起始版本：** 18

<!--Device-DeviceIconInfoFilterOptions-subProductId?: string--><!--Device-DeviceIconInfoFilterOptions-subProductId?: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

