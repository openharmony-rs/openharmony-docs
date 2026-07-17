# Event（系统接口）

SSAP事件。

**起始版本：** 26.0.0

<!--Device-ssap-interface Event--><!--Device-ssap-interface Event-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## eventUuid

```TypeScript
eventUuid: string
```

事件实例的UUID。长度必须为36，由16进制数字字符和连字符共36个字符组成，形如“FFFFFFFF-1234-5678-ABCD-000000001234”，代表128比特标识。<br>不允许使用NearLink标准UUID。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Event-eventUuid: string--><!--Device-Event-eventUuid: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

## parameter

```TypeScript
parameter?: ArrayBuffer
```

事件实例的参数。

**类型：** ArrayBuffer

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Event-parameter?: ArrayBuffer--><!--Device-Event-parameter?: ArrayBuffer-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

## serviceUuid

```TypeScript
serviceUuid: string
```

事件所属服务实例的UUID长度必须为36，由16进制数字字符和连字符共36个字符组成，形如“FFFFFFFF-1234-5678-ABCD-000000001234”，代表128比特标识。<br>禁止使用星闪标准服务UUID。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Event-serviceUuid: string--><!--Device-Event-serviceUuid: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

