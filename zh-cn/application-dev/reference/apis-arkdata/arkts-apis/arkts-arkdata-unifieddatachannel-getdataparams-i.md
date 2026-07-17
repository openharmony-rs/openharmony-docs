# GetDataParams

表示从UDMF获取数据时的参数，包含目标路径、文件冲突选项、进度条类型等。

具体使用示例可见[拖拽异步获取数据]。

**起始版本：** 15

<!--Device-unifiedDataChannel-interface GetDataParams--><!--Device-unifiedDataChannel-interface GetDataParams-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## acceptableInfo

```TypeScript
acceptableInfo?: DataLoadInfo
```

定义接收方对数据类型和数据记录数量的接收能力。延迟加载场景下，发送方可根据此信息生成并返回更合适的数据内容。默认为空，不提供接收方数据接收能力。

**类型：** DataLoadInfo

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-GetDataParams-acceptableInfo?: DataLoadInfo--><!--Device-GetDataParams-acceptableInfo?: DataLoadInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## dataProgressListener

```TypeScript
dataProgressListener: DataProgressListener
```

表示获取统一数据时的进度和数据监听器。

**类型：** DataProgressListener

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-GetDataParams-dataProgressListener: DataProgressListener--><!--Device-GetDataParams-dataProgressListener: DataProgressListener-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## destUri

```TypeScript
destUri?: string
```

拷贝文件的目标路径。若不支持文件处理，则不需要设置此参数，默认为空；若支持文件处理，须设置一个已经存在的目录。若应用涉及复杂文件处理策略或需要区分文件多路径存储，建议不设置此参数，由应用自行完成文件copy处理。不填写时获取到的uri为源端路径URI，填写后获取到的uri为目标路径uri。

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-GetDataParams-destUri?: string--><!--Device-GetDataParams-destUri?: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## fileConflictOptions

```TypeScript
fileConflictOptions?: FileConflictOptions
```

定义文件拷贝冲突时的选项，默认为OVERWRITE。

**类型：** FileConflictOptions

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-GetDataParams-fileConflictOptions?: FileConflictOptions--><!--Device-GetDataParams-fileConflictOptions?: FileConflictOptions-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## progressIndicator

```TypeScript
progressIndicator: ProgressIndicator
```

定义进度条指示选项，可选择是否采用系统默认进度显示。

**类型：** ProgressIndicator

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-GetDataParams-progressIndicator: ProgressIndicator--><!--Device-GetDataParams-progressIndicator: ProgressIndicator-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

