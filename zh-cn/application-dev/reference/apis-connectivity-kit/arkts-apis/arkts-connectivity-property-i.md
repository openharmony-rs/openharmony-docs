# Property

SSAP属性。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NearLink.Base

## descriptors

```TypeScript
descriptors?: PropertyDescriptor[]
```

属性中包含的描述符列表。

**类型：** PropertyDescriptor[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## operation

```TypeScript
operation?: number
```

指示如何访问数据值和描述符值。
取值为枚举值的或运算。
取值范围为全体整数。 默认值： 默认值：READABLE | WRITE_NO_RESPONSE。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## propertyUuid

```TypeScript
propertyUuid: string
```

Property实例的UUID
长度必须为32，由16进制数字字符和连字符共36个字符组成，形如“FFFFFFFF-1234-5678-ABCD-000000001234”，代表128比特标识。
<br>不允许使用NearLink标准UUID。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## serviceUuid

```TypeScript
serviceUuid: string
```

属性所属的{@link Service}实例的UUID
长度必须为32，禁止使用星闪标准服务UUID。
<br>不允许使用NearLink标准UUID。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## value

```TypeScript
value: ArrayBuffer
```

Property实例的值。

**类型：** ArrayBuffer

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

