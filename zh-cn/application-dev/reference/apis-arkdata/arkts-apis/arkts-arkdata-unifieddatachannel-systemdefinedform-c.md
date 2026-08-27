# SystemDefinedForm

系统定义的桌面卡片类型数据，是[SystemDefinedRecord](arkts-arkdata-unifieddatachannel-systemdefinedrecord-c.md)的子类。

**继承/实现关系：** SystemDefinedForm extends [SystemDefinedRecord](arkts-arkdata-unifieddatachannel-systemdefinedrecord-c.md)

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## abilityName

```TypeScript
set abilityName(value: string)
```

卡片对应的ability名。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## bundleName

```TypeScript
set bundleName(value: string)
```

卡片所属的bundle名。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## formId

```TypeScript
set formId(value: number)
```

卡片id。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## formName

```TypeScript
set formName(value: string)
```

卡片名称。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## module

```TypeScript
set module(value: string)
```

卡片所属的module名。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**示例**

```TypeScript
let form = new unifiedDataChannel.SystemDefinedForm();
form.formId = 123456;
form.formName = 'MyFormName';
form.bundleName = 'MyBundleName';
form.abilityName = 'MyAbilityName';
form.module = 'MyModule';
let u8Array = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]);
form.details = {
  formKey1: 123,
  formKey2: 'formValue',
  formKey3: u8Array
};
let unifiedData = new unifiedDataChannel.UnifiedData(form);
```
