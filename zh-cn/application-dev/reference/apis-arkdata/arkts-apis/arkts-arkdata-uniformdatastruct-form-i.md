# Form

系统定义的卡片类型数据，用于跨应用共享卡片信息。典型使用场景包括：卡片拖拽分享、卡片内容跨应用传输、桌面小组件数据共享等。

**起始版本：** 15

<!--Device-uniformDataStruct-interface Form--><!--Device-uniformDataStruct-interface Form-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## abilityName

```TypeScript
abilityName: string
```

卡片对应的ability名。建议遵循Ability组件命名规范：取值为长度不超过127字节的字符串，以字母开头，可包含字母、数字、下划线（_）或点号（.）；确保该名称在整个应用中唯一。推荐使用"包名.Ability名"格式（如"com.example.myapplication.MainAbility"）。

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Form-abilityName: string--><!--Device-Form-abilityName: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## bundleName

```TypeScript
bundleName: string
```

卡片所属的bundle名，格式需符合应用包名规范。

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Form-bundleName: string--><!--Device-Form-bundleName: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## details

```TypeScript
details?: Record<string, number | number | number | string | Uint8Array>
```

字典类型对象，key为string类型，value可包含number（数值类型）、string（字符串类型）或Uint8Array（二进制字节数组）类型数据。非必填字段，默认值为空字典对象。

**类型：** Record&lt;string, number \| number \| number \| string \| Uint8Array&gt;

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Form-details?: Record<string, int | long | double | string | Uint8Array>--><!--Device-Form-details?: Record<string, int | long | double | string | Uint8Array>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## formId

```TypeScript
formId: number
```

卡片id。

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Form-formId: int--><!--Device-Form-formId: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## formName

```TypeScript
formName: string
```

卡片名。

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Form-formName: string--><!--Device-Form-formName: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## module

```TypeScript
module: string
```

卡片所属的module名。

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Form-module: string--><!--Device-Form-module: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## uniformDataType

```TypeScript
readonly uniformDataType: 'openharmony.form'
```

统一数据类型标识为卡片类型数据，固定为“openharmony.form”，数据类型描述信息见[UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)。

**类型：** 'openharmony.form'

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Form-readonly uniformDataType: 'openharmony.form'--><!--Device-Form-readonly uniformDataType: 'openharmony.form'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

