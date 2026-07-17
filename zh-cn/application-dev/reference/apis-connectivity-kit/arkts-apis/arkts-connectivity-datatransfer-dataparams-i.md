# DataParams

数据参数说明。

**起始版本：** 26.0.0

<!--Device-dataTransfer-interface DataParams--><!--Device-dataTransfer-interface DataParams-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { dataTransfer } from '@kit.ConnectivityKit';
```

## address

```TypeScript
address: string
```

连接的设备地址。长度必须为17，由十六进制数字和冒号组成，例如：11:22:33:AA:BB:FF。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataParams-address: string--><!--Device-DataParams-address: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## data

```TypeScript
data: ArrayBuffer
```

数据缓冲区。

**类型：** ArrayBuffer

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataParams-data: ArrayBuffer--><!--Device-DataParams-data: ArrayBuffer-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## uuid

```TypeScript
uuid: string
```

服务ID。长度必须为36，由16进制数字字符和连字符共36个字符组成，形如“FFFFFFFF-1234-5678-ABCD-000000001234”，代表128比特标识。<br>禁止使用星闪标准服务UUID。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataParams-uuid: string--><!--Device-DataParams-uuid: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

