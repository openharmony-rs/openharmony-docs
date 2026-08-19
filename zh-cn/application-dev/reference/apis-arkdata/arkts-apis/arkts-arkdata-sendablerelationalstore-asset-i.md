# Asset

记录资产附件（文件、图片、视频等类型文件）的相关信息。用于支持资产数据跨线程传递，继承自 lang.ISendable。资产类型的相关接口暂不支持Datashare。使用 [sendableRelationalStore.toSendableAsset](arkts-arkdata-sendablerelationalstore-tosendableasset-f.md)方法创建。

**继承/实现关系：** Asset extends lang.ISendable

**起始版本：** 12

<!--Device-sendableRelationalStore-interface Asset--><!--Device-sendableRelationalStore-interface Asset-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## 导入模块

```TypeScript
import { sendableRelationalStore } from '@kit.ArkData';
```

## createTime

```TypeScript
createTime: string
```

资产被创建出来的时间。

**类型：** string

**起始版本：** 12

<!--Device-Asset-createTime: string--><!--Device-Asset-createTime: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## modifyTime

```TypeScript
modifyTime: string
```

资产最后一次被修改的时间。

**类型：** string

**起始版本：** 12

<!--Device-Asset-modifyTime: string--><!--Device-Asset-modifyTime: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## name

```TypeScript
name: string
```

资产的名称。

**类型：** string

**起始版本：** 12

<!--Device-Asset-name: string--><!--Device-Asset-name: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## path

```TypeScript
path: string
```

资产在应用沙箱里的路径。

**类型：** string

**起始版本：** 12

<!--Device-Asset-path: string--><!--Device-Asset-path: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## size

```TypeScript
size: string
```

资产占用空间的大小。

**类型：** string

**起始版本：** 12

<!--Device-Asset-size: string--><!--Device-Asset-size: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## status

```TypeScript
status?: number
```

资产的状态，取值与[relationalStore.AssetStatus](arkts-arkdata-relationalstore-assetstatus-e.md)枚举值保持一致，默认值为 relationalStore.AssetStatus.ASSET_NORMAL。

**类型：** number

**起始版本：** 12

<!--Device-Asset-status?: number--><!--Device-Asset-status?: number-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## uri

```TypeScript
uri: string
```

资产的uri，在系统里的绝对路径。

**类型：** string

**起始版本：** 12

<!--Device-Asset-uri: string--><!--Device-Asset-uri: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

