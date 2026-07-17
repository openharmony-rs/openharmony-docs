# CloudAsset（系统接口）

云资产的信息。

**继承/实现关系：** CloudAsset extends [relationalStore.Asset](relationalStore.Asset)

**起始版本：** 11

<!--Device-cloudExtension-export interface CloudAsset extends relationalStore.Asset--><!--Device-cloudExtension-export interface CloudAsset extends relationalStore.Asset-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## assetId

```TypeScript
assetId: string
```

资产ID。

**类型：** string

**起始版本：** 11

<!--Device-CloudAsset-assetId: string--><!--Device-CloudAsset-assetId: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## hash

```TypeScript
hash: string
```

资产的修改时间和大小转换成的哈希值。

**类型：** string

**起始版本：** 11

<!--Device-CloudAsset-hash: string--><!--Device-CloudAsset-hash: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

