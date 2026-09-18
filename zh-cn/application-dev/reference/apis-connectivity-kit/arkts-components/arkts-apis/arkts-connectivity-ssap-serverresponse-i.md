# ServerResponse

表示回复客户端请求的响应。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## address

```TypeScript
address: string
```

表示客户端设备地址。地址格式参考：11:22:33:AA:BB:FF。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## requestId

```TypeScript
requestId: number
```

表示请求ID。取值范围[0, 65535]。该ID必须与收到的[PropertyReadRequest](arkts-connectivity-ssap-propertyreadrequest-i.md)或[PropertyWriteRequest](arkts-connectivity-ssap-propertywriterequest-i.md)中的requestId一致，用于关联请求与响应。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## value

```TypeScript
value: ArrayBuffer
```

表示回复的数据值。

**类型：** ArrayBuffer

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base
