# @ohos.data.commonType(数据通用类型)

数据通用类型（commonType）是数据管理中通用的数据类型，提供了资产状态枚举、资产信息和键值对存储等基础数据类型，用于支持分布式数据管理场景下的数据统一表示和传递。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CommonType

## 导入模块

```TypeScript
import { commonType } from '@kit.ArkData';
```

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [Asset](arkts-arkdata-commontype-asset-i.md) | 记录资产附件（文件、图片、视频等类型文件）的相关信息，相关示例见[在跨端迁移中使用分布式数据对象迁移数据](../../../database/data-sync-of-distributed-data-object.md#在跨端迁移中使用分布式数据对象迁移数据)的示例代码。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AssetStatus](arkts-arkdata-commontype-assetstatus-e.md) | 描述资产附件的状态枚举。请使用枚举名称而非枚举值。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [Assets](arkts-arkdata-commontype-assets-t.md) | 表示[Asset](arkts-arkdata-commontype-asset-i.md)类型的数组。 |
| [ValuesBucket](arkts-arkdata-commontype-valuesbucket-t.md) | 用于存储键值对的类型。该类型不是并发安全的，如果应用中存在多线程同时操作该类派生出的实例，注意加锁保护。 |
| [ValueType](arkts-arkdata-commontype-valuetype-t.md) | 表示允许的数据字段类型，接口参数具体类型根据其功能而定。 |
