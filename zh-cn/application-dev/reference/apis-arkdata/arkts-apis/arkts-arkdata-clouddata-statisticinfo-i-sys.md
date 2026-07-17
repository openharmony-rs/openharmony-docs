# StatisticInfo（系统接口）

端云同步的统计信息。

**起始版本：** 12

<!--Device-cloudData-interface StatisticInfo--><!--Device-cloudData-interface StatisticInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## inserted

```TypeScript
inserted: number
```

本地新增且未同步到云端的数据条数，如返回值为2，表示本地新增2条数据且还未同步到云端。

**类型：** number

**起始版本：** 12

<!--Device-StatisticInfo-inserted: int--><!--Device-StatisticInfo-inserted: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

## normal

```TypeScript
normal: number
```

端云一致的数据条数。如返回值为2，表示本地与云端一致的数据为2条。

**类型：** number

**起始版本：** 12

<!--Device-StatisticInfo-normal: int--><!--Device-StatisticInfo-normal: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

## table

```TypeScript
table: string
```

查询的表名。如返回值为"cloud_notes"，表示查询结果是表名为"cloud_notes"的同步信息。

**类型：** string

**起始版本：** 12

<!--Device-StatisticInfo-table: string--><!--Device-StatisticInfo-table: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

## updated

```TypeScript
updated: number
```

云端同步之后，本地或云端修改还未同步的数据条数，如返回值为2，表示本地或云端修改还有2条数据未同步。

**类型：** number

**起始版本：** 12

<!--Device-StatisticInfo-updated: int--><!--Device-StatisticInfo-updated: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

