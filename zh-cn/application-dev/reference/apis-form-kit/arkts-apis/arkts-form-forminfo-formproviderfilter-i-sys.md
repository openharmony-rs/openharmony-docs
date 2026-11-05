# FormProviderFilter（系统接口）

```TypeScript
interface FormProviderFilter
```

卡片提供方信息。

**起始版本：** 10

<!--Device-formInfo-interface FormProviderFilter--><!--Device-formInfo-interface FormProviderFilter-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## abilityName

```TypeScript
abilityName ?: string
```

卡片所属的Ability名称。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FormProviderFilter-abilityName ?: string--><!--Device-FormProviderFilter-abilityName ?: string-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string
```

提供方卡片所属包的Bundle名称。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FormProviderFilter-bundleName: string--><!--Device-FormProviderFilter-bundleName: string-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## formName

```TypeScript
formName ?: string
```

卡片名称。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FormProviderFilter-formName ?: string--><!--Device-FormProviderFilter-formName ?: string-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## isUnusedIncluded

```TypeScript
isUnusedIncluded?: boolean
```

是否包含未使用的卡片。

- true：包含未使用的卡片。

- false：不包含未使用的卡片。

默认值：false。

**类型：** boolean

**默认值：** false

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FormProviderFilter-isUnusedIncluded?: boolean--><!--Device-FormProviderFilter-isUnusedIncluded?: boolean-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## moduleName

```TypeScript
moduleName ?: string
```

卡片所属模块的名称。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FormProviderFilter-moduleName ?: string--><!--Device-FormProviderFilter-moduleName ?: string-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。
