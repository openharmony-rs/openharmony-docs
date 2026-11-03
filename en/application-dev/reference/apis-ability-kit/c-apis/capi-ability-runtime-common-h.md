# ability_runtime_common.h

## Overview

The file declares the error codes of the AbilityRuntime module.

**Library**: libability_runtime.so

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

**Related module**: [AbilityRuntime](capi-ability-kit-abilityruntime.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [AbilityRuntime_ErrorCode](#abilityruntime_errorcode) | AbilityRuntime_ErrorCode | Enumerates the error codes of the AbilityRuntime module. |

## Enum type description

### AbilityRuntime_ErrorCode

```c
enum AbilityRuntime_ErrorCode
```

**Description**

Enumerates the error codes of the AbilityRuntime module.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

| Enum item | Description |
| -- | -- |
| ABILITY_RUNTIME_ERROR_CODE_NO_ERROR = 0 | Operation successful.<br>**Since**: 13 |
| ABILITY_RUNTIME_ERROR_CODE_PERMISSION_DENIED = 201 | Permission verification fails.<br>**Since**: 15 |
| ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID = 401 | Invalid parameter.<br>**Since**: 13 |
| ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED = 801 | The device type is not supported.<br>**Since**: 15 |
| ABILITY_RUNTIME_ERROR_CODE_NO_SUCH_ABILITY = 16000001 | The specified ability name does not exist.<br>**Since**: 15 |
| ABILITY_RUNTIME_ERROR_CODE_INCORRECT_ABILITY_TYPE = 16000002 | The ability type is incorrect.<br>**Since**: 15 |
| ABILITY_RUNTIME_ERROR_CODE_VISIBILITY_VERIFICATION_FAILED = 16000004 | Cannot start an invisible component.<br>**Since**: 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_STATIC_CFG_PERMISSION = 16000005 | The specified process does not have permission.<br>**Since**: 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_CROSS_USER_OPERATION = 16000006 | Cross-user operations are not allowed.<br>**Since**: 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_CROWDTEST_EXPIRED = 16000008 | The crowdtesting application expires.<br>**Since**: 15 |
| ABILITY_RUNTIME_ERROR_CODE_WUKONG_MODE = 16000009 | An ability cannot be started or stopped in Wukong mode.<br>**Since**: 15 |
| ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST = 16000011 | The context does not exist.<br>**Since**: 13 |
| ABILITY_RUNTIME_ERROR_CODE_CONTROLLED = 16000012 | The application is under control.<br>**Since**: 15 |
| ABILITY_RUNTIME_ERROR_CODE_EDM_CONTROLLED = 16000013 | The application is under control by EDM.<br>**Since**: 15 |
| ABILITY_RUNTIME_ERROR_CODE_CROSS_APP = 16000018 | Redirection to third-party applications is not allowed in API versions later than 11.<br>**Since**: 15 |
| ABILITY_RUNTIME_ERROR_CODE_INTERNAL = 16000050 | Internal server error.<br>**Since**: 15 |
| ABILITY_RUNTIME_ERROR_CODE_NOT_TOP_ABILITY = 16000053 | The application is not on top.<br>**Since**: 15 |
| ABILITY_RUNTIME_ERROR_VISIBILITY_SETTING_DISABLED = 16000067 | Setting the window visibility during startup is not allowed.<br>**Since**: 17 |
| ABILITY_RUNTIME_ERROR_CODE_MULTI_APP_NOT_SUPPORTED = 16000072 | The application does not support clone or multi-instance mode.<br>**Since**: 17 |
| ABILITY_RUNTIME_ERROR_CODE_INVALID_APP_INSTANCE_KEY = 16000076 | The multi-instance key is invalid.<br>**Since**: 17 |
| ABILITY_RUNTIME_ERROR_CODE_UPPER_LIMIT_REACHED = 16000077 | The number of instances has reached the upper limit.<br>**Since**: 17 |
| ABILITY_RUNTIME_ERROR_MULTI_INSTANCE_NOT_SUPPORTED = 16000078 | The application does not support multi-instance mode.<br>**Since**: 17 |
| ABILITY_RUNTIME_ERROR_CODE_APP_INSTANCE_KEY_NOT_SUPPORTED = 16000079 | Setting **APP_INSTANCE_KEY** is not supported.<br>**Since**: 17 |
| ABILITY_RUNTIME_ERROR_CODE_GET_APPLICATION_INFO_FAILED = 16000081 | Failed to obtain the application information.<br>**Since**: 21 |
| ABILITY_RUNTIME_ERROR_CODE_START_TIMEOUT = 16000133 | Starting the UIAbility times out.<br>**Since**: 21 |
| ABILITY_RUNTIME_ERROR_CODE_MAIN_THREAD_NOT_SUPPORTED = 16000134 | The function cannot be called on the main thread of the application.<br>**Since**: 21 |
| ABILITY_RUNTIME_ERROR_CODE_NO_RUNNING_ABILITIES_WITH_UI = 16000170 | The target application does not have running abilities with UI.<br>**Since**: 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_UPPER_RATE_LIMIT = 16000171 | The API call frequency is too high and exceeds the rate control limit.<br>**Since**: 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_UPPER_CONNECTION_NUMBER_LIMIT = 16000172 | The number of connections exceeds limit.<br>**Since**: 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND = 16000173 | The requested property, method, interface, enum, struct type, struct field, set element, or map key is not found.<br>**Since**: 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_TYPE_MISMATCH = 16000174 | The runtime value type does not match the expected metadata type.<br>**Since**: 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_SEND_REQUEST_FAILED = 16000175 | The IPC request to the remote service fails.<br>**Since**: 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_CROSS_APP_IN_PROCESS = 16000176 | Caller and target are not in the same application for [OH_ABILITY_RUNTIME_LAUNCH_MODE_IN_PROCESS](capi-modular-object-extension-manager-h.md#oh_abilityruntime_launchmode) mode.<br>**Since**: 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_ABILITY_WRAPPER_INVALID = 16000177 | The native ability wrapper is invalid or incomplete.<br>**Since**: 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_METADATA_INVALID = 16000178 | The type library metadata is invalid, for example, missing or duplicate main interface.<br>**Since**: 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_BUFFER_TOO_SMALL = 16000179 | The buffer is too small.<br>**Since**: 26.0.1 |


