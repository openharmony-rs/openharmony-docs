# BackupConfig

用于备份数据库的配置信息。

**起始版本：** 24

<!--Device-distributedKVStore-interface BackupConfig--><!--Device-distributedKVStore-interface BackupConfig-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## 导入模块

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

## fileName

```TypeScript
fileName: string
```

备份数据库的名称，无长度限制，不能包含特殊字符'/'。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackupConfig-fileName: string--><!--Device-BackupConfig-fileName: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## filePath

```TypeScript
filePath: string
```

备份数据库的路径，无长度限制。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackupConfig-filePath: string--><!--Device-BackupConfig-filePath: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

