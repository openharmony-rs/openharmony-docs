# Audio

音频类型数据，是[File]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的子类，用于描述音频文件。

**继承/实现关系：** Audio extends [File](arkts-arkdata-unifieddatachannel-file-c.md)

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-unifiedDataChannel-class Audio extends File--><!--Device-unifiedDataChannel-class Audio extends File-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## audioUri

```TypeScript
set audioUri(value: string)
```

本地音频数据uri或网络音频uri，本地音频数据uri可通过[getUriFromPath]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_函数获取。

**类型：** string

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Audio-set audioUri(value: string)--><!--Device-Audio-set audioUri(value: string)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

