# ability_runtime_common.h

## 概述

声明AbilityRuntime模块的错误码。

**库：** libability_runtime.so

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 13

**相关模块：** [AbilityRuntime](capi-ability-kit-abilityruntime.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [AbilityRuntime_ErrorCode](#abilityruntime_errorcode) | AbilityRuntime_ErrorCode | AbilityRuntime模块的错误码的枚举。 |

## 枚举类型说明

### AbilityRuntime_ErrorCode

```c
enum AbilityRuntime_ErrorCode
```

**描述：**

AbilityRuntime模块的错误码的枚举。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 13

| 枚举项 | 描述 |
| -- | -- |
| ABILITY_RUNTIME_ERROR_CODE_NO_ERROR = 0 | 操作成功。<br>**起始版本：** 13 |
| ABILITY_RUNTIME_ERROR_CODE_PERMISSION_DENIED = 201 | 权限校验失败。<br>**起始版本：** 15 |
| ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID = 401 | 无效参数。<br>**起始版本：** 13 |
| ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED = 801 | 设备类型不支持。<br>**起始版本：** 15 |
| ABILITY_RUNTIME_ERROR_CODE_NO_SUCH_ABILITY = 16000001 | 指定的Ability名称不存在。<br>**起始版本：** 15 |
| ABILITY_RUNTIME_ERROR_CODE_INCORRECT_ABILITY_TYPE = 16000002 | 接口调用Ability类型错误。<br>**起始版本：** 15 |
| ABILITY_RUNTIME_ERROR_CODE_VISIBILITY_VERIFICATION_FAILED = 16000004 | 无法启动不可见组件。<br>**起始版本：** 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_STATIC_CFG_PERMISSION = 16000005 | 指定的进程没有权限。<br>**起始版本：** 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_CROSS_USER_OPERATION = 16000006 | 不允许跨用户操作。<br>**起始版本：** 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_CROWDTEST_EXPIRED = 16000008 | 众测应用到期。<br>**起始版本：** 15 |
| ABILITY_RUNTIME_ERROR_CODE_WUKONG_MODE = 16000009 | Wukong模式，不允许启动/停止Ability。<br>**起始版本：** 15 |
| ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST = 16000011 | 上下文不存在。<br>**起始版本：** 13 |
| ABILITY_RUNTIME_ERROR_CODE_CONTROLLED = 16000012 | 应用被管控。<br>**起始版本：** 15 |
| ABILITY_RUNTIME_ERROR_CODE_EDM_CONTROLLED = 16000013 | 应用被EDM管控。<br>**起始版本：** 15 |
| ABILITY_RUNTIME_ERROR_CODE_CROSS_APP = 16000018 | 限制API 11以上版本三方应用跳转。<br>**起始版本：** 15 |
| ABILITY_RUNTIME_ERROR_CODE_INTERNAL = 16000050 | 内部错误。<br>**起始版本：** 15 |
| ABILITY_RUNTIME_ERROR_CODE_NOT_TOP_ABILITY = 16000053 | 非顶层应用。<br>**起始版本：** 15 |
| ABILITY_RUNTIME_ERROR_VISIBILITY_SETTING_DISABLED = 16000067 | 不允许设置窗口启动可见性。<br>**起始版本：** 17 |
| ABILITY_RUNTIME_ERROR_CODE_MULTI_APP_NOT_SUPPORTED = 16000072 | 不支持应用分身和多实例。<br>**起始版本：** 17 |
| ABILITY_RUNTIME_ERROR_CODE_INVALID_APP_INSTANCE_KEY = 16000076 | 无效多实例。<br>**起始版本：** 17 |
| ABILITY_RUNTIME_ERROR_CODE_UPPER_LIMIT_REACHED = 16000077 | 应用多实例已达到上限。<br>**起始版本：** 17 |
| ABILITY_RUNTIME_ERROR_MULTI_INSTANCE_NOT_SUPPORTED = 16000078 | 不支持应用多实例。<br>**起始版本：** 17 |
| ABILITY_RUNTIME_ERROR_CODE_APP_INSTANCE_KEY_NOT_SUPPORTED = 16000079 | 不允许设置APP_INSTANCE_KEY。<br>**起始版本：** 17 |
| ABILITY_RUNTIME_ERROR_CODE_GET_APPLICATION_INFO_FAILED = 16000081 | 获取应用信息失败。<br>**起始版本：** 21 |
| ABILITY_RUNTIME_ERROR_CODE_START_TIMEOUT = 16000133 | 启动UIAbility超时。<br>**起始版本：** 21 |
| ABILITY_RUNTIME_ERROR_CODE_MAIN_THREAD_NOT_SUPPORTED = 16000134 | 接口不允许在应用主线程调用。<br>**起始版本：** 21 |
| ABILITY_RUNTIME_ERROR_CODE_NO_RUNNING_ABILITIES_WITH_UI = 16000170 | 目标应用程序没有UI的运行能力。<br>**起始版本：** 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_UPPER_RATE_LIMIT = 16000171 | API调用频率过高，超过速率控制限制。<br>**起始版本：** 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_UPPER_CONNECTION_NUMBER_LIMIT = 16000172 | 连接数超过限制。<br>**起始版本：** 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND = 16000173 | 找不到该属性。<br>**起始版本：** 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_TYPE_MISMATCH = 16000174 | 类型不匹配。<br>**起始版本：** 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_SEND_REQUEST_FAILED = 16000175 | 向远程发送请求失败。<br>**起始版本：** 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_CROSS_APP_IN_PROCESS = 16000176 | 调用方和目标不在[OH_ABILITY_RUNTIME_LAUNCH_MODE_IN_PROCESS](capi-modular-object-extension-manager-h.md#oh_abilityruntime_launchmode)模式的同一应用程序中。<br>**起始版本：** 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_ABILITY_WRAPPER_INVALID = 16000177 | native ability wrapper无效或不完整。<br>**起始版本：** 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_METADATA_INVALID = 16000178 | 类型库元数据无效，例如主接口缺失或重复。<br>**起始版本：** 26.0.0 |
| ABILITY_RUNTIME_ERROR_CODE_BUFFER_TOO_SMALL = 16000179 |  |


