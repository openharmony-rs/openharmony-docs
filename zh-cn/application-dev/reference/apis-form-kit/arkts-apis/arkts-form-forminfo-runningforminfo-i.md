# RunningFormInfo

已经添加到桌面的卡片信息。

**起始版本：** 20

**系统能力：** SystemCapability.Ability.Form

## 导入模块

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## abilityName

```TypeScript
readonly abilityName: string
```

卡片所属的Ability名称，用于定位卡片提供方的具体Ability组件。

**类型：** string

**默认值：** -

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

## bundleName

```TypeScript
readonly bundleName: string
```

卡片提供方所属包的Bundle名称，用于定位卡片提供方应用。

**类型：** string

**默认值：** -

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

## dimension

```TypeScript
readonly dimension: number
```

卡片尺寸，用于标识卡片的大小规格。取值及其对应含义请参考[FormDimension](arkts-form-forminfo-formdimension-e.md)。  
**说明：** 取值范围[1, 9]的整数，数值5从API version 9开始支持，从API version 20开始废弃。

**类型：** number

**默认值：** -

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

## formId

```TypeScript
readonly formId: string
```

卡片唯一标识，用于识别和管理已添加到桌面的卡片实例。

**类型：** string

**默认值：** -

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

## formLocation

```TypeScript
readonly formLocation: FormLocation
```

卡片位置信息，用于标识卡片当前所在的位置（如桌面、卡片中心等）。

**类型：** [FormLocation](arkts-form-forminfo-formlocation-e.md)

**默认值：** -

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

## formName

```TypeScript
readonly formName: string
```

卡片名称，用于标识和区分同一模块中的不同卡片。

**类型：** string

**默认值：** -

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

## moduleName

```TypeScript
readonly moduleName: string
```

卡片所属模块的名称，用于定位卡片提供方的具体模块。

**类型：** string

**默认值：** -

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form
