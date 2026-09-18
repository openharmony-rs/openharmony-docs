# GattPermissions

描述读写GATT特征值或描述符需具备的权限。

**起始版本：** 20

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## read

```TypeScript
read?: boolean
```

是否允许读取该特征值或描述符内容。

true表示允许，false表示不允许。默认值为true。

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## readEncrypted

```TypeScript
readEncrypted?: boolean
```

读取该特征值或描述符内容是否需要加密。

true表示需要加密后，方可读取内容，false表示不需要普通方式加密。默认值为false。

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## readEncryptedMitm

```TypeScript
readEncryptedMitm?: boolean
```

读取该特征值或描述符内容是否需要防中间人攻击的加密。

防中间人攻击表示操作需要经过认证，防止数据被第三方篡改。true表示需要防中间人攻击的加密后才能读取内容，false表示不需要防中间人攻击的加密。默认值为false。

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## write

```TypeScript
write?: boolean
```

是否允许写入该特征值或描述符内容。

true表示允许，false表示不允许。默认值为true。

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## writeEncrypted

```TypeScript
writeEncrypted?: boolean
```

写入该特征值或描述符内容是否需要加密。

true表示需要加密后，方可写入内容，false表示不需要普通方式加密。默认值为false。

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## writeEncryptedMitm

```TypeScript
writeEncryptedMitm?: boolean
```

写入该特征值或描述符内容是否需要防中间人攻击的加密。

true表示需要防中间人攻击的加密后才能写入内容，false表示不需要防中间人攻击的加密。默认值为false。

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## writeSigned

```TypeScript
writeSigned?: boolean
```

写入该特征值或描述符内容是否需要经过签名处理。

true表示内容需要签名处理后方可写入，false表示不需要签名处理。默认值为false。

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## writeSignedMitm

```TypeScript
writeSignedMitm?: boolean
```

写入该特征值或描述符内容是否需要经过防中间人攻击方式的签名处理。

true表示需要防中间人攻击方式的签名处理后方可写入，false表示不需要以防中间人攻击方式签名处理。默认值为false。

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
