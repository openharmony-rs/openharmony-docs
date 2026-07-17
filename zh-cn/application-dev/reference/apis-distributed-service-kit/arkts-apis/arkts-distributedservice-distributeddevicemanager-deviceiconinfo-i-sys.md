# DeviceIconInfo（系统接口）

设备图标信息。

**起始版本：** 18

<!--Device-distributedDeviceManager-interface DeviceIconInfo--><!--Device-distributedDeviceManager-interface DeviceIconInfo-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
```

## icon

```TypeScript
icon: ArrayBuffer
```

图标。

**类型：** ArrayBuffer

**起始版本：** 18

<!--Device-DeviceIconInfo-icon: ArrayBuffer--><!--Device-DeviceIconInfo-icon: ArrayBuffer-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## imageType

```TypeScript
imageType: string
```

图片类型。固定值为"ID"，表示产品实物图。

**类型：** string

**起始版本：** 18

<!--Device-DeviceIconInfo-imageType: string--><!--Device-DeviceIconInfo-imageType: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## internalModel

```TypeScript
internalModel?: string
```

设备所属产品的内部型号。默认为空。

**类型：** string

**起始版本：** 18

<!--Device-DeviceIconInfo-internalModel?: string--><!--Device-DeviceIconInfo-internalModel?: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## productId

```TypeScript
productId: string
```

设备所属产品ID。

**类型：** string

**起始版本：** 18

<!--Device-DeviceIconInfo-productId: string--><!--Device-DeviceIconInfo-productId: string-End-->

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

<!--Device-DeviceIconInfo-specName: string--><!--Device-DeviceIconInfo-specName: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## subProductId

```TypeScript
subProductId?: string
```

设备所属产品子ID。默认为空。

**类型：** string

**起始版本：** 18

<!--Device-DeviceIconInfo-subProductId?: string--><!--Device-DeviceIconInfo-subProductId?: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## url

```TypeScript
url: string
```

URL。

**类型：** string

**起始版本：** 18

<!--Device-DeviceIconInfo-url: string--><!--Device-DeviceIconInfo-url: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

