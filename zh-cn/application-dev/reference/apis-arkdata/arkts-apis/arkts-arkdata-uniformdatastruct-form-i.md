# Form

系统定义的卡片类型数据，用于跨应用共享卡片信息。典型使用场景包括：卡片拖拽分享、卡片内容跨应用传输、桌面小组件数据共享等。

**起始版本：** 15

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

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## bundleName

```TypeScript
bundleName: string
```

卡片所属的bundle名，格式需符合应用包名规范。

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## details

```TypeScript
details?: Record<string, number | number | number | string | Uint8Array>
```

字典类型对象，key为string类型，value可包含number（数值类型）、string（字符串类型）或Uint8Array（二进制字节数组）类型数据。非必填字段，默认值为空字典对象。

**类型：** Record&lt;string, number \| number \| number \| string \| Uint8Array&gt;

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## formId

```TypeScript
formId: number
```

卡片id。

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## formName

```TypeScript
formName: string
```

卡片名。

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## module

```TypeScript
module: string
```

卡片所属的module名。

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## uniformDataType

```TypeScript
readonly uniformDataType: 'openharmony.form'
```

统一数据类型标识为卡片类型数据，固定为“openharmony.form”，数据类型描述信息见 [UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)。

**类型：** 'openharmony.form'

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**示例**

```TypeScript
import { unifiedDataChannel, uniformTypeDescriptor } from '@kit.ArkData';

let u8Array = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]);
let formDetails: Record<string, number | string | Uint8Array> = {
  'formKey1': 123,
  'formKey2': 'formValue',
  'formKey3': u8Array
};
let form: uniformDataStruct.Form = {
  uniformDataType: 'openharmony.form',
  formId: 1,
  formName: 'formName',
  bundleName: 'com.xx.app',
  abilityName: 'abilityName',
  module: 'module',
  details: formDetails
};
console.info('form.uniformDataType: ' + form.uniformDataType);
let record = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.OPENHARMONY_FORM, form);
```
