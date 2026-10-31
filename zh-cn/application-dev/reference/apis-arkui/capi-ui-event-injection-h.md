# ui_event_injection.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @lushi871202 -->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

声明供应用内智能体和UI自动化使用的接口，用于向指定UI节点或UI实例注入控制命令。

**引用文件：** <arkui/ui_event_injection.h>

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_ArkUI_NativeModule_UIEventInjection_ResultCode](#oh_arkui_nativemodule_uieventinjection_resultcode) | OH_ArkUI_NativeModule_UIEventInjection_ResultCode | 枚举UI事件注入的结果码。<br>所有注入接口共用此枚举，包括宽松交互注入（非精确）和面向指定组件的精确注入。非零结果码表示执行失败，其具体值表示失败原因。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*OH_ArkUI_NativeModule_UIEventInjectionCallback)(OH_ArkUI_NativeModule_UIEventInjection_ResultCode result, void *userData)](#oh_arkui_nativemodule_uieventinjectioncallback) | OH_ArkUI_NativeModule_UIEventInjectionCallback | 注入完成回调。<br>用于通知命令的派发结果和组件对命令的即时处理结果，不等待组件延迟效果或渲染完成。精确注入的每个已受理请求在注入函数返回后，在原UI线程恰好回调一次；宽松注入的回调时机参见[OH_ArkUI_NativeModule_UIEventInjectRelaxedInteraction](#oh_arkui_nativemodule_uieventinjectrelaxedinteraction)。不同UI线程上的回调不保证全局串行执行。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIEventInjectCompositeCommand(ArkUI_ContextHandle uiContext, uint32_t uniqueId, const OH_ArkUI_NativeModule_UIJsonWrapper *command, OH_ArkUI_NativeModule_UIEventInjectionCallback callback, void *userData)](#oh_arkui_nativemodule_uieventinjectcompositecommand) | - | 向目标UI节点异步注入控制命令。<br>本接口不提供取消操作或固定的完成超时，完成依赖UI线程的任务处理。调用方等待超时不会取消已受理请求。实例销毁不会取消已受理请求的完成回调。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIEventInjectRelaxedInteraction(ArkUI_ContextHandle uiContext, const OH_ArkUI_NativeModule_UIJsonWrapper *command, OH_ArkUI_NativeModule_UIEventInjectionCallback callback, void *userData)](#oh_arkui_nativemodule_uieventinjectrelaxedinteraction) | - | 向指定UI实例异步注入宽松交互命令，可从任意线程调用，无需指定节点ID。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| void (*OH_ArkUI_NativeModule_UIEventInjectionCallback)(OH_ArkUI_NativeModule_UIEventInjection_ResultCode result, void *userData) | 注入完成回调。<br>用于通知命令的派发结果和组件对命令的即时处理结果，不等待组件延迟效果或渲染完成。精确注入的每个已受理请求在注入函数返回后，在原UI线程恰好回调一次；宽松注入的回调时机参见[OH_ArkUI_NativeModule_UIEventInjectRelaxedInteraction](#oh_arkui_nativemodule_uieventinjectrelaxedinteraction)。不同UI线程上的回调不保证全局串行执行。 |

## 枚举类型说明

### OH_ArkUI_NativeModule_UIEventInjection_ResultCode

```c
enum OH_ArkUI_NativeModule_UIEventInjection_ResultCode
```

**描述：**

枚举UI事件注入的结果码。<br>所有注入接口共用此枚举，包括宽松交互注入（非精确）和面向指定组件的精确注入。非零结果码表示执行失败，其具体值表示失败原因。

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_SUCCESS = 0 | 注入的命令执行成功。 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_TARGET_NOT_FOUND = 1 | 未找到能够响应注入命令的组件或目标。<br>例如，点击坐标未命中任何组件，或无法定位执行模式所需的目标。 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_COMMAND_NOT_SUPPORTED = 2 | 当前UI上下文无法执行该命令。<br>命令结构有效，但当前UI状态不支持该命令的类型或执行模式。 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_INTERRUPTED_BY_USER = 3 | 注入的命令被用户操作中断。 |

## 函数说明

### OH_ArkUI_NativeModule_UIEventInjectionCallback()

```c
typedef void (*OH_ArkUI_NativeModule_UIEventInjectionCallback)(OH_ArkUI_NativeModule_UIEventInjection_ResultCode result, void *userData)
```

**描述：**

注入完成回调。<br>用于通知命令的派发结果和组件对命令的即时处理结果，不等待组件延迟效果或渲染完成。精确注入的每个已受理请求在注入函数返回后，在原UI线程恰好回调一次；宽松注入的回调时机参见[OH_ArkUI_NativeModule_UIEventInjectRelaxedInteraction](#oh_arkui_nativemodule_uieventinjectrelaxedinteraction)。不同UI线程上的回调不保证全局串行执行。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_NativeModule_UIEventInjection_ResultCode](capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjection_resultcode) result | [入参] 注入执行的结果码。详情参见[OH_ArkUI_NativeModule_UIEventInjection_ResultCode](capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjection_resultcode)。 |
| void *userData | [入参] 注入时传入的自定义用户数据指针。如果注入时传入NULL，则此处为NULL。框架仅保存指针值以供此回调使用，不访问该指针指向的数据，也不复制、释放该数据或接管其所有权。请求受理后，调用方必须保持非NULL数据有效，直到回调返回。 |

### OH_ArkUI_NativeModule_UIEventInjectCompositeCommand()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIEventInjectCompositeCommand(ArkUI_ContextHandle uiContext, uint32_t uniqueId, const OH_ArkUI_NativeModule_UIJsonWrapper *command, OH_ArkUI_NativeModule_UIEventInjectionCallback callback, void *userData)
```

**描述：**

向目标UI节点异步注入控制命令。<br>本接口不提供取消操作或固定的完成超时，完成依赖UI线程的任务处理。调用方等待超时不会取消已受理请求。实例销毁不会取消已受理请求的完成回调。

相关声明位于`<arkui/ui_json_wrapper.h>`。使用`OH_ArkUI_NativeModule_UIJsonWrapperCreate`接口创建JSON包装对象。

`data`指向JSON字符串，`size`为不包含结尾空字符的字节长度。创建成功后，调用方拥有`outOwned`返回的对象，并需在不再使用时调用`OH_ArkUI_NativeModule_UIJsonWrapperDestroy`接口释放对象。

创建接口会复制JSON数据，因此调用方可在`OH_ArkUI_NativeModule_UIJsonWrapperCreate`返回后释放或复用原始字符串。传入`NULL`给销毁接口不会产生任何操作。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) uiContext | [入参] UI实例指针，不能为NULL。调用方必须在该实例的UI线程上调用；检测到线程违规时，将触发致命错误并终止进程。uniqueId必须能够解析为此实例内的节点。uiContext需在本函数调用期间保持有效。 |
| uint32_t uniqueId | [入参] 目标节点ID。框架在uiContext实例中将此节点ID解析为对应的ArkUI节点。 |
| const OH_ArkUI_NativeModule_UIJsonWrapper *command | [入参] 命令数据，不能为NULL，由OH_ArkUI_NativeModule_UIJsonWrapperCreate创建的OH_ArkUI_NativeModule_UIJsonWrapper对象承载。<br>命令内容的顶层结构为：`{"schemaVersion": 1, "cmd": {"type": "<命令类型>", "action_info": { ... }}}`<br>函数返回前会在内部复制JSON数据；调用方拥有的command可在本函数返回后销毁。 |
| [OH_ArkUI_NativeModule_UIEventInjectionCallback](capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectioncallback) callback | [入参] 完成回调，不能为NULL；请求受理后，须保持可调用直至回调返回，即使调用方等待超时也不能提前释放回调资源。 |
| void *userData | [入参] 传递给回调的自定义用户数据指针，可以为NULL。用户数据由调用方管理。请求受理后，非NULL数据须保持有效直至回调返回，即使调用方等待超时也不能提前释放。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | 返回0表示请求已受理，执行结果通过callback报告；返回非零值表示请求被拒绝，不执行命令，也不触发回调。<br>[ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)请求已受理。<br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) command或callback为NULL、命令数据无效，或命令提交失败。<br>[ARKUI_ERROR_CODE_NODE_NOT_FOUND](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)在uiContext实例内未找到节点ID（uniqueId）对应的ArkUI节点。<br>[ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) uiContext为NULL，或对应的UI实例正在销毁或已失效。<br>[ARKUI_ERROR_CODE_COMMAND_UNFINISHED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)当前进程中，前一命令对后续请求的限制尚未解除。命令受理后，同一进程内的其他有效请求均返回此错误码。<br>框架在调用完成回调前解除此限制。可在回调中再次提交命令，仍需满足参数和UI线程要求。被拒绝的请求可在限制解除后重试，能否受理仍取决于进程内的其他请求。 |

### OH_ArkUI_NativeModule_UIEventInjectRelaxedInteraction()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIEventInjectRelaxedInteraction(ArkUI_ContextHandle uiContext, const OH_ArkUI_NativeModule_UIJsonWrapper *command, OH_ArkUI_NativeModule_UIEventInjectionCallback callback, void *userData)
```

**描述：**

向指定UI实例异步注入宽松交互命令，无需指定节点ID。支持点击、内容切换、滚动、返回和按键五类命令，参数格式及示例参见[注入实例级交互命令](../../ui/ndk-ui-event-injection.md)。本接口仅作用于调用方进程内的UI实例。

本接口可从任意线程调用，在返回前完成JSON参数校验和复制，将命令投递到目标实例的UI线程执行。同步返回0仅表示请求已受理，执行结果通过callback报告。返回非零值时，不执行命令，也不触发回调。

callback非NULL时，在命令完成后于目标实例的UI线程调用一次。UI线程发起时，回调在注入函数返回后执行；其他线程发起时，回调可能在注入函数返回前执行。回调表示命令派发与即时处理结束，不等待动画或渲染完成。可同时提交多个请求，不保证执行或回调顺序。

用户操作可中断尚未完成的命令，回调报告INTERRUPTED_BY_USER。请求受理后实例失效，未完成请求报告TARGET_NOT_FOUND；已经判定为用户中断的请求保留INTERRUPTED_BY_USER结果。实例销毁不取消完成通知，但通知依赖UI线程继续处理任务，不提供固定完成超时。调用方等待超时不会取消请求，也不能据此释放回调资源或userData。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) uiContext | [入参] 目标UI实例句柄，不能为NULL，调用期间必须有效。调用方须同步句柄自身的销毁。 |
| const [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) *command | [入参] 使用[OH_ArkUI_NativeModule_UIJsonWrapperCreate](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappercreate)创建的JSON命令对象，不能为NULL。调用期间必须有效，函数返回后可立即销毁。 |
| [OH_ArkUI_NativeModule_UIEventInjectionCallback](#oh_arkui_nativemodule_uieventinjectioncallback) callback | [入参] 完成回调，可为NULL。非NULL时，须保持可调用直至回调退出。 |
| void *userData | [入参] 原样传递给callback的自定义用户数据指针，可为NULL。框架不访问、复制或释放所指数据，不接管其所有权。callback非NULL时，数据必须在发起调用前准备好，并保持有效直至回调退出；运行环境关闭时须同步回调退出后再释放。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | ARKUI_ERROR_CODE_NO_ERROR（0）：请求已受理。<br>ARKUI_ERROR_CODE_PARAM_INVALID（401）：command为NULL、JSON格式或命令参数非法、缺少必填字段，或命令投递失败。<br>ARKUI_ERROR_CODE_UI_CONTEXT_INVALID（190001）：uiContext为NULL，或目标实例、任务执行器不可用。 |
