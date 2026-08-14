# AdvertisingData

广播数据。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-advertising-interface AdvertisingData--><!--Device-advertising-interface AdvertisingData-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## includeDeviceName

```TypeScript
includeDeviceName?: boolean
```

指示是否包含设备名称。 默认值： 默认值：false。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AdvertisingData-includeDeviceName?: boolean--><!--Device-AdvertisingData-includeDeviceName?: boolean-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## manufacturerData

```TypeScript
manufacturerData?: ManufacturerData[]
```

制造商数据。

**类型：** [ManufacturerData](arkts-connectivity-advertising-manufacturerdata-i.md)[]

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AdvertisingData-manufacturerData?: ManufacturerData[]--><!--Device-AdvertisingData-manufacturerData?: ManufacturerData[]-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## serviceData

```TypeScript
serviceData?: ServiceData[]
```

服务数据。

**类型：** [ServiceData](arkts-connectivity-advertising-servicedata-i.md)[]

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AdvertisingData-serviceData?: ServiceData[]--><!--Device-AdvertisingData-serviceData?: ServiceData[]-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## serviceUuids

```TypeScript
serviceUuids?: string[]
```

指定的服务UUID。 UUID的长度必须为36，由36位十六进制数字和“-”组成。 例如：FFFFFFFF-1234-5678-ABCD-000000001234，表示128位的标识符。

**类型：** string[]

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AdvertisingData-serviceUuids?: string[]--><!--Device-AdvertisingData-serviceUuids?: string[]-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

