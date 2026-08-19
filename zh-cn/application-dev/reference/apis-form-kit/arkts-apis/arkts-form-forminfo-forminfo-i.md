# FormInfo

卡片配置信息。

**起始版本：** 23

<!--Device-formInfo-interface FormInfo--><!--Device-formInfo-interface FormInfo-End-->

**系统能力：** SystemCapability.Ability.Form

## 导入模块

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## abilityName

```TypeScript
abilityName: string
```

卡片所属的Ability名称。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-abilityName: string--><!--Device-FormInfo-abilityName: string-End-->

**系统能力：** SystemCapability.Ability.Form

## bundleName

```TypeScript
bundleName: string
```

卡片所属包的Bundle名称。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-bundleName: string--><!--Device-FormInfo-bundleName: string-End-->

**系统能力：** SystemCapability.Ability.Form

## colorMode

```TypeScript
colorMode: ColorMode
```

卡片颜色模式。 **说明：** 从API version 9开始支持，从API version 20开始废弃。无替代接口。

**类型：** ColorMode

**起始版本：** 9

**废弃版本：** 20

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-colorMode: ColorMode--><!--Device-FormInfo-colorMode: ColorMode-End-->

**系统能力：** SystemCapability.Ability.Form

## customizeData

```TypeScript
customizeData: Record<string, string>
```

卡片用户数据。

**类型：** Record&lt;string, string&gt;

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-customizeData: Record<string, string>--><!--Device-FormInfo-customizeData: Record<string, string>-End-->

**系统能力：** SystemCapability.Ability.Form

## defaultDimension

```TypeScript
defaultDimension: int
```

卡片规格。具体可选规格参考[FormDimension](arkts-form-forminfo-formdimension-e.md)。 **说明：** 数值为[1, 9]的整数，数值5从API version 9开始支持，从API version 20开始废弃。超出范围时抛出异常。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-defaultDimension: int--><!--Device-FormInfo-defaultDimension: int-End-->

**系统能力：** SystemCapability.Ability.Form

## description

```TypeScript
description: string
```

卡片描述。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-description: string--><!--Device-FormInfo-description: string-End-->

**系统能力：** SystemCapability.Ability.Form

## descriptionId

```TypeScript
descriptionId: int
```

卡片描述ID。 **说明：** 数值为大于0小于2^32的整数。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-descriptionId: int--><!--Device-FormInfo-descriptionId: int-End-->

**系统能力：** SystemCapability.Ability.Form

## displayName

```TypeScript
displayName: string
```

卡片展示名称。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-displayName: string--><!--Device-FormInfo-displayName: string-End-->

**系统能力：** SystemCapability.Ability.Form

## displayNameId

```TypeScript
displayNameId: int
```

卡片预览时标识卡片名称的ID。 **说明：** 数值为大于0小于2^32的整数。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-displayNameId: int--><!--Device-FormInfo-displayNameId: int-End-->

**系统能力：** SystemCapability.Ability.Form

## formConfigAbility

```TypeScript
formConfigAbility: string
```

卡片配置Ability。指定长按卡片弹出的选择框内，编辑选项所对应的Ability。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-formConfigAbility: string--><!--Device-FormInfo-formConfigAbility: string-End-->

**系统能力：** SystemCapability.Ability.Form

## formVisibleNotify

```TypeScript
formVisibleNotify: boolean
```

卡片是否使能可见通知。 - true：通知卡片提供方可见状态变化。 - false：不通知卡片提供方可见状态变化。

**类型：** boolean

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-formVisibleNotify: boolean--><!--Device-FormInfo-formVisibleNotify: boolean-End-->

**系统能力：** SystemCapability.Ability.Form

## isDefault

```TypeScript
isDefault: boolean
```

卡片是否是默认卡片。 - true：默认卡片。 - false：非默认卡片。

**类型：** boolean

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-isDefault: boolean--><!--Device-FormInfo-isDefault: boolean-End-->

