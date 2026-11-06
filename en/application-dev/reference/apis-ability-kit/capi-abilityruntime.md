# AbilityRuntime

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

## Overview

The module provides capabilities related to the ability framework.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

## Files

| Name| Description|
| -- | -- |
| [ability_runtime_common.h](capi-ability-runtime-common-h.md) | Declares the error codes of the AbilityRuntime module.|
| [application_context.h](capi-application-context-h.md) | Declares the APIs related to the application-level context.|
| [context.h](capi-abilityruntime-context-h.md) | Provides the context data structure [AbilityRuntime_Context](capi-abilityruntime-abilityruntime-context.md) and related APIs to obtain information such as the application file path, data encryption level, and process name in the current context.|
| [context_constant.h](capi-context-constant-h.md) | Declares the context constants of the AbilityRuntime module.|
| [connect_options.h](capi-connect-options-h.md) | Declares the connection options of an ExtensionAbility, including the callback APIs for connection success, disconnection, and connection failure.|
| [extension_ability.h](capi-extension-ability-h.md) | Provides the type declaration of the ExtensionAbility callback function and the name declaration of the entry function.|
| [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md) | Declares the ModularObject dispatcher API, which provides the cross-process late binding invocation capability based on type library metadata. You can use this module to create a main service or sub-instance dispatcher from a remote Proxy object, query the type library metadata (APIs, methods, enumerations, and structures) of the remote service, dynamically invoke remote methods through the member ID, and create and operate container types (Array, Vector, Set, and Map) and structures.|
| [modular_object_extension_ability.h](capi-modular-object-extension-ability-h.md) | Declares the API for the ModularObjectExtensionAbility instance, including registering lifecycle callbacks and obtaining the context.|
| [modular_object_extension_context.h](capi-modular-object-extension-context-h.md) | Declares the context API of ModularObjectExtensionAbility, including starting UIAbility, destroying ModularObjectExtensionAbility, and creating and destroying IPC objects.|
| [modular_object_extension_manager.h](capi-modular-object-extension-manager-h.md) | Declares the APIs for managing ModularObjectExtensionAbility, including querying ModularObjectExtensionAbility information, establishing connections, and disconnecting. You can use the APIs provided by this module to query information about all registered ModularObjectExtensionAbility in the current application (including the startup mode, process mode, thread mode, component name, and disabled status) and establish or disconnect communication with a ModularObjectExtensionAbility as required.|
| [start_options.h](capi-start-options-h.md) | Declares the [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) struct for application startup parameters and the functions for setting and obtaining data.|
| [native_ability_wrapper.h](capi-native-ability-wrapper-h.md) | Provides APIs related to NativeAbility data information for obtaining information including the ability instance ID, ability name, and napi_env.|
<!--no_check-->