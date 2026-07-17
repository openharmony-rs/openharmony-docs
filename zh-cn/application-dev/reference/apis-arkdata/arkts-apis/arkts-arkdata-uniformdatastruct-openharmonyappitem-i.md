# OpenHarmonyAppItem

系统定义的桌面图标类型数据，用于跨应用共享桌面图标信息。典型使用场景包括：桌面启动器拖拽图标、应用商店分享应用图标或创建快捷方式等。

**起始版本：** 12

<!--Device-uniformDataStruct-interface OpenHarmonyAppItem--><!--Device-uniformDataStruct-interface OpenHarmonyAppItem-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## abilityName

```TypeScript
abilityName: string
```

图标对应的应用ability名。建议遵循Ability组件命名规范：取值为长度不超过127字节的字符串，以字母开头，可包含字母、数字、下划线（_）或点号（.）；确保该名称在整个应用中唯一。推荐使用"包名.Ability名"格式（如"com.example.myapplication.MainAbility"）。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OpenHarmonyAppItem-abilityName: string--><!--Device-OpenHarmonyAppItem-abilityName: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## appIconId

```TypeScript
appIconId: string
```

图标的图片id。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OpenHarmonyAppItem-appIconId: string--><!--Device-OpenHarmonyAppItem-appIconId: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## appId

```TypeScript
appId: string
```

图标对应的应用id。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OpenHarmonyAppItem-appId: string--><!--Device-OpenHarmonyAppItem-appId: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## appLabelId

```TypeScript
appLabelId: string
```

图标名称对应的标签id。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OpenHarmonyAppItem-appLabelId: string--><!--Device-OpenHarmonyAppItem-appLabelId: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## appName

```TypeScript
appName: string
```

图标对应的应用名。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OpenHarmonyAppItem-appName: string--><!--Device-OpenHarmonyAppItem-appName: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## bundleName

```TypeScript
bundleName: string
```

图标对应的应用bundle名，格式需符合应用包名规范。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OpenHarmonyAppItem-bundleName: string--><!--Device-OpenHarmonyAppItem-bundleName: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## details

```TypeScript
details?: Record<string, number | number | number | string | Uint8Array>
```

字典类型对象，key为string类型，value可包含number（数值类型）、string（字符串类型）或Uint8Array（二进制字节数组）类型数据。非必填字段，默认值为空字典对象。

**类型：** Record<string, number | number | number | string | Uint8Array>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OpenHarmonyAppItem-details?: Record<string, int | long | double | string | Uint8Array>--><!--Device-OpenHarmonyAppItem-details?: Record<string, int | long | double | string | Uint8Array>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## uniformDataType

```TypeScript
readonly uniformDataType: 'openharmony.app-item'
```

统一数据类型标识为桌面图标类型数据，固定为“openharmony.app-item”，数据类型描述信息见[UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)。

**类型：** 'openharmony.app-item'

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OpenHarmonyAppItem-readonly uniformDataType: 'openharmony.app-item'--><!--Device-OpenHarmonyAppItem-readonly uniformDataType: 'openharmony.app-item'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

