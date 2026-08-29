# connect_options.h

## 概述

声明ExtensionAbility的连接选项，包括连接成功、断开连接和连接失败的回调接口。

**库：** libability_runtime.so

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 26.0.0

**相关模块：** [AbilityRuntime](capi-abilityruntime.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) | OH_AbilityRuntime_ConnectOptions | 定义OH_AbilityRuntime_ConnectOptions结构体类型。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*OH_AbilityRuntime_ConnectOptions_OnConnectCallback)(OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityBase_Element *element, OHIPCRemoteProxy *proxy)](#oh_abilityruntime_connectoptions_onconnectcallback) | OH_AbilityRuntime_ConnectOptions_OnConnectCallback | 回调接口已成功连接。 |
| [typedef void (\*OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback)(OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityBase_Element *element)](#oh_abilityruntime_connectoptions_ondisconnectcallback) | OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback | 回调接口已成功断开连接。 |
| [typedef void (\*OH_AbilityRuntime_ConnectOptions_OnFailedCallback)(OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityRuntime_ErrorCode code)](#oh_abilityruntime_connectoptions_onfailedcallback) | OH_AbilityRuntime_ConnectOptions_OnFailedCallback | 连接失败时调用回调接口。 |
| [OH_AbilityRuntime_ConnectOptions* OH_AbilityRuntime_CreateConnectOptions()](#oh_abilityruntime_createconnectoptions) | - | 创建一个ConnectOptions对象。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_DestroyConnectOptions(OH_AbilityRuntime_ConnectOptions *connectOptions)](#oh_abilityruntime_destroyconnectoptions) | - | 销毁指定的ConnectOptions对象。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ConnectOptions_SetOnConnectCallback(OH_AbilityRuntime_ConnectOptions *connectOptions, OH_AbilityRuntime_ConnectOptions_OnConnectCallback onConnectCallback)](#oh_abilityruntime_connectoptions_setonconnectcallback) | - | 将回调[OH_AbilityRuntime_ConnectOptions_OnConnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onconnectcallback)设置为[OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md)。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ConnectOptions_SetOnDisconnectCallback(OH_AbilityRuntime_ConnectOptions *connectOptions, OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback onDisconnectCallback)](#oh_abilityruntime_connectoptions_setondisconnectcallback) | - | 将回调[OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_ondisconnectcallback)设置为[OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md)。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ConnectOptions_SetOnFailedCallback(OH_AbilityRuntime_ConnectOptions *connectOptions, OH_AbilityRuntime_ConnectOptions_OnFailedCallback onFailedCallback)](#oh_abilityruntime_connectoptions_setonfailedcallback) | - | 将回调[OH_AbilityRuntime_ConnectOptions_OnFailedCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onfailedcallback)设置为[OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md)。 |

## 函数说明

### OH_AbilityRuntime_ConnectOptions_OnConnectCallback()

```c
typedef void (*OH_AbilityRuntime_ConnectOptions_OnConnectCallback)(OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityBase_Element *element, OHIPCRemoteProxy *proxy)
```

**描述**

回调接口已成功连接。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) \*connectOptions | 表示指向[OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md)实例的指针。 |
| [AbilityBase_Element](capi-abilitybase-abilitybase-element.md) \*element | 表示模块对象扩展功能的元素名称。 |
| OHIPCRemoteProxy \*proxy | 表示远程对象实例。 |

### OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback()

```c
typedef void (*OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback)(OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityBase_Element *element)
```

**描述**

回调接口已成功断开连接。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) \*connectOptions | 表示指向[OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md)实例的指针。 |
| [AbilityBase_Element](capi-abilitybase-abilitybase-element.md) \*element | 表示模块对象扩展功能的元素名称。 |

### OH_AbilityRuntime_ConnectOptions_OnFailedCallback()

```c
typedef void (*OH_AbilityRuntime_ConnectOptions_OnFailedCallback)(OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityRuntime_ErrorCode code)
```

**描述**

连接失败时调用回调接口。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) \*connectOptions | 表示指向[OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md)实例的指针。 |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) code | 表示失败的错误代码。 |

### OH_AbilityRuntime_CreateConnectOptions()

```c
OH_AbilityRuntime_ConnectOptions* OH_AbilityRuntime_CreateConnectOptions()
```

**描述**

创建一个ConnectOptions对象。

**起始版本：** 26.0.0

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AbilityRuntime_ConnectOptions*](capi-abilityruntime-oh-abilityruntime-connectoptions.md) | 返回新创建的OH_AbilityRuntime_ConnectOptions对象。      <br>调用方需调用[OH_AbilityRuntime_DestroyConnectOptions](capi-connect-options-h.md#oh_abilityruntime_destroyconnectoptions)销毁返回的对象，避免内存泄漏。 |

### OH_AbilityRuntime_DestroyConnectOptions()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_DestroyConnectOptions(OH_AbilityRuntime_ConnectOptions *connectOptions)
```

**描述**

销毁指定的ConnectOptions对象。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) *connectOptions | 待销毁的ConnectOptions对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回特定的错误码。      <br>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) 操作成功。      <br>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) connectOptions无效。 |

### OH_AbilityRuntime_ConnectOptions_SetOnConnectCallback()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ConnectOptions_SetOnConnectCallback(OH_AbilityRuntime_ConnectOptions *connectOptions, OH_AbilityRuntime_ConnectOptions_OnConnectCallback onConnectCallback)
```

**描述**

将回调[OH_AbilityRuntime_ConnectOptions_OnConnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onconnectcallback)设置为[OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md)。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) *connectOptions | 表示指向[OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md)实例的指针，在其中设置。 |
| [OH_AbilityRuntime_ConnectOptions_OnConnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onconnectcallback) onConnectCallback | 表示[OH_AbilityRuntime_ConnectOptions_OnConnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onconnectcallback)实例，将在其中设置。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回特定的错误码。  [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)-成功。  [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode)-参数校验失败。 |

### OH_AbilityRuntime_ConnectOptions_SetOnDisconnectCallback()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ConnectOptions_SetOnDisconnectCallback(OH_AbilityRuntime_ConnectOptions *connectOptions, OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback onDisconnectCallback)
```

**描述**

将回调[OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_ondisconnectcallback)设置为[OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md)。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) *connectOptions | 表示指向[OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md)实例的指针，在其中设置。 |
| [OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_ondisconnectcallback) onDisconnectCallback | 表示[OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_ondisconnectcallback)实例，将在其中设置。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回特定的错误码。  [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)-成功。  [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode)-参数校验失败。 |

### OH_AbilityRuntime_ConnectOptions_SetOnFailedCallback()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ConnectOptions_SetOnFailedCallback(OH_AbilityRuntime_ConnectOptions *connectOptions, OH_AbilityRuntime_ConnectOptions_OnFailedCallback onFailedCallback)
```

**描述**

将回调[OH_AbilityRuntime_ConnectOptions_OnFailedCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onfailedcallback)设置为[OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md)。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) *connectOptions | 表示指向[OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md)实例的指针，在其中设置。 |
| [OH_AbilityRuntime_ConnectOptions_OnFailedCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onfailedcallback) onFailedCallback | 表示[OH_AbilityRuntime_ConnectOptions_OnFailedCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onfailedcallback)实例，将在其中设置。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回特定的错误码。  [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)-成功。  [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode)-参数校验失败。 |


