# File

File类型数据，是[UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md#UnifiedRecord)的子类，也是文件类型数据的基类，用于描述文件类型数据，推荐开发者优先使用File的子类描述数据，如 [Image](arkts-arkdata-unifieddatachannel-image-c.md#Image)、[Video](arkts-arkdata-unifieddatachannel-video-c.md#Video)、 [Folder](arkts-arkdata-unifieddatachannel-folder-c.md#Folder)等具体子类。

**继承/实现关系：** File extends [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md#UnifiedRecord)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unifiedDataChannel-class File--><!--Device-unifiedDataChannel-class File-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## details

```TypeScript
details?: Record<string, string>
```

是一个字典类型对象，key和value都是string类型，用于描述文件相关信息。例如，可生成一个details内容为 { "name":"文件名", "type":"文件类型" } 的数据对象，用于描述一个文件。非必填字段，默认值为空字典对象。

**类型：** Record&lt;string, string&gt;

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-File-details?: Record<string, string>--><!--Device-File-details?: Record<string, string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

