# UnifiedDataProperties

定义统一数据对象中所有数据记录的属性，包含时间戳、标签、粘贴范围以及一些附加数据等。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## getDelayData

```TypeScript
getDelayData?: GetDelayData
```

延迟获取数据回调。当前只支持同设备剪贴板场景，当用户从剪贴板读取数据时触发该回调。非必填字段，默认值为undefined。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## extras

```TypeScript
extras?: Record<string, object>
```

是一个字典类型对象，用于设置其他附加属性数据。非必填字段，默认值为空字典对象。

**类型：** Record&lt;string, object&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## shareOptions

```TypeScript
shareOptions?: ShareOptions
```

指示[UnifiedData](arkts-arkdata-unifieddatachannel-unifieddata-c.md)支持的设备内使用范围，非必填字段，默认值为CROSS_APP。

**类型：** [ShareOptions](arkts-arkdata-unifieddatachannel-shareoptions-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## tag

```TypeScript
tag?: string
```

用户自定义标签。非必填字段，默认值为空字符串。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## timestamp

```TypeScript
readonly timestamp?: Date
```

[UnifiedData](arkts-arkdata-unifieddatachannel-unifieddata-c.md)的生成时间戳。默认值为1970年1月1日（UTC）。

**类型：** Date

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## uriAuthorizationPolicies

```TypeScript
uriAuthorizationPolicies?: Array<UriPermission>
```

用于拖拽场景的URI授权策略。默认值为READ+WRITE+PERSIST，只对单次数据生效，优先级较低，具体策略见[UriPermission](arkts-arkdata-unifieddatachannel-uripermission-e.md)。

**类型：** Array&lt;[UriPermission](arkts-arkdata-unifieddatachannel-uripermission-e.md)&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core
