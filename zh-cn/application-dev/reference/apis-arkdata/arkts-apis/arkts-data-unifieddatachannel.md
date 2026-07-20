# @ohos.data.unifiedDataChannel

本模块为统一数据管理框架（Unified Data Management Framework，UDMF）的组成部分，针对多对多跨应用数据共享的不同业务场景提供了标准化的数据通路，提供了标准化的数据接入与读取接口。同时对文本、图片等数据类型提供了标准化定义，方便不同应用间进行数据交互，减少数据类型适配的工作量。

**设计逻辑：** UDMF采用统一数据模型，将不同类型的数据封装为UnifiedData对象，通过Intention标识不同的数据通路类型（如DATA_HUB、DRAG等），实现跨应用数据共享。数据写入时生成唯一标识符key，数据读取时通过key或intention查询获取。

UDMF处理数据时，不会解析用户数据的内容，存储路径安全性较低，不建议传输个人敏感数据和隐私数据。

**起始版本：** 10

<!--Device-unnamed-declare namespace unifiedDataChannel--><!--Device-unnamed-declare namespace unifiedDataChannel-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [convertRecordsToEntries](arkts-arkdata-unifieddatachannel-convertrecordstoentries-f.md#convertrecordstoentries) | 本接口用于将传入的data转换成多样式数据结构。若原data使用多个record去承载同一份数据的不同数据格式，则可以使用此接口将原data转换为多样式数据结构。  当满足以下规则时进行转换，传入的data经转换后变为多样式数据结构：  1. data中的record数量大于1；2. data中的properties中的tag值为"records_to_entries_data_format"。  否则不会产生任何行为。 |
| [deleteData](arkts-arkdata-unifieddatachannel-deletedata-f.md#deletedata) | 删除UDMF公共数据通路的数据，返回删除的数据集，使用callback异步回调。 |
| [deleteData](arkts-arkdata-unifieddatachannel-deletedata-f.md#deletedata-1) | 删除UDMF公共数据通路的数据，返回删除的数据集，使用Promise异步回调。 |
| [insertData](arkts-arkdata-unifieddatachannel-insertdata-f.md#insertdata) | 将数据写入UDMF的公共数据通路中，并生成数据的唯一标识符，使用callback异步回调。  **实现机制：** 系统接收UnifiedData对象后，验证数据完整性并序列化存储。根据intention值路由到对应存储空间，生成唯一标识符key。数据在公共数据通路中由系统管理有效期，默认策略为应用退出后自动清理。 |
| [insertData](arkts-arkdata-unifieddatachannel-insertdata-f.md#insertdata-1) | 将数据写入UDMF的公共数据通路中，并生成数据的唯一标识符，使用Promise异步回调。 |
| [queryData](arkts-arkdata-unifieddatachannel-querydata-f.md#querydata) | 查询UDMF公共数据通路的数据，使用callback异步回调。 |
| [queryData](arkts-arkdata-unifieddatachannel-querydata-f.md#querydata-1) | 查询UDMF公共数据通路的数据，使用Promise异步回调。 |
| [updateData](arkts-arkdata-unifieddatachannel-updatedata-f.md#updatedata) | 更新已写入UDMF的公共数据通路的数据，使用callback异步回调。 |
| [updateData](arkts-arkdata-unifieddatachannel-updatedata-f.md#updatedata-1) | 更新已写入UDMF的公共数据通路的数据，使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [removeAppShareOptions](arkts-arkdata-unifieddatachannel-removeappshareoptions-f-sys.md#removeappshareoptions) | 清除[setAppShareOptions](arkts-arkdata-unifieddatachannel-setappshareoptions-f-sys.md#setappshareoptions-1)设置的管控信息。调用成功后，setAppShareOptions设置的管控信息被清除，应用内拖拽通道数据恢复到默认使用范围。 |
| [setAppShareOptions](arkts-arkdata-unifieddatachannel-setappshareoptions-f-sys.md#setappshareoptions) | 设置应用内拖拽通道数据可使用的范围[ShareOptions](arkts-arkdata-unifieddatachannel-shareoptions-e.md)，目前仅支持DRAG类型数据通道的管控设置。调用成功后，应用内拖拽通道数据的使用范围被设置为指定的ShareOptions值。 |
<!--DelEnd-->

### 类

| 名称 | 说明 |
| --- | --- |
| [ApplicationDefinedRecord](arkts-arkdata-unifieddatachannel-applicationdefinedrecord-c.md) | ApplicationDefinedRecord是[UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md)的子类，也是应用自定义数据类型的基类，用于描述仅在应用生态内部流通的自定义数据类型，应用可基于此类进行自定义数据类型的扩展。 |
| [Audio](arkts-arkdata-unifieddatachannel-audio-c.md) | 音频类型数据，是[File](arkts-arkdata-unifieddatachannel-file-c.md)的子类，用于描述音频文件。 |
| [File](arkts-arkdata-unifieddatachannel-file-c.md) | File类型数据，是[UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md)的子类，也是文件类型数据的基类，用于描述文件类型数据，推荐开发者优先使用File的子类描述数据，如[Image](arkts-arkdata-unifieddatachannel-image-c.md)、[Video](arkts-arkdata-unifieddatachannel-video-c.md)、[Folder](arkts-arkdata-unifieddatachannel-folder-c.md)等具体子类。 |
| [Folder](arkts-arkdata-unifieddatachannel-folder-c.md) | 文件夹类型数据，是[File](arkts-arkdata-unifieddatachannel-file-c.md)的子类，用于描述文件夹。 |
| [HTML](arkts-arkdata-unifieddatachannel-html-c.md) | HTML类型数据，是[Text](arkts-arkdata-unifieddatachannel-text-c.md)的子类，用于描述超文本标记语言数据。 |
| [Hyperlink](arkts-arkdata-unifieddatachannel-hyperlink-c.md) | [Text](arkts-arkdata-unifieddatachannel-text-c.md)的子类，用于描述超链接类型数据。 |
| [Image](arkts-arkdata-unifieddatachannel-image-c.md) | 图片类型数据，是[File](arkts-arkdata-unifieddatachannel-file-c.md)的子类，用于描述图片文件。 |
| [PlainText](arkts-arkdata-unifieddatachannel-plaintext-c.md) | [Text](arkts-arkdata-unifieddatachannel-text-c.md)的子类，用于描述纯文本类数据。 |
| [Summary](arkts-arkdata-unifieddatachannel-summary-c.md) | 描述统一数据对象的数据摘要，包括数据类型和大小。 |
| [SystemDefinedAppItem](arkts-arkdata-unifieddatachannel-systemdefinedappitem-c.md) | 系统定义的桌面图标类型数据，是[SystemDefinedRecord](arkts-arkdata-unifieddatachannel-systemdefinedrecord-c.md)的子类。 |
| [SystemDefinedForm](arkts-arkdata-unifieddatachannel-systemdefinedform-c.md) | 系统定义的桌面卡片类型数据，是[SystemDefinedRecord](arkts-arkdata-unifieddatachannel-systemdefinedrecord-c.md)的子类。 |
| [SystemDefinedPixelMap](arkts-arkdata-unifieddatachannel-systemdefinedpixelmap-c.md) | 与系统侧定义的[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)数据类型对应的图片数据类型，是[SystemDefinedRecord](arkts-arkdata-unifieddatachannel-systemdefinedrecord-c.md)的子类，仅保存PixelMap的二进制数据。 |
| [SystemDefinedRecord](arkts-arkdata-unifieddatachannel-systemdefinedrecord-c.md) | SystemDefinedRecord是[UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md)的子类，也是OpenHarmony系统特有数据类型的基类，用于描述仅在OpenHarmony系统范围内流通的特有数据类型，推荐开发者优先使用SystemDefinedRecord的子类描述数据，如[SystemDefinedForm](arkts-arkdata-unifieddatachannel-systemdefinedform-c.md)、[SystemDefinedAppItem](arkts-arkdata-unifieddatachannel-systemdefinedappitem-c.md)、[SystemDefinedPixelMap](arkts-arkdata-unifieddatachannel-systemdefinedpixelmap-c.md)等具体子类。 |
| [Text](arkts-arkdata-unifieddatachannel-text-c.md) | 文本类型数据，是[UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md)的子类，也是文本类型数据的基类，用于描述文本类数据，推荐开发者优先使用Text的子类描述数据，如[PlainText](arkts-arkdata-unifieddatachannel-plaintext-c.md)、[Hyperlink](arkts-arkdata-unifieddatachannel-hyperlink-c.md)、[HTML](arkts-arkdata-unifieddatachannel-html-c.md)等具体子类。 |
| [UnifiedData](arkts-arkdata-unifieddatachannel-unifieddata-c.md) | 表示UDMF统一数据对象，提供封装一组数据记录的方法。 |
| [UnifiedDataProperties](arkts-arkdata-unifieddatachannel-unifieddataproperties-c.md) | 定义统一数据对象中所有数据记录的属性，包含时间戳、标签、粘贴范围以及一些附加数据等。 |
| [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md) | 对UDMF支持的数据内容的抽象定义，称为数据记录。一个统一数据对象内包含一条或多条数据记录，例如一条文本记录、一条图片记录、一条HTML记录等。从API version 15开始，支持往数据记录中增加同一内容的不同数据格式（例如同一文本可同时以纯文本、HTML或超链接等格式存储），数据使用方根据业务需要通过getEntry方法获取对应格式。 |
| [Video](arkts-arkdata-unifieddatachannel-video-c.md) | 视频类型数据，是[File](arkts-arkdata-unifieddatachannel-file-c.md)的子类，用于描述视频文件。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [DataLoadInfo](arkts-arkdata-unifieddatachannel-dataloadinfo-i.md) | 用于描述被加载数据的类型与数量。  - 在**数据发送方**中使用，表示实际可提供的数据范围，必须设置该字段。  - 在**数据接收方**中使用，表示期望加载的数据类型与数量，可根据需要设置该字段。 |
| [DataLoadParams](arkts-arkdata-unifieddatachannel-dataloadparams-i.md) | 用于在延迟加载场景下描述发送方的数据加载策略。  当同时传入loadHandler和delayedDataLoadHandler时，优先使用delayedDataLoadHandler，loadHandler不生效。 |
| [GetDataParams](arkts-arkdata-unifieddatachannel-getdataparams-i.md) | 表示从UDMF获取数据时的参数，包含目标路径、文件冲突选项、进度条类型等。  具体使用示例可见[拖拽异步获取数据]。 |
| [Options](arkts-arkdata-unifieddatachannel-options-i.md) | UDMF提供的数据操作接口包含三个可选参数：intention、key和visibility。如果接口不需要这些参数，可以不填，具体要求请参阅该接口的参数说明。 |
| [ProgressInfo](arkts-arkdata-unifieddatachannel-progressinfo-i.md) | 定义进度上报的数据。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [FileConflictOptions](arkts-arkdata-unifieddatachannel-fileconflictoptions-e.md) | 表示文件拷贝冲突时的可选策略的枚举。 |
| [Intention](arkts-arkdata-unifieddatachannel-intention-e.md) | UDMF已经支持的数据通路枚举类型。其主要用途是标识各种UDMF数据通路所面向的不同业务场景。 |
| [ListenerStatus](arkts-arkdata-unifieddatachannel-listenerstatus-e.md) | 表示从UDMF获取数据时的状态码的枚举。 |
| [ProgressIndicator](arkts-arkdata-unifieddatachannel-progressindicator-e.md) | 表示进度条指示选项的枚举，可选择是否采用系统默认进度显示。 |
| [ShareOptions](arkts-arkdata-unifieddatachannel-shareoptions-e.md) | UDMF支持的设备内使用范围类型枚举。 |
| [UriPermission](arkts-arkdata-unifieddatachannel-uripermission-e.md) | 拖拽场景下的URI授权策略。 |
| [Visibility](arkts-arkdata-unifieddatachannel-visibility-e.md) | 表示数据的可见性等级枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Intention](arkts-arkdata-unifieddatachannel-intention-e-sys.md) | UDMF已经支持的数据通路枚举类型。其主要用途是标识各种UDMF数据通路所面向的不同业务场景。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [DataLoadHandler](arkts-arkdata-unifieddatachannel-dataloadhandler-t.md) | 用于延迟加载数据的处理函数。支持数据发送方根据接收方传入的信息，动态生成数据，实现更灵活、精准的数据交互策略。  该处理函数为同步函数，适用于处理简单业务逻辑，若函数业务逻辑较复杂、执行时间较长（3s以上），推荐使用异步处理函数[DelayedDataLoadHandler](arkts-arkdata-unifieddatachannel-delayeddataloadhandler-t.md)。 |
| [DataProgressListener](arkts-arkdata-unifieddatachannel-dataprogresslistener-t.md) | 定义获取进度信息和数据的监听回调函数。 |
| [DelayedDataLoadHandler](arkts-arkdata-unifieddatachannel-delayeddataloadhandler-t.md) | 用于延迟加载数据的处理函数。支持数据发送方根据接收方传入的信息，动态生成数据，实现更灵活、精准的数据交互策略。  该处理函数为异步函数，返回Promise对象，不阻塞主线程，可处理复杂业务逻辑、执行长耗时任务。 |
| [GetDelayData](arkts-arkdata-unifieddatachannel-getdelaydata-t.md) | 对UnifiedData的延迟封装，支持延迟获取数据。当数据接收方请求特定类型数据时，系统会触发此回调函数，数据发送方可在回调中动态生成数据，而非提前准备所有数据。当前只支持同设备剪贴板场景。 |
| [ValueType](arkts-arkdata-unifieddatachannel-valuetype-t.md) | 用于表示统一数据记录允许的数据字段类型。 |

