# SystemDefinedAppItem

```TypeScript
class SystemDefinedAppItem extends SystemDefinedRecord
```

系统定义的桌面图标类型数据，是[SystemDefinedRecord](arkts-arkdata-unifieddatachannel-systemdefinedrecord-c.md)的子类。

**继承/实现关系：** SystemDefinedAppItem extends [SystemDefinedRecord](arkts-arkdata-unifieddatachannel-systemdefinedrecord-c.md)

**起始版本：** 10

<!--Device-unifiedDataChannel-class SystemDefinedAppItem extends SystemDefinedRecord--><!--Device-unifiedDataChannel-class SystemDefinedAppItem extends SystemDefinedRecord-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## abilityName

```TypeScript
get abilityName(): string
```

图标对应的应用ability名。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-SystemDefinedAppItem-get abilityName(): string--><!--Device-SystemDefinedAppItem-get abilityName(): string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set abilityName(value: string)
```

图标对应的应用ability名。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-SystemDefinedAppItem-set abilityName(value: string)--><!--Device-SystemDefinedAppItem-set abilityName(value: string)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## appIconId

```TypeScript
get appIconId(): string
```

图标的图片id。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-SystemDefinedAppItem-get appIconId(): string--><!--Device-SystemDefinedAppItem-get appIconId(): string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set appIconId(value: string)
```

图标的图片id。This field can be sourced from BMS or customized as needed.

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-SystemDefinedAppItem-set appIconId(value: string)--><!--Device-SystemDefinedAppItem-set appIconId(value: string)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## appId

```TypeScript
get appId(): string
```

图标对应的应用id。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-SystemDefinedAppItem-get appId(): string--><!--Device-SystemDefinedAppItem-get appId(): string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set appId(value: string)
```

图标对应的应用id。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-SystemDefinedAppItem-set appId(value: string)--><!--Device-SystemDefinedAppItem-set appId(value: string)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## appLabelId

```TypeScript
get appLabelId(): string
```

图标名称对应的标签id。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-SystemDefinedAppItem-get appLabelId(): string--><!--Device-SystemDefinedAppItem-get appLabelId(): string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set appLabelId(value: string)
```

图标名称对应的标签id。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-SystemDefinedAppItem-set appLabelId(value: string)--><!--Device-SystemDefinedAppItem-set appLabelId(value: string)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## appName

```TypeScript
get appName(): string
```

图标对应的应用名。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-SystemDefinedAppItem-get appName(): string--><!--Device-SystemDefinedAppItem-get appName(): string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set appName(value: string)
```

图标对应的应用名。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-SystemDefinedAppItem-set appName(value: string)--><!--Device-SystemDefinedAppItem-set appName(value: string)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## bundleName

```TypeScript
get bundleName(): string
```

图标对应的应用bundle名。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-SystemDefinedAppItem-get bundleName(): string--><!--Device-SystemDefinedAppItem-get bundleName(): string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set bundleName(value: string)
```

图标对应的应用bundle名。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-SystemDefinedAppItem-set bundleName(value: string)--><!--Device-SystemDefinedAppItem-set bundleName(value: string)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core
