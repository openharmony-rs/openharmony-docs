# Asset

记录资产附件（文件、图片、视频等类型文件）的相关信息，相关示例见[在跨端迁移中使用分布式数据对象迁移数据](../../../database/data-sync-of-distributed-data-object.md#在跨端迁移中使用分布式数据对象迁移数据)的示例代码。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CommonType

## 导入模块

```TypeScript
import { commonType } from '@kit.ArkData';
```

## createTime

```TypeScript
createTime: string
```

资产被创建出来的时间。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CommonType

## modifyTime

```TypeScript
modifyTime: string
```

资产最后一次被修改的时间。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CommonType

## name

```TypeScript
name: string
```

资产的名称。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CommonType

## path

```TypeScript
path: string
```

资产在应用沙箱里的路径。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CommonType

## size

```TypeScript
size: string
```

资产占用空间的大小（单位：字节（Byte），取值为非负整数）。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CommonType

## status

```TypeScript
status?: AssetStatus
```

资产的状态，默认值为ASSET_NORMAL。

**类型：** [AssetStatus](arkts-arkdata-commontype-assetstatus-e.md)

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CommonType

## uri

```TypeScript
uri: string
```

资产的uri，在系统里的绝对路径。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CommonType
