# ui_event_injection.h

## 概述

声明供应用内智能体和UI自动化使用的接口，用于向UI注入宽松的非精确控制操作。

**引用文件：** <arkui/ui_event_injection.h>

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_ArkUI_NativeModule_UIEventInjection_ResultCode](#oh_arkui_nativemodule_uieventinjection_resultcode) | OH_ArkUI_NativeModule_UIEventInjection_ResultCode | 枚举UI事件注入的结果码。<br> 所有注入接口共用此枚举，包括宽松交互注入（非精确）和面向指定组件的精确注入。 非零结果码表示执行失败，其具体值表示失败原因。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*OH_ArkUI_NativeModule_UIEventInjectionCallback)(OH_ArkUI_NativeModule_UIEventInjection_ResultCode result, void *userData)](#oh_arkui_nativemodule_uieventinjectioncallback) | OH_ArkUI_NativeModule_UIEventInjectionCallback | 注入完成回调。<br> 注入的命令执行结束时，无论成功与否，均调用此回调一次。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIEventInjectCompositeCommand(ArkUI_ContextHandle uiContext, uint32_t uniqueId, const OH_ArkUI_NativeModule_UIJsonWrapper *command, OH_ArkUI_NativeModule_UIEventInjectionCallback callback, void *userData)](#oh_arkui_nativemodule_uieventinjectcompositecommand) | - | 向目标UI节点异步注入控制命令。<br> 目标节点通过唯一ID标识，该ID与OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId使用的ID相同。 框架在uiContext指定的UI实例中，将此唯一ID解析为对应的节点。<br> 命令由通过OH_ArkUI_NativeModule_UIJsonWrapper_Create创建的 OH_ArkUI_NativeModule_UIJsonWrapper对象承载。命令内容的顶层结构如下： {"schemaVersion": 1, "cmd": {"type": "<命令类型>", "action_info": { ... }}}<br> 支持的命令类型及其action_info参数请参见开发指南。<br> uniqueId对应的节点必须与uiContext属于同一UI实例。如果节点属于其他实例， 框架将无法在uiContext中解析该节点，并返回ARKUI_ERROR_CODE_PARAM_INVALID。<br> 必须在uiContext指定的UI实例的UI线程上调用此函数。如果在非UI线程上调用， 框架将输出致命错误日志并终止进程。这是为防止跨线程访问UI导致未定义行为而采用的快速失败设计。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| void (*OH_ArkUI_NativeModule_UIEventInjectionCallback)( OH_ArkUI_NativeModule_UIEventInjection_ResultCode result, void *userData) | 注入完成回调。<br> 注入的命令执行结束时，无论成功与否，均调用此回调一次。<br>**起始版本：** 26.2.0<br>**系统能力：** SystemCapability.ArkUI.ArkUI.Full |

## 枚举类型说明

### OH_ArkUI_NativeModule_UIEventInjection_ResultCode

```c
enum OH_ArkUI_NativeModule_UIEventInjection_ResultCode
```

**描述：**

枚举UI事件注入的结果码。<br> 所有注入接口共用此枚举，包括宽松交互注入（非精确）和面向指定组件的精确注入。 非零结果码表示执行失败，其具体值表示失败原因。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_SUCCESS = 0 | 注入的命令执行成功。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_TARGET_NOT_FOUND = 1 | 未找到能够响应注入命令的组件或目标。<br> 例如，点击坐标未命中任何组件，或无法定位执行模式所需的目标。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_COMMAND_NOT_SUPPORTED = 2 | 当前UI上下文无法执行该命令。<br> 命令结构有效，但当前UI状态不支持该命令的类型或执行模式。<br>**起始版本：** 26.2.0 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_INTERRUPTED_BY_USER = 3 | 注入的命令被用户操作中断。<br>**起始版本：** 26.2.0 |


## 函数说明

### OH_ArkUI_NativeModule_UIEventInjectionCallback()

```c
typedef void (*OH_ArkUI_NativeModule_UIEventInjectionCallback)(OH_ArkUI_NativeModule_UIEventInjection_ResultCode result, void *userData)
```

**描述：**

注入完成回调。<br> 注入的命令执行结束时，无论成功与否，均调用此回调一次。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_NativeModule_UIEventInjection_ResultCode](capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjection_resultcode) result | [in] 注入执行的结果码。详情参见 [OH_ArkUI_NativeModule_UIEventInjection_ResultCode](capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjection_resultcode)。 |
| void *userData | [in] 注入时传入的自定义用户数据指针。如果注入时传入NULL，则此处为NULL。 所指向数据的类型、所有权和生命周期完全由调用方定义。 框架不会解引用或保留此指针，仅将其传回此回调。 该指针必须在回调被调用之前保持有效。 |

### OH_ArkUI_NativeModule_UIEventInjectCompositeCommand()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIEventInjectCompositeCommand(ArkUI_ContextHandle uiContext, uint32_t uniqueId, const OH_ArkUI_NativeModule_UIJsonWrapper *command, OH_ArkUI_NativeModule_UIEventInjectionCallback callback, void *userData)
```

**描述：**

向目标UI节点异步注入控制命令。<br> 目标节点通过唯一ID标识，该ID与OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId使用的ID相同。 框架在uiContext指定的UI实例中，将此唯一ID解析为对应的节点。<br> 命令由通过OH_ArkUI_NativeModule_UIJsonWrapper_Create创建的 OH_ArkUI_NativeModule_UIJsonWrapper对象承载。命令内容的顶层结构如下： {"schemaVersion": 1, "cmd": {"type": "<命令类型>", "action_info": { ... }}}<br> 支持的命令类型及其action_info参数请参见开发指南。<br> uniqueId对应的节点必须与uiContext属于同一UI实例。如果节点属于其他实例， 框架将无法在uiContext中解析该节点，并返回ARKUI_ERROR_CODE_PARAM_INVALID。<br> 必须在uiContext指定的UI实例的UI线程上调用此函数。如果在非UI线程上调用， 框架将输出致命错误日志并终止进程。这是为防止跨线程访问UI导致未定义行为而采用的快速失败设计。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) uiContext | [in] UI实例指针，不能为NULL。调用方必须在该实例的UI线程上调用； 在其他线程上调用将触发致命错误并终止进程。uniqueId必须能够解析为此实例内的节点。 |
| uint32_t uniqueId | [in] 目标节点的唯一ID，与OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId使用的ID相同。 框架在uiContext实例中将此ID解析为对应的节点。 |
| [const OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) *command | [in] 已配置的JSON命令对象指针，不能为NULL。 函数返回前会在内部复制JSON数据；调用方保留对象所有权，可在函数返回后立即销毁该对象。 |
| [OH_ArkUI_NativeModule_UIEventInjectionCallback](capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectioncallback) callback | [in] 可选的完成回调。如果无需接收执行结果，可传入NULL。 如果不为NULL，则在UI线程上恰好调用一次。 |
| void *userData | [in] 传递给回调的自定义用户数据指针，可以为NULL。 如果不为NULL，则必须在回调被调用之前保持有效。框架不会解引用或保留此指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR 命令成功加入队列。</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID 参数无效，包括callback为NULL、缺少必填字段或JSON转换失败。</li> <li>ARKUI_ERROR_CODE_NODE_NOT_FOUND uniqueId无法解析为uiContext实例内的节点。</li> <li>ARKUI_ERROR_CODE_UI_CONTEXT_INVALID UI上下文无效。</li> <li>ARKUI_ERROR_CODE_COMMAND_UNFINISHED 当前进程中仍有其他复合命令正在执行；新命令不会加入队列，也不会调用回调。</li> </ul> |


