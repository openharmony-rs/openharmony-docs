# PropertyWriteType

```TypeScript
enum PropertyWriteType
```

表示Property支持的写类型，为枚举值。

**起始版本：** 26.0.0

<!--Device-ssap-enum PropertyWriteType--><!--Device-ssap-enum PropertyWriteType-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## WRITE

```TypeScript
WRITE = 1
```

表示写属性请求并等待服务端响应回复。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PropertyWriteType-WRITE = 1--><!--Device-PropertyWriteType-WRITE = 1-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## WRITE_NO_RESPONSE

```TypeScript
WRITE_NO_RESPONSE = 2
```

表示写属性请求，无需服务端响应回复。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PropertyWriteType-WRITE_NO_RESPONSE = 2--><!--Device-PropertyWriteType-WRITE_NO_RESPONSE = 2-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base
