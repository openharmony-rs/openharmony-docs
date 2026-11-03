# AbilityRuntime

## Overview

Provide the definition of the C interface for the native AbilityRuntime

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

## Files

| Name | Description |
| -- | -- |
| [ability_runtime_common.h](capi-ability-runtime-common-h.md) | The file declares the error codes of the AbilityRuntime module. |
| [context.h](capi-context-h.md) | Provides the context data structure [AbilityRuntime_Context](capi-abilityruntime-abilityruntime-context.md) and related APIs for obtaining information such as the app file path, data encryption level, and process name of the current context. |
| [modular_object_extension_ability.h](capi-modular-object-extension-ability-h.md) | Declares the interfaces of a ModularObjectExtensionAbility instance, including the capabilities of registering lifecycle callback functions and obtaining the context. It is applicable to scenarios where the lifecycle of ModularObjectExtensionAbility is processed.<br> **File to include:** <AbilityKit/ability_runtime/modular_object_extension_ability.h> |
| [start_options.h](capi-start-options-h.md) | Defines the start options APIs. |
| [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md) | Declares the ModularObject dispatcher APIs, providing cross-process deferred binding invocation capabilities based on type library metadata. Through this module, developers can create a main service or sub-instance dispatcher from a remote Proxy object, query the type library metadata (interface/method/enum/struct) of the remote service, dynamically invoke remote methods by member ID (MemberID), and create and operate container types (Array/Vector/Set/Map) and structs.<br> **File to include:** <AbilityKit/ability_runtime/modular_object_dispatcher.h> |
| [connect_options.h](capi-connect-options-h.md) | Declares the connection options for extension ability, including callbacks for connection success, disconnection, and connection failure. |
| [application_context.h](capi-application-context-h.md) | The file declares the APIs related to the application-level context. |
| [context_constant.h](capi-context-constant-h.md) | The file declares the context constants of the AbilityRuntime module. |
| [modular_object_extension_manager.h](capi-modular-object-extension-manager-h.md) | Declares the APIs for managing ModularObjectExtensionAbility, including querying ModularObjectExtensionAbility information, connecting to and disconnecting from it. Developers can use the APIs provided by this module to query the information of all registered ModularObjectExtensionAbility instances in the current app (including the startup mode, process mode, thread mode, component name, and disabled state), and establish or disconnect the communication connection with ModularObjectExtensionAbility as needed.<br> **File to include:** <AbilityKit/ability_runtime/modular_object_extension_manager.h> |
| [extension_ability.h](capi-extension-ability-h.md) | Provides the type declaration of the ExtensionAbility callback function and the name declaration of the entry function. |
| [native_ability_wrapper.h](capi-native-ability-wrapper-h.md) | Provides the NativeAbility data information APIs for obtaining the Ability instance ID, Ability name, and napi_env.<br> **File to include:** <AbilityKit/ability_runtime/native_ability_wrapper.h> |
| [modular_object_extension_context.h](capi-modular-object-extension-context-h.md) | Declares the context APIs of ModularObjectExtensionAbility, including starting a UIAbility, destroying the ModularObjectExtensionAbility itself, and creating and destroying IPC objects.<br> **File to include:** <AbilityKit/ability_runtime/modular_object_extension_context.h> |
| [child_process_info.h](capi-child-process-info-h.md) | Defines the child process info type and accessor functions. |