**系统能力：** SystemCapability.Ability.Form

## isDynamic

```TypeScript
isDynamic: boolean
```

卡片是否为动态卡片。 仅ArkTS卡片区分动静态卡片，JS卡片均为动态卡片。 - true：为动态卡片。 - false：为静态卡片。

**类型：** boolean

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-isDynamic: boolean--><!--Device-FormInfo-isDynamic: boolean-End-->

**系统能力：** SystemCapability.Ability.Form

## jsComponentName

```TypeScript
jsComponentName: string
```

JS卡片的组件名，仅当卡片类型为JS时有效。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-jsComponentName: string--><!--Device-FormInfo-jsComponentName: string-End-->

**系统能力：** SystemCapability.Ability.Form

## moduleName

```TypeScript
moduleName: string
```

卡片所属模块的模块名称。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-moduleName: string--><!--Device-FormInfo-moduleName: string-End-->

**系统能力：** SystemCapability.Ability.Form

## name

```TypeScript
name: string
```

卡片名称。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-name: string--><!--Device-FormInfo-name: string-End-->

**系统能力：** SystemCapability.Ability.Form

## scheduledUpdateTime

```TypeScript
scheduledUpdateTime: string
```

卡片更新时间。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-scheduledUpdateTime: string--><!--Device-FormInfo-scheduledUpdateTime: string-End-->

**系统能力：** SystemCapability.Ability.Form

## supportDimensions

```TypeScript
supportDimensions: Array<int>
```

卡片支持的规格。具体可选规格参考[FormDimension](arkts-form-forminfo-formdimension-e.md)。 **说明：** 最大长度为9，数值取值范围[1, 9]的整数的数组，数值5从API version 9开始支持，从API version 20开始废弃。超出范围时抛出异常。

**类型：** Array&lt;int&gt;

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-supportDimensions: Array<int>--><!--Device-FormInfo-supportDimensions: Array<int>-End-->

**系统能力：** SystemCapability.Ability.Form

## supportedShapes

```TypeScript
supportedShapes: Array<int>
```

卡片支持的形状。具体可选形状参考[FormShape&lt;sup&gt;12+&lt;/sup&gt;](arkts-form-forminfo-formshape-e.md) **说明：** 1代表方形，2代表圆形。

**类型：** Array&lt;int&gt;

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-supportedShapes: Array<int>--><!--Device-FormInfo-supportedShapes: Array<int>-End-->

**系统能力：** SystemCapability.Ability.Form

## transparencyEnabled

```TypeScript
transparencyEnabled: boolean
```

卡片是否支持设置背景透明度。 ArkTS卡片由用户配置决定是否支持，JS卡片均不支持。 - true：表示是透明卡片。 - false：表示不是透明卡片。

**类型：** boolean

**默认值：** false

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-transparencyEnabled: boolean--><!--Device-FormInfo-transparencyEnabled: boolean-End-->

**系统能力：** SystemCapability.Ability.Form

## type

```TypeScript
type: FormType
```

卡片类型。当前支持JS卡片、ArkTS卡片。 **说明：** 当卡片类型为JS时，isDynamic强制为true，transparencyEnabled不生效，jsComponentName为必填项。

**类型：** FormType

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-type: FormType--><!--Device-FormInfo-type: FormType-End-->

**系统能力：** SystemCapability.Ability.Form

## updateDuration

```TypeScript
updateDuration: int
```

卡片更新周期。 **说明：** 数值为[0, 336]的整数。超出范围时抛出异常。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-updateDuration: int--><!--Device-FormInfo-updateDuration: int-End-->

**系统能力：** SystemCapability.Ability.Form

## updateEnabled

```TypeScript
updateEnabled: boolean
```

卡片是否使能更新。 - true：表示支持周期性刷新。 - false：表示不支持周期性刷新。

**类型：** boolean

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-updateEnabled: boolean--><!--Device-FormInfo-updateEnabled: boolean-End-->

**系统能力：** SystemCapability.Ability.Form

