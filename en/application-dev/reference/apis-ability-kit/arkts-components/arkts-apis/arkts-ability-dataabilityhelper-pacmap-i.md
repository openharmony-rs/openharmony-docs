# PacMap

Defines the PacMap type used for data storage.

**Since:** 7

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## [key: string]

```TypeScript
[key: string]: number | string | boolean | Array<string | number | boolean> | null
```

Indicates the parameter of the PacMap type. If a custom Sequenceable object is put in the PacMap object and will be transferred across processes, you must call BasePacMap.setClassLoader(ClassLoader) to set a class loader for the custom object. If the PacMap object is to be transferred to a non-OHOS process, values of primitive types are supported, but not custom Sequenceable objects.

**Type:** number &#124; string &#124; boolean &#124; Array&lt;string &#124; number &#124; boolean&gt; &#124; null

**Since:** 7

**Model restriction:** 
- API version 11 and later: This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel
