# PropertyWriteRequest

SSAP客户端属性写请求参数说明。

**起始版本：** 26.0.0

<!--Device-ssap-interface PropertyWriteRequest--><!--Device-ssap-interface PropertyWriteRequest-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## address

```TypeScript
address: string
```

设备地址。长度必须为17，由16进制数字和冒号组成，形如 "11:22:33:AA:BB:FF"。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PropertyWriteRequest-address: string--><!--Device-PropertyWriteRequest-address: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## propertyUuid

```TypeScript
propertyUuid: string
```

客户端请求写入的属性实例的UUID。长度必须为36，由16进制数字字符和连字符共36个字符组成，形如“FFFFFFFF-1234-5678-ABCD-000000001234”，代表128比特标识。<br>禁止使用星闪标准服务UUID。禁止使用星闪标准服务UUID。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PropertyWriteRequest-propertyUuid: string--><!--Device-PropertyWriteRequest-propertyUuid: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## requestId

```TypeScript
requestId: number
```

请求ID。取值范围为全体整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PropertyWriteRequest-requestId: int--><!--Device-PropertyWriteRequest-requestId: int-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## serviceUuid

```TypeScript
serviceUuid: string
```

属性所属的{@link Service}实例的UUID长度必须为32，禁止使用星闪标准服务UUID。<br>不允许使用NearLink标准UUID。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PropertyWriteRequest-serviceUuid: string--><!--Device-PropertyWriteRequest-serviceUuid: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## value

```TypeScript
value: ArrayBuffer
```

需要写入的数据。

**类型：** ArrayBuffer

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PropertyWriteRequest-value: ArrayBuffer--><!--Device-PropertyWriteRequest-value: ArrayBuffer-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## writeType

```TypeScript
writeType: PropertyWriteType
```

此请求的写入类型。

**类型：** PropertyWriteType

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PropertyWriteRequest-writeType: PropertyWriteType--><!--Device-PropertyWriteRequest-writeType: PropertyWriteType-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

