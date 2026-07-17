# Asset

记录资产附件（文件、图片、视频等类型文件）的相关信息。

**起始版本：** 11

<!--Device-commonType-interface Asset--><!--Device-commonType-interface Asset-End-->

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

<!--Device-Asset-createTime: string--><!--Device-Asset-createTime: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.CommonType

## modifyTime

```TypeScript
modifyTime: string
```

资产最后一次被修改的时间。

**类型：** string

**起始版本：** 11

<!--Device-Asset-modifyTime: string--><!--Device-Asset-modifyTime: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.CommonType

## name

```TypeScript
name: string
```

资产的名称。

**类型：** string

**起始版本：** 11

<!--Device-Asset-name: string--><!--Device-Asset-name: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.CommonType

## path

```TypeScript
path: string
```

资产在应用沙箱里的路径。

**类型：** string

**起始版本：** 11

<!--Device-Asset-path: string--><!--Device-Asset-path: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.CommonType

## size

```TypeScript
size: string
```

资产占用空间的大小。确保在全链路中保持统一、一致的存储格式与取值逻辑。建议所有系统节点均采用标准化处理方式（单位为字节（Byte），取值为非负整数）。

**类型：** string

**起始版本：** 11

<!--Device-Asset-size: string--><!--Device-Asset-size: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.CommonType

## status

```TypeScript
status?: AssetStatus
```

资产的状态，默认值为ASSET_NORMAL。

**类型：** AssetStatus

**起始版本：** 11

<!--Device-Asset-status?: AssetStatus--><!--Device-Asset-status?: AssetStatus-End-->

**系统能力：** SystemCapability.DistributedDataManager.CommonType

## uri

```TypeScript
uri: string
```

资产的uri，在系统里的绝对路径。

**类型：** string

**起始版本：** 11

<!--Device-Asset-uri: string--><!--Device-Asset-uri: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.CommonType

