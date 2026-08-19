# RunningFormInfo（系统接口）

已经添加到桌面的卡片信息。

**起始版本：** 23

<!--Device-formInfo-interface RunningFormInfo--><!--Device-formInfo-interface RunningFormInfo-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

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

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-RunningFormInfo-readonly abilityName: string--><!--Device-RunningFormInfo-readonly abilityName: string-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
readonly bundleName: string
```

卡片提供方所属包的Bundle名称，用于定位卡片提供方应用。

**类型：** string

**默认值：** -

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-RunningFormInfo-readonly bundleName: string--><!--Device-RunningFormInfo-readonly bundleName: string-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## dimension

```TypeScript
readonly dimension: int
```

卡片尺寸，用于标识卡片的大小规格。取值及其对应含义请参考[FormDimension](arkts-form-forminfo-formdimension-e.md)。 **说明：** 取值范围[1, 9]的整数，数值5从API version 9开始支持，从API version 20开始废弃。

**类型：** int

**默认值：** -

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-RunningFormInfo-readonly dimension: int--><!--Device-RunningFormInfo-readonly dimension: int-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## extraData

```TypeScript
readonly extraData?: Record<string, Object>
```

卡片的额外数据。

**类型：** Record&lt;string, Object&gt;

**默认值：** -

**起始版本：** 23

<!--Device-RunningFormInfo-readonly extraData?: Record<string, Object>--><!--Device-RunningFormInfo-readonly extraData?: Record<string, Object>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## formDescription

```TypeScript
readonly formDescription: string
```

提供方卡片配置文件中的描述信息。

**类型：** string

**起始版本：** 23

<!--Device-RunningFormInfo-readonly formDescription: string--><!--Device-RunningFormInfo-readonly formDescription: string-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## formId

```TypeScript
readonly formId: string
```

卡片唯一标识，用于识别和管理已添加到桌面的卡片实例。

**类型：** string

**默认值：** -

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-RunningFormInfo-readonly formId: string--><!--Device-RunningFormInfo-readonly formId: string-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## formLocation

```TypeScript
readonly formLocation: FormLocation
```

卡片位置信息，用于标识卡片当前所在的位置（如桌面、卡片中心等）。

**类型：** [FormLocation](arkts-form-forminfo-formlocation-e.md)

**默认值：** -

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-RunningFormInfo-readonly formLocation: FormLocation--><!--Device-RunningFormInfo-readonly formLocation: FormLocation-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## formName

```TypeScript
readonly formName: string
```

卡片名称，用于标识和区分同一模块中的不同卡片。

**类型：** string

**默认值：** -

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-RunningFormInfo-readonly formName: string--><!--Device-RunningFormInfo-readonly formName: string-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## formUsageState

```TypeScript
readonly formUsageState: FormUsageState
```

卡片当前使用状态枚举。默认值为FormUsageState.USED

**类型：** [FormUsageState](arkts-form-forminfo-formusagestate-e-sys.md)

**默认值：** FormUsageState.USED

**起始版本：** 23

<!--Device-RunningFormInfo-readonly formUsageState: FormUsageState--><!--Device-RunningFormInfo-readonly formUsageState: FormUsageState-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## hostBundleName

```TypeScript
readonly hostBundleName: string
```

使用方卡片所属包的Bundle名称。

**类型：** string

**默认值：** -

**起始版本：** 23

<!--Device-RunningFormInfo-readonly hostBundleName: string--><!--Device-RunningFormInfo-readonly hostBundleName: string-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## moduleName

```TypeScript
readonly moduleName: string
```

卡片所属模块的名称，用于定位卡片提供方的具体模块。

**类型：** string

**默认值：** -

**起始版本：** 23

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-RunningFormInfo-readonly moduleName: string--><!--Device-RunningFormInfo-readonly moduleName: string-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## visibilityType

```TypeScript
readonly visibilityType: VisibilityType
```

卡片当前可见类型枚举。

**类型：** [VisibilityType](arkts-form-forminfo-visibilitytype-e.md)

**默认值：** -

**起始版本：** 23

<!--Device-RunningFormInfo-readonly visibilityType: VisibilityType--><!--Device-RunningFormInfo-readonly visibilityType: VisibilityType-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

