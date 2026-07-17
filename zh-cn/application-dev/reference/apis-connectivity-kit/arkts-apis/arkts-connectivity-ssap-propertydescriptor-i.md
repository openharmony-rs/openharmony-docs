# PropertyDescriptor

属性的SSAP描述符。

**起始版本：** 26.0.0

<!--Device-ssap-interface PropertyDescriptor--><!--Device-ssap-interface PropertyDescriptor-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## descriptorType

```TypeScript
descriptorType: PropertyDescriptorType
```

属性描述符实例的类型。

**类型：** PropertyDescriptorType

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PropertyDescriptor-descriptorType: PropertyDescriptorType--><!--Device-PropertyDescriptor-descriptorType: PropertyDescriptorType-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## isWriteable

```TypeScript
isWriteable?: boolean
```

描述符是否可写。默认值： 默认值：false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PropertyDescriptor-isWriteable?: boolean--><!--Device-PropertyDescriptor-isWriteable?: boolean-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## propertyUuid

```TypeScript
propertyUuid: string
```

描述符所属的属性实例的UUID。长度必须为36，由16进制数字字符和连字符共36个字符组成，形如“FFFFFFFF-1234-5678-ABCD-000000001234”，代表128比特标识。<br>禁止使用星闪标准服务UUID。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PropertyDescriptor-propertyUuid: string--><!--Device-PropertyDescriptor-propertyUuid: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## serviceUuid

```TypeScript
serviceUuid: string
```

描述符所属属性所属的服务实例的UUID。长度必须为36，由16进制数字字符和连字符共36个字符组成，形如“FFFFFFFF-1234-5678-ABCD-000000001234”，代表128比特标识。<br>不允许使用NearLink标准UUID。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PropertyDescriptor-serviceUuid: string--><!--Device-PropertyDescriptor-serviceUuid: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## value

```TypeScript
value: ArrayBuffer
```

属性描述符实例的值。

**类型：** ArrayBuffer

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PropertyDescriptor-value: ArrayBuffer--><!--Device-PropertyDescriptor-value: ArrayBuffer-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

