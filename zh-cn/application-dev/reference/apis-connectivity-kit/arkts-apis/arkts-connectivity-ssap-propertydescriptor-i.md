# PropertyDescriptor

表示Property的描述符。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## descriptorType

```TypeScript
descriptorType: PropertyDescriptorType
```

表示Property的描述符类型。

**类型：** [PropertyDescriptorType](arkts-connectivity-ssap-propertydescriptortype-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## isWriteable

```TypeScript
isWriteable?: boolean
```

表示描述符是否是可写的。true：可写，false：不可写。默认值为true。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## propertyUuid

```TypeScript
propertyUuid: string
```

表示Property的UUID，数据格式同serviceUuid。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## serviceUuid

```TypeScript
serviceUuid: string
```

星闪服务UUID，个字符，由32个十六进制数字和4个连字符（-）组成，例如： FFFFFFFF-1234-5678-ABCD-000000001234，表示一个128位标识符。 不允许使用星闪标准UUID。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## value

```TypeScript
value: ArrayBuffer
```

表示描述符的数据值。

**类型：** ArrayBuffer

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base
