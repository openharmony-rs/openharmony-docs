# File

File类型数据，是[UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md)的子类，也是文件类型数据的基类，用于描述文件类型数据，推荐开发者优先使用File的子类描述数据，如[Image](arkts-arkdata-unifieddatachannel-image-c.md)、[Video](arkts-arkdata-unifieddatachannel-video-c.md)、[Folder](arkts-arkdata-unifieddatachannel-folder-c.md)等具体子类。

**继承/实现关系：** File extends [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md)

**起始版本：** 10

<!--Device-unifiedDataChannel-class File extends UnifiedRecord--><!--Device-unifiedDataChannel-class File extends UnifiedRecord-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## details

```TypeScript
details?: Record<string, string>
```

是一个字典类型对象，key和value都是string类型，用于描述文件相关信息。例如，可生成一个details内容为

{

"name":"文件名",

"type":"文件类型"

}

的数据对象，用于描述一个文件。非必填字段，默认值为空字典对象。

**类型：** Record<string, string>

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-File-details?: Record<string, string>--><!--Device-File-details?: Record<string, string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## uri

```TypeScript
set uri(value: string)
```

表示统一文件的详细信息。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-File-set uri(value: string)--><!--Device-File-set uri(value: string)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## uriAuthorizationPolicies

```TypeScript
set uriAuthorizationPolicies(value: Array<UriPermission> | undefined)
```

用于拖拽场景的URI授权策略。默认值为READ+WRITE+PERSIST（读+写+持久化授权），只针对单个record使用，优先级最高，具体策略见[UriPermission](arkts-arkdata-unifieddatachannel-uripermission-e.md)。

**类型：** Array<UriPermission>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-File-set uriAuthorizationPolicies(value: Array<UriPermission> | undefined)--><!--Device-File-set uriAuthorizationPolicies(value: Array<UriPermission> | undefined)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

