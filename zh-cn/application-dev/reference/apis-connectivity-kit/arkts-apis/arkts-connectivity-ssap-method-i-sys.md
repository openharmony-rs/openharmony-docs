# Method（系统接口）

SSAP方法。

**起始版本：** 26.0.0

<!--Device-ssap-interface Method--><!--Device-ssap-interface Method-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## methodUuid

```TypeScript
methodUuid: string
```

方法实例的UUID长度必须为36，由16进制数字字符和连字符共36个字符组成，形如“FFFFFFFF-1234-5678-ABCD-000000001234”，代表128比特标识。<br>不允许使用NearLink标准UUID。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Method-methodUuid: string--><!--Device-Method-methodUuid: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

## parameter

```TypeScript
parameter?: ArrayBuffer
```

方法实例的参数

**类型：** ArrayBuffer

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Method-parameter?: ArrayBuffer--><!--Device-Method-parameter?: ArrayBuffer-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

## result

```TypeScript
result?: ArrayBuffer
```

方法实例的结果

**类型：** ArrayBuffer

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Method-result?: ArrayBuffer--><!--Device-Method-result?: ArrayBuffer-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

## serviceUuid

```TypeScript
serviceUuid: string
```

方法所属的{@link Service}实例的UUID长度必须为36，由16进制数字字符和连字符共36个字符组成，形如“FFFFFFFF-1234-5678-ABCD-000000001234”，代表128比特标识。<br>不允许使用NearLink标准UUID。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Method-serviceUuid: string--><!--Device-Method-serviceUuid: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

