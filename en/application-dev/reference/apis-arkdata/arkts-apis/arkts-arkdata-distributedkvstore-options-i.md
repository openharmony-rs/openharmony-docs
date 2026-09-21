# Options

```TypeScript
interface Options
```

Provides KV store configuration.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## Modules to Import

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

## autoSync

```TypeScript
autoSync?: boolean
```

Whether to enable auto sync across devices. The default value is **false**, indicating that only manual sync is supported. If this parameter is set to **true**, &lt;!--RP1--&gt;it takes effect only in [device collaboration using cross-device calls](../../../application-models/hop-multi-device-collaboration.md#using-cross-device-call).&lt;!--RP1End--&gt;

SystemCapability.DistributedDataManager.KVStore.Core

ohos.permission.DISTRIBUTED_DATASYNC

**Type:** boolean

**Since:** 9

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## backup

```TypeScript
backup?: boolean
```

Whether to back up the database files. The value **true** means to back up the database files, and the value **false** means the opposite. The default value is **true**.

SystemCapability.DistributedDataManager.KVStore.Core

**Type:** boolean

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## createIfMissing

```TypeScript
createIfMissing?: boolean
```

Whether to create a database when database files do not exist. The value **true** means to create a database, and the value **false** means the opposite. The default value is **true**.

SystemCapability.DistributedDataManager.KVStore.Core

**Type:** boolean

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## encrypt

```TypeScript
encrypt?: boolean
```

Whether to encrypt the database files. The value **true** means to encrypt the database files, and the value **false** means the opposite. The default value is **false**.

SystemCapability.DistributedDataManager.KVStore.Core

**Type:** boolean

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## kvStoreType

```TypeScript
kvStoreType?: KVStoreType
```

Type of the KV store to create. The default value is **DEVICE_COLLABORATION**, which indicates a device KV store.

SystemCapability.DistributedDataManager.KVStore.Core

**Type:** [KVStoreType](arkts-arkdata-distributedkvstore-kvstoretype-e.md)

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## rootDir

```TypeScript
rootDir?: string
```

Specifies the root directory relative to the database

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## schema

```TypeScript
schema?: Schema
```

Schema that defines the values stored in the KV store. The default value is **undefined**, which means no schema is used.

SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Type:** [Schema](arkts-arkdata-distributedkvstore-schema-c.md)

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## securityLevel

```TypeScript
securityLevel: SecurityLevel
```

Security level of the KV store.

**Type:** [SecurityLevel](arkts-arkdata-distributedkvstore-securitylevel-e.md)

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core
