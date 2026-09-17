# AdvertisingData

表示广播数据包。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { advertising } from '@kit.ConnectivityKit';
```

## includeDeviceName

```TypeScript
includeDeviceName?: boolean
```

指示广播数据中是否携带本机设备名。true：表示包含设备名称。false：表示不包含设备名称。默认值为false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## manufacturerData

```TypeScript
manufacturerData?: ManufacturerData[]
```

厂商数据。若未配置则默认不携带该字段。

**类型：** [ManufacturerData](arkts-connectivity-advertising-manufacturerdata-i.md)[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## serviceData

```TypeScript
serviceData?: ServiceData[]
```

服务数据。若未配置则默认不携带该字段。

**类型：** [ServiceData](arkts-connectivity-advertising-servicedata-i.md)[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## serviceUuids

```TypeScript
serviceUuids?: string[]
```

服务UUID列表。UUID长度必须为36个字符，由32个十六进制数字和4个连字符（-）组成。若未配置则默认不携带该字段。

**类型：** string[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base
