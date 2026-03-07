# extension_ability.h

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yangzhongkai-->
<!--Designer: @yangzhongkai-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

## 概述

提供ExtensionAbility加载原生代码的回调函数和入口函数名称声明。

**引用文件：** <AbilityKit/ability_runtime/extension_ability.h>

**库：** libability_runtime.so

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 24

**相关模块：** [AbilityRuntime](capi-abilityruntime.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [AbilityRuntime_ExtensionInstance](capi-abilityruntime-extensioninstance.md) | - | 定义AbilityRuntime_ExtensionInstance结构体类型。 |
| [AbilityRuntime_ExtensionInstance*](capi-abilityruntime-extensioninstance8h.md) | AbilityRuntime_ExtensionInstanceHandle | 定义指向AbilityRuntime_ExtensionInstance的指针。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void AbilityRuntime_Extension_CreateFunc(AbilityRuntime_ExtensionInstanceHandle handle, const char *abilityName);](#abilityruntime_extension_createfunc) | AbilityRuntime_Extension_CreateFunc | ExtensionAbility创建回调函数类型。定义原生代码中必须实现的回调函数类型，用于实例化ExtensionAbility。开发者需要实现此类型的函数并将其命名为OH_AbilityRuntime_OnNativeExtensionCreate，系统会自动查找并调用该函数。 |

### 变量

| 名称 | 描述 |
|------|------|
| [AbilityRuntime_Extension_CreateFunc](#abilityruntime_extension_createfunc) OH_AbilityRuntime_OnNativeExtensionCreate | ExtensionAbility入口函数名称声明。声明原生ExtensionAbility实例在启动时系统查找的入口函数。开发者需要实现一个类型为[AbilityRuntime_Extension_CreateFunc](#abilityruntime_extension_createfunc)的函数，并将其命名为OH_AbilityRuntime_OnNativeExtensionCreate。系统会自动查找并调用此函数来完成ExtensionAbility实例的初始化。<br>**起始版本：** 24 |

## 函数说明

### AbilityRuntime_Extension_CreateFunc()

```c
typedef void AbilityRuntime_Extension_CreateFunc(AbilityRuntime_ExtensionInstanceHandle handle, const char *abilityName)
```

**描述**

ExtensionAbility创建回调函数类型。定义原生代码中必须实现的回调函数类型，用于实例化ExtensionAbility。开发者需要实现此类型的函数并将其命名为OH_AbilityRuntime_OnNativeExtensionCreate，系统会自动查找并调用该函数。

**起始版本：** 24

**参数：**

| 参数名 | 描述 |
|--------|------|
| [AbilityRuntime_ExtensionInstanceHandle](capi-abilityruntime-extensioninstance8h.md) handle | 新创建的AbilityRuntime_ExtensionInstanceHandle实例的指针。 |
| const char *abilityName | 要创建的ExtensionAbility的名称。 |
