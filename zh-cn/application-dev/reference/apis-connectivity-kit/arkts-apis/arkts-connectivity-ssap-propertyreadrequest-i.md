# PropertyReadRequest

SSAP客户端属性读请求参数说明。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-ssap-interface PropertyReadRequest--><!--Device-ssap-interface PropertyReadRequest-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## address

```TypeScript
address: string
```

设备地址。 长度必须为17，由16进制数字和冒号组成，形如 "11:22:33:AA:BB:FF"。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PropertyReadRequest-address: string--><!--Device-PropertyReadRequest-address: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## propertyUuid

```TypeScript
propertyUuid: string
```

客户端请求读取的属性实例的UUID。 长度必须为36，由16进制数字字符和连字符共36个字符组成，形如“FFFFFFFF-1234-5678-ABCD-000000001234”，代表128比特标识。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_禁止使用星闪标准服务UUID。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PropertyReadRequest-propertyUuid: string--><!--Device-PropertyReadRequest-propertyUuid: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## requestId

```TypeScript
requestId: int
```

请求ID。 取值范围为全体整数。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PropertyReadRequest-requestId: int--><!--Device-PropertyReadRequest-requestId: int-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## serviceUuid

```TypeScript
serviceUuid: string
```

属性所属的\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_实例的UUID 长度必须为32，禁止使用星闪标准服务UUID。 \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_不允许使用NearLink标准UUID。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PropertyReadRequest-serviceUuid: string--><!--Device-PropertyReadRequest-serviceUuid: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

