# Service

SSAP服务。

**起始版本：** 26.0.0

<!--Device-ssap-interface Service--><!--Device-ssap-interface Service-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## properties

```TypeScript
properties: Property[]
```

属于此服务的属性。

**类型：** Property[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Service-properties: Property[]--><!--Device-Service-properties: Property[]-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## serviceUuid

```TypeScript
serviceUuid: string
```

服务的UUID。长度必须为36，由16进制数字字符和连字符共36个字符组成，形如“FFFFFFFF-1234-5678-ABCD-000000001234”，代表128比特标识。<br>禁止使用星闪标准服务UUID。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Service-serviceUuid: string--><!--Device-Service-serviceUuid: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

