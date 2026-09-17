# Method（系统接口）

表示服务的方法。

**起始版本：** 26.0.0

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

表示方法UUID。数据格式同serviceUuid。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

## parameter

```TypeScript
parameter?: ArrayBuffer
```

表示方法的参数，数据格式由具体服务定义。若未配置则默认不携带该字段。

**类型：** ArrayBuffer

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

## result

```TypeScript
result?: ArrayBuffer
```

表示方法的返回值，数据格式由具体服务定义。若未配置则默认不携带该字段。

**类型：** ArrayBuffer

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

## serviceUuid

```TypeScript
serviceUuid: string
```

星闪服务UUID，个字符，由32个十六进制数字和4个连字符（-）组成，例如： FFFFFFFF-1234-5678-ABCD-000000001234，表示一个128位标识符。 不允许使用星闪标准UUID。长度必须为36。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。
