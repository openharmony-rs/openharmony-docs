# AdvertiseData

描述BLE广播报文数据内容，也可以用作回复扫描请求的广播报文数据内容。支持传统广播和扩展广播，传统广播报文最大长度为31个字节，扩展广播报文最大长度由蓝牙芯片能力决定。若超出最大长度限制，会导致启动广播失败。

传统广播模式下，若携带了所有参数，尤其是携带了广播名称（通过includeDeviceName或advertiseName进行设置），需要注意广播报文长度。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## advertiseName

```TypeScript
advertiseName?: string
```

要携带的自定义广播名称。若不设置此参数，则默认不携带自定义广播名称。

不可与includeDeviceName同时使用。

[ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME](../../../security/AccessToken/restricted-permissions.md#ohospermissionmanage_bluetooth_advertiser_name)

**类型：** string

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## includeDeviceName

```TypeScript
includeDeviceName?: boolean
```

是否携带本机的设备名称作为广播名称。

true表示携带，false表示不携带，默认值为false。

若应用需要自定义广播名称，可通过advertiseName进行设置。本参数不可与advertiseName同时使用。

**类型：** boolean

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## includeTxPower

```TypeScript
includeTxPower?: boolean
```

是否携带广播发送功率。

true表示携带广播发送功率，false表示不携带广播发送功率，默认值为false。

携带该值后，广播报文长度将多占用3个字节。

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## manufactureData

```TypeScript
manufactureData: Array<ManufactureData>
```

要携带的制造商数据内容。

**类型：** Array&lt;[ManufactureData](arkts-connectivity-ble-manufacturedata-i.md)&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceData

```TypeScript
serviceData: Array<ServiceData>
```

要携带的服务数据内容。

**类型：** Array&lt;[ServiceData](arkts-connectivity-ble-servicedata-i.md)&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceUuids

```TypeScript
serviceUuids: Array<string>
```

要携带的服务UUID。

**类型：** Array&lt;string&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
