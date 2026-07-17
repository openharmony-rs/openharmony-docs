# ConnectionStateParams

获取连接状态所需的参数。

**起始版本：** 26.0.0

<!--Device-dataTransfer-interface ConnectionStateParams--><!--Device-dataTransfer-interface ConnectionStateParams-End-->

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

<!--Device-ConnectionStateParams-address: string--><!--Device-ConnectionStateParams-address: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## uuid

```TypeScript
uuid: string
```

服务UUID。长度必须为36，由16进制数字字符和连字符共36个字符组成，形如“FFFFFFFF-1234-5678-ABCD-000000001234”，代表128比特标识。<br>禁止使用星闪标准服务UUID。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectionStateParams-uuid: string--><!--Device-ConnectionStateParams-uuid: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

