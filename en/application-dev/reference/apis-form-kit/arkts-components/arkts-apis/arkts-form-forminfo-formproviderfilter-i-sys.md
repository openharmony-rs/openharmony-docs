# FormProviderFilter (System API)

```TypeScript
interface FormProviderFilter
```

Information about a running form.

@typedef FormProviderFilter

**Since:** 10

<!--Device-formInfo-interface FormProviderFilter--><!--Device-formInfo-interface FormProviderFilter-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## abilityName

```TypeScript
abilityName ?: string
```

Obtains the ability name of the provider application module.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-FormProviderFilter-abilityName ?: string--><!--Device-FormProviderFilter-abilityName ?: string-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## bundleName

```TypeScript
bundleName: string
```

Obtains the bundle name of the provider application.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-FormProviderFilter-bundleName: string--><!--Device-FormProviderFilter-bundleName: string-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## formName

```TypeScript
formName ?: string
```

Obtains the form name of the provider application form.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-FormProviderFilter-formName ?: string--><!--Device-FormProviderFilter-formName ?: string-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## isUnusedIncluded

```TypeScript
isUnusedIncluded?: boolean
```

Indicates whether to include unused form.

**Type:** boolean

**Default:** false

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-FormProviderFilter-isUnusedIncluded?: boolean--><!--Device-FormProviderFilter-isUnusedIncluded?: boolean-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## moduleName

```TypeScript
moduleName ?: string
```

Obtains the module name of the provider application module.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-FormProviderFilter-moduleName ?: string--><!--Device-FormProviderFilter-moduleName ?: string-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.
