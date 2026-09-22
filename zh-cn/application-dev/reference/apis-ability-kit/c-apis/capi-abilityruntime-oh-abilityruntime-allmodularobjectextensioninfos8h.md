# OH_AbilityRuntime_AllModularObjectExtensionInfos*

```c
typedef struct OH_AbilityRuntime_AllModularObjectExtensionInfos* OH_AbilityRuntime_AllModObjExtensionInfosHandle
```

## 概述

表示当前应用内所有ModularObjectExtensionAbility信息的集合句柄。该句柄指向一个包含多个{@link OH_AbilityRuntime_ModObjExtensionInfoHandle}<br>的集合，可通过{@link OH_AbilityRuntime_GetCountFromAllModObjExtensionInfos} 获取集合中元素的数量，并通过<br>{@link OH_AbilityRuntime_GetModObjExtensionInfoByIndex} 按索引遍历获取单个ModularObjectExtensionAbility信息。使用完毕后需通过<br>{@link OH_AbilityRuntime_ReleaseAllExtensionInfos} 释放该集合。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 26.0.0

**相关模块：** [AbilityRuntime](capi-abilityruntime.md)

**所在头文件：** [modular_object_extension_manager.h](capi-modular-object-extension-manager-h.md)

