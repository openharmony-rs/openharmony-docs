# Options

用于提供创建数据库的配置信息。

**起始版本：** 9

<!--Device-distributedKVStore-interface Options--><!--Device-distributedKVStore-interface Options-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## 导入模块

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

## autoSync

```TypeScript
autoSync?: boolean
```

设置数据库是否支持跨设备自动同步。默认为false，即只支持手动同步。配置为true，即只支持在跨设备Call调用实现的多端协同中生效，其他场景无法生效。

**类型：** boolean

**起始版本：** 9

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Options-autoSync?: boolean--><!--Device-Options-autoSync?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## backup

```TypeScript
backup?: boolean
```

设置数据库文件是否备份，true为备份，false为不备份，默认为true。

**类型：** boolean

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Options-backup?: boolean--><!--Device-Options-backup?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## createIfMissing

```TypeScript
createIfMissing?: boolean
```

当数据库文件不存在时是否创建数据库，true为创建，false为不创建，默认为true。

**类型：** boolean

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Options-createIfMissing?: boolean--><!--Device-Options-createIfMissing?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## encrypt

```TypeScript
encrypt?: boolean
```

设置数据库文件是否加密，true为加密，false为不加密，默认为false。

**类型：** boolean

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Options-encrypt?: boolean--><!--Device-Options-encrypt?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## kvStoreType

```TypeScript
kvStoreType?: KVStoreType
```

设置要创建的数据库类型，默认为DEVICE_COLLABORATION，即多设备协同数据库。

**类型：** KVStoreType

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Options-kvStoreType?: KVStoreType--><!--Device-Options-kvStoreType?: KVStoreType-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## rootDir

```TypeScript
rootDir?: string
```

设置数据库文件存储路径，不设置即为默认路径（context.databaseDir）。不能设置空字符串，创建数据库和删除数据库时目录必须有访问权限且存在，关闭数据库不校验此参数。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Options-rootDir?: string--><!--Device-Options-rootDir?: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## schema

```TypeScript
schema?: Schema
```

设置定义存储在数据库中的值，默认为undefined，即不使用Schema。

**类型：** Schema

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Options-schema?: Schema--><!--Device-Options-schema?: Schema-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## securityLevel

```TypeScript
securityLevel: SecurityLevel
```

设置数据库安全级别。

**类型：** SecurityLevel

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Options-securityLevel: SecurityLevel--><!--Device-Options-securityLevel: SecurityLevel-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

