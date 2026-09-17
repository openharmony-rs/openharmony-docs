# ScanFilters

表示扫描过滤条件。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { scan } from '@kit.ConnectivityKit';
```

## address

```TypeScript
address?: string
```

表示设备地址，若未配置则默认不过滤该字段。地址格式参考：11:22:33:AA:BB:FF。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## deviceName

```TypeScript
deviceName?: string
```

表示设备名称，字符串长度范围[0, 30]。若未配置则默认不过滤该字段。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## manufacturerData

```TypeScript
manufacturerData?: ArrayBuffer
```

表示厂商数据，若未配置则默认不过滤该字段。配置该字段需同时配置manufacturerId。

**类型：** ArrayBuffer

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## manufacturerDataMask

```TypeScript
manufacturerDataMask?: ArrayBuffer
```

表示厂商数据掩码，若未配置则默认不过滤该字段。配置该字段需同时配置manufacturerData，且二者长度必须一致。掩码与厂商数据按位与运算，用于精确匹配厂商数据中指定比特位。

**类型：** ArrayBuffer

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## manufacturerId

```TypeScript
manufacturerId?: number
```

表示厂商ID，取值范围[1, 65535]，若未配置则默认不过滤该字段。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## rssi

```TypeScript
rssi?: number
```

过滤信号强度大于或等于该信号强度门限值的广播报文，取值范围[-128, 127]，单位：dBm。建议设置[-90, 20]范围内的门限值。若未配置则默认不对信号强度进行过滤。取值限定为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base
