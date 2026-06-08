# AbilityRuntime

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

## 概述

声明元能力基础框架的相关能力。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 13

## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [ability_runtime_common.h](capi-ability-runtime-common-h.md) | 提供AbilityRuntime模块的错误码。 |
| [application_context.h](capi-application-context-h.md) | 提供应用级别上下文相关的接口。 |
| [context.h](capi-abilityruntime-context-h.md) | 提供上下文数据结构[AbilityRuntime_Context](capi-abilityruntime-abilityruntime-context.md)和相关接口用于获取当前上下文的应用文件路径、数据加密等级和进程名等信息。|
| [context_constant.h](capi-context-constant-h.md) | 提供AbilityRuntime模块上下文常量的定义。 |
| [connect_options.h](capi-connect-options-h.md) | 声明ExtensionAbility的连接选项，包括连接成功、断开连接和连接失败的回调接口。 |
| [extension_ability.h](capi-extension-ability-h.md) | 提供ExtensionAbility回调函数类型声明和入口函数名称声明。 |
| [modular_object_extension_ability.h](capi-modular-object-extension-ability-h.md) | 声明ModularObjectExtensionAbility实例的接口，包括注册生命周期回调函数和获取上下文等能力。 |
| [modular_object_extension_context.h](capi-modular-object-extension-context-h.md) | 声明ModularObjectExtensionAbility的上下文接口，包括启动UIAbility、销毁ModularObjectExtensionAbility自身、创建和销毁IPC对象等功能。 |
| [modular_object_extension_manager.h](capi-modular-object-extension-manager-h.md) | 声明用于管理ModularObjectExtensionAbility的接口，包括查询ModularObjectExtensionAbility信息、连接与断开连接等能力。开发者可以通过本模块提供的接口查询当前应用内所有已注册的ModularObjectExtensionAbility的信息（包括启动模式、进程模式、线程模式、组件名称及禁用状态等），并根据需要建立或断开与ModularObjectExtensionAbility的通信连接。 |
| [start_options.h](capi-start-options-h.md) | 提供应用启动参数数据结构[AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md)以及设置和获取相关函数。 |
| [native_ability_wrapper.h](capi-native-ability-wrapper-h.md) | 提供NativeAbility数据信息相关接口，用于获取Ability实例ID、Ability名称和napi_env等信息。 |
