# @ohos.data.commonType (数据通用类型)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @lvcong_oh-->
<!--Designer: @hollokin; @yuchaozhng-->
<!--Tester: @lj_liujing; @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

数据通用类型（commonType）是数据管理中通用的数据类型。

> **说明：**
>
> 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { commonType } from '@kit.ArkData';
```

## AssetStatus

描述资产附件的状态枚举。请使用枚举名称而非枚举值。

**系统能力：** SystemCapability.DistributedDataManager.CommonType

| 名称              | 值  | 说明                         |
| ----------------- | --- | ---------------------------- |
| ASSET_NORMAL      | 1   | 表示资产状态正常。           |
| ASSET_INSERT      | 2   | 表示资产需要插入到云端。     |
| ASSET_UPDATE      | 3   | 表示资产需要更新到云端。     |
| ASSET_DELETE      | 4   | 表示资产需要在云端删除。     |
| ASSET_ABNORMAL    | 5   | 表示资产状态异常。           |
| ASSET_DOWNLOADING | 6   | 表示资产正在下载到本地设备。 |

## Asset

记录资产附件（文件、图片、视频等类型文件）的相关信息，相关示例见[在跨端迁移中使用分布式数据对象迁移数据](../../database/data-sync-of-distributed-data-object.md#在跨端迁移中使用分布式数据对象迁移数据)的示例代码。

**系统能力：** SystemCapability.DistributedDataManager.CommonType

| 名称       | 类型                        | 必填 | 说明                               |
| ---------- | --------------------------- | ---- | ---------------------------------- |
| name       | string                      | 是   | 资产的名称。                       |
| uri        | string                      | 是   | 资产的uri，在系统里的绝对路径。    |
| path       | string                      | 是   | 资产在应用沙箱里的路径。           |
| createTime | string                      | 是   | 资产被创建出来的时间。             |
| modifyTime | string                      | 是   | 资产最后一次被修改的时间。         |
| size       | string                      | 是   | 资产占用空间的大小。               |
| status     | [AssetStatus](#assetstatus) | 否   | 资产的状态，默认值为ASSET_NORMAL。 |

## Assets

type Assets = Array\<Asset>

表示[Asset](#asset)类型的数组。

**系统能力：** SystemCapability.DistributedDataManager.CommonType

| 类型                         | 说明                  |
| ---------------------------- | --------------------- |
| Array&lt;[Asset](#asset)&gt; | 表示Asset类型的数组。 |

## ValueType

type ValueType = null | number | string | boolean | Uint8Array | Asset | Assets

用于表示允许的数据字段类型，接口参数具体类型根据其功能而定。

**系统能力：** SystemCapability.DistributedDataManager.CommonType

| 类型       | 说明                                    |
| ---------- | --------------------------------------- |
| null       | 表示值类型为空。                        |
| number     | 表示值类型为数字。                      |
| string     | 表示值类型为字符串。                    |
| boolean    | 表示值类型为布尔值。                    |
| Uint8Array | 表示值类型为Uint8类型的数组。           |
| Asset      | 表示值类型为附件[Asset](#asset)。       |
| Assets     | 表示值类型为附件数组[Assets](#assets)。 |

## ValuesBucket

type ValuesBucket = Record<string, ValueType>

用于存储键值对的类型。该类型不是多线程安全的，如果应用中存在多线程同时操作该类派生出的实例，注意加锁保护。

**系统能力：** SystemCapability.DistributedDataManager.CommonType

| 类型 | 说明                  |
| ------ | ----------------------- |
| Record<string, [ValueType](#valuetype)> | 表示键值对类型。键的类型为string，值的类型为[ValueType](#valuetype)。|
