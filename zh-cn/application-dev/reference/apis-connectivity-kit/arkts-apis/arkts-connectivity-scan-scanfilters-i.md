# ScanFilters

扫描过滤器。

**起始版本：** 26.0.0

<!--Device-scan-interface ScanFilters--><!--Device-scan-interface ScanFilters-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { scan } from '@kit.ConnectivityKit';
```

## address

```TypeScript
address?: string
```

设备地址。长度必须为17，由16进制数字和冒号组成，形如 "11:22:33:AA:BB:FF"。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScanFilters-address?: string--><!--Device-ScanFilters-address?: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## deviceName

```TypeScript
deviceName?: string
```

设备名称。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScanFilters-deviceName?: string--><!--Device-ScanFilters-deviceName?: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## manufacturerData

```TypeScript
manufacturerData?: ArrayBuffer
```

制造商数据。

**类型：** ArrayBuffer

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScanFilters-manufacturerData?: ArrayBuffer--><!--Device-ScanFilters-manufacturerData?: ArrayBuffer-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## manufacturerDataMask

```TypeScript
manufacturerDataMask?: ArrayBuffer
```

制造商数据掩码。

**类型：** ArrayBuffer

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScanFilters-manufacturerDataMask?: ArrayBuffer--><!--Device-ScanFilters-manufacturerDataMask?: ArrayBuffer-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## manufacturerId

```TypeScript
manufacturerId?: number
```

厂商ID。取值范围为全体整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScanFilters-manufacturerId?: int--><!--Device-ScanFilters-manufacturerId?: int-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## rssi

```TypeScript
rssi?: number
```

接收信号强度指示。单位为： 分贝毫瓦，取值应为[-128,127]内的整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScanFilters-rssi?: int--><!--Device-ScanFilters-rssi?: int-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

