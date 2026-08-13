# Asset

记录资产附件（文件、图片、视频等类型文件）的相关信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-relationalStore-interface Asset--><!--Device-relationalStore-interface Asset-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## createTime

```TypeScript
createTime: string
```

资产被创建出来的时间。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Asset-createTime: string--><!--Device-Asset-createTime: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## modifyTime

```TypeScript
modifyTime: string
```

资产最后一次被修改的时间。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Asset-modifyTime: string--><!--Device-Asset-modifyTime: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## name

```TypeScript
name: string
```

资产的名称，长度不超过256字节。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Asset-name: string--><!--Device-Asset-name: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## path

```TypeScript
path: string
```

资产在应用沙箱里的路径，路径长度不超过1024字节。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Asset-path: string--><!--Device-Asset-path: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## size

```TypeScript
size: string
```

资产占用空间的大小。在端云同步机制中，本字段作为判定资产是否发生变更的关键依据之一，需确保在全链路中保持统一、一致的存储格式与取值逻辑。建议所有系统节点均采用标准化处理方式（单位为字节（Byte），取值为非负整数），避免因格式 差异导致同步异常或误判。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Asset-size: string--><!--Device-Asset-size: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## status

```TypeScript
status?: AssetStatus
```

资产的状态，默认值为ASSET_NORMAL。

**类型：** AssetStatus

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Asset-status?: AssetStatus--><!--Device-Asset-status?: AssetStatus-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## uri

```TypeScript
uri: string
```

资产的uri，在系统里的绝对路径，路径长度不超过1024字节。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Asset-uri: string--><!--Device-Asset-uri: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

