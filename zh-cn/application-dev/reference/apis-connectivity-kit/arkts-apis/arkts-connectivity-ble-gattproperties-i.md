# GattProperties

描述GATT特征值支持的属性。决定了特征值内容和描述符如何被使用和访问。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## authenticatedSignedWrite

```TypeScript
authenticatedSignedWrite?: boolean
```

该特征值是否支持签名写入操作，通过对写入内容进行签名校验替代加密流程。

true表示支持，且该特征值权限[GattPermissions](arkts-connectivity-ble-gattpermissions-i.md)中的writeSigned或writeSignedMitm需设置为true，否则该属性不生效，false表示不支持。默认值为false。

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## broadcast

```TypeScript
broadcast?: boolean
```

该特征值是否支持作为广播内容由server端发送。

true表示支持，server端可将特征值内容以[ServiceData](arkts-connectivity-ble-servicedata-i.md)类型在广播报文中携带，false表示不支持。默认值为false。

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## extendedProperties

```TypeScript
extendedProperties?: boolean
```

该特征值是否存在扩展属性。

true表示存在扩展属性，即该特征值关联了特征值扩展属性描述符（UUID：00002900-0000-1000-8000-00805f9b34fb），用于定义附加的特征值属性（如可靠写入等）；false表示不存在扩展属性。默认值为false。

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## indicate

```TypeScript
indicate?: boolean
```

该特征值是否支持向对端设备指示特征值内容。

true表示支持，对端设备需要回复确认，false表示不支持。默认值为false。

**类型：** boolean

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## notify

```TypeScript
notify?: boolean
```

该特征值是否支持主动向对端设备通知特征值内容。

true表示支持，且对端设备不需要回复确认，false表示不支持。默认值为false。

**类型：** boolean

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## read

```TypeScript
read?: boolean
```

该特征值是否支持读取操作。

true表示支持，false表示不支持。默认值为true。

**类型：** boolean

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## write

```TypeScript
write?: boolean
```

该特征值是否支持写入操作。

true表示支持，且被写入时需要回复对端设备，false表示不支持。默认值为true。

**类型：** boolean

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## writeNoResponse

```TypeScript
writeNoResponse?: boolean
```

该特征值是否支持写入操作。

true表示支持，且被写入时无需回复对端设备，false表示不支持。默认值为true。

**类型：** boolean

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
