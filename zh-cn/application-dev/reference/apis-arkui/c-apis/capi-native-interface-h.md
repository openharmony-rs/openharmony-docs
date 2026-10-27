# native_interface.h

## 概述

提供NativeModule接口的统一入口函数。

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_NativeAPIVariantKind](#arkui_nativeapivariantkind) | ArkUI_NativeAPIVariantKind | 定义Native接口集合类型。 |
| [OH_ArkUI_NativeModule_RuntimeCheckType](#oh_arkui_nativemodule_runtimechecktype) | OH_ArkUI_NativeModule_RuntimeCheckType | ArkUI C API的运行时检查类型枚举。<br> 每种检查类型对应一种ArkUI C API的不当使用场景，用于在运行时检测开发者 对C API的误用行为（如跨线程调用、访问已销毁对象等）。 可通过[OH_ArkUI_NativeModule_SetRuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_setruntimecheckmode)为每种检查类型 独立配置运行时检查模式，检查失败时的行为由所配置的运行时检查模式决定，模式取值见[OH_ArkUI_NativeModule_RuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode)。 |
| [OH_ArkUI_NativeModule_RuntimeCheckMode](#oh_arkui_nativemodule_runtimecheckmode) | OH_ArkUI_NativeModule_RuntimeCheckMode | ArkUI C API运行时检查的模式枚举。<br> 所有C API的运行时检查类型均使用本枚举中定义的相同模式集合（DISABLED、LOG、CRASH）设置检查失败时的行为， 即每种检查类型都可以独立设置为以下三种模式之一。 默认模式取决于应用程序的构建类型： 以debug模式编译的应用（DevEco Studio中Debug构建，用于开发调试） 默认为[OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode)， 以release模式编译的应用（DevEco Studio中Release构建，用于正式发布） 默认为[OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode)。 |

### 宏定义

| 名称 | 描述 |
| -- | -- |
| OH_ArkUI_GetModuleInterface(nativeAPIVariantKind, structType, structPtr)                      do {                                                                                              void* anyNativeAPI = OH_ArkUI_QueryModuleInterfaceByName(nativeAPIVariantKind, #structType);  if (anyNativeAPI) {                                                                           structPtr = (structType*)(anyNativeAPI);                                                  }                                                                                             } while (0) | 初始化C-API环境，并基于结构体类型获取对应结构体指针。 适用于已确定Native接口集合类型和接口结构体类型，需要获取具体Native接口结构体指针以调用ArkUI Native C API的场景。<br>**起始版本：** 12 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [void* OH_ArkUI_QueryModuleInterfaceByName(ArkUI_NativeAPIVariantKind type, const char* structName)](#oh_arkui_querymoduleinterfacebyname) | 需调用该函数初始化C-API环境，并获取指定类型的Native模块接口集合。 |
| [const char* OH_ArkUI_NativeModule_GetErrorMessage()](#oh_arkui_nativemodule_geterrormessage) | 获取最新的错误消息，该消息包含错误码、方法名称及错误原因。 当其他接口返回错误码时，会保存对应的错误信息， 通过此接口可获取当前存储的错误消息。 此接口返回的信息可能随版本演进，仅用于输出以辅助分析和定位问题， 不得用于逻辑判断。<br> 返回的字符串为系统创建的全局字符串，可能被其他线程修改。调用方不能对其内容进行修改，如果有对齐编辑的需要，自行创建字符串拷贝内容。无需调用方进行内存释放。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_SetRuntimeCheckMode(OH_ArkUI_NativeModule_RuntimeCheckType checkType, OH_ArkUI_NativeModule_RuntimeCheckMode mode)](#oh_arkui_nativemodule_setruntimecheckmode) | 设置ArkUI C API的进程级运行时检查模式。<br> 本函数配置特定运行时检查类型在检测到误用时的行为。 该设置为进程级，在针对同一检查类型的下一次成功调用之前持续有效。<br> <b>线程要求：</b>本函数必须在UI线程上调用。 从其他线程调用将立即终止应用程序，不会返回。 线程检查在参数校验之前执行。<br> <b>默认行为：</b>如果未针对某个检查类型调用本函数， debug应用构建默认为ARKUI_RUNTIME_CHECK_MODE_CRASH， release应用构建默认为ARKUI_RUNTIME_CHECK_MODE_DISABLED。 |

## 枚举类型说明

### ArkUI_NativeAPIVariantKind

```c
enum ArkUI_NativeAPIVariantKind
```

**描述：**

定义Native接口集合类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_NATIVE_NODE | UI组件相关接口类型，详见[native_node.h](capi-native-node-h.md)中的结构体类型定义。 |
| ARKUI_NATIVE_DIALOG | 弹窗相关接口类型，详见[native_dialog.h](capi-native-dialog-h.md)中的结构体类型定义。 |
| ARKUI_NATIVE_GESTURE | 手势相关接口类型，详见[native_gesture.h](capi-native-gesture-h.md)中的结构体类型定义。 |
| ARKUI_NATIVE_ANIMATE | 动画相关接口类型，详见[native_animate.h](capi-native-animate-h.md)中的结构体类型定义。 |
| ARKUI_MULTI_THREAD_NATIVE_NODE |  |

### OH_ArkUI_NativeModule_RuntimeCheckType

```c
enum OH_ArkUI_NativeModule_RuntimeCheckType
```

**描述：**

ArkUI C API的运行时检查类型枚举。<br> 每种检查类型对应一种ArkUI C API的不当使用场景，用于在运行时检测开发者 对C API的误用行为（如跨线程调用、访问已销毁对象等）。 可通过[OH_ArkUI_NativeModule_SetRuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_setruntimecheckmode)为每种检查类型 独立配置运行时检查模式，检查失败时的行为由所配置的运行时检查模式决定，模式取值见[OH_ArkUI_NativeModule_RuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_NATIVEMODULE_CHECK_TYPE_UI_THREAD = 0 | UI线程检查类型：部分ArkUI C API要求必须在UI线程调用， 此类型用于检测这些API是否被非UI线程调用。<br>**起始版本：** 26.1.0 |
| OH_ARKUI_NATIVEMODULE_CHECK_TYPE_NODE_DISPOSED = 1 | 节点销毁检查类型：检测传递给C API的ArkUI_NodeHandle是否已经被销毁。<br>**起始版本：** 26.1.0 |
| OH_ARKUI_NATIVEMODULE_CHECK_TYPE_ATTRIBUTE_MATCH = 2 | 属性匹配检查类型：检测传递给SetAttribute/GetAttribute/ResetAttribute的 ArkUI_NodeAttributeType是否与节点实际组件类型匹配。<br>**起始版本：** 26.1.0 |
| OH_ARKUI_NATIVEMODULE_CHECK_TYPE_MULTI_THREAD = 3 | 多线程竞争检查类型：检测调用多线程API时，是否已有其他线程 正在操作同一棵组件树。<br>**起始版本：** 26.1.0 |

### OH_ArkUI_NativeModule_RuntimeCheckMode

```c
enum OH_ArkUI_NativeModule_RuntimeCheckMode
```

**描述：**

ArkUI C API运行时检查的模式枚举。<br> 所有C API的运行时检查类型均使用本枚举中定义的相同模式集合（DISABLED、LOG、CRASH）设置检查失败时的行为， 即每种检查类型都可以独立设置为以下三种模式之一。 默认模式取决于应用程序的构建类型： 以debug模式编译的应用（DevEco Studio中Debug构建，用于开发调试） 默认为[OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode)， 以release模式编译的应用（DevEco Studio中Release构建，用于正式发布） 默认为[OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED = 0 | 禁用指定的运行时检查。C API行为与引入该检查之前一致。<br>**起始版本：** 26.1.0 |
| OH_ARKUI_NATIVEMODULE_CHECK_MODE_LOG = 1 | 打印诊断日志（检查类型、API名称、原因、native堆栈）并继续C API调用。<br>**起始版本：** 26.1.0 |
| OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH = 2 | 打印诊断日志并立即终止应用程序。<br>**起始版本：** 26.1.0 |


## 函数说明

### OH_ArkUI_QueryModuleInterfaceByName()

```c
void* OH_ArkUI_QueryModuleInterfaceByName(ArkUI_NativeAPIVariantKind type, const char* structName)
```

**描述：**

需调用该函数初始化C-API环境，并获取指定类型的Native模块接口集合。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NativeAPIVariantKind](capi-native-interface-h.md#arkui_nativeapivariantkind) type | 表示ArkUI提供的Native接口集合大类，例如<b>ARKUI_NATIVE_NODE</b>、<b>ARKUI_NATIVE_GESTURE</b>。 |
| const char* structName | 表示Native接口结构体的名称，可通过查询对应头文件内的结构体定义获取， 例如<arkui/native_node.h>中的<b>ArkUI_NativeNodeAPI_1</b>。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| void* | 返回Native接口抽象指针，在转换为具体类型后进行使用。 |

### OH_ArkUI_NativeModule_GetErrorMessage()

```c
const char* OH_ArkUI_NativeModule_GetErrorMessage()
```

**描述：**

获取最新的错误消息，该消息包含错误码、方法名称及错误原因。 当其他接口返回错误码时，会保存对应的错误信息， 通过此接口可获取当前存储的错误消息。 此接口返回的信息可能随版本演进，仅用于输出以辅助分析和定位问题， 不得用于逻辑判断。<br> 返回的字符串为系统创建的全局字符串，可能被其他线程修改。调用方不能对其内容进行修改，如果有对齐编辑的需要，自行创建字符串拷贝内容。无需调用方进行内存释放。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| -- | -- |
| const char* | 返回最新的错误信息。 |

### OH_ArkUI_NativeModule_SetRuntimeCheckMode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_SetRuntimeCheckMode(OH_ArkUI_NativeModule_RuntimeCheckType checkType, OH_ArkUI_NativeModule_RuntimeCheckMode mode)
```

**描述：**

设置ArkUI C API的进程级运行时检查模式。<br> 本函数配置特定运行时检查类型在检测到误用时的行为。 该设置为进程级，在针对同一检查类型的下一次成功调用之前持续有效。<br> <b>线程要求：</b>本函数必须在UI线程上调用。 从其他线程调用将立即终止应用程序，不会返回。 线程检查在参数校验之前执行。<br> <b>默认行为：</b>如果未针对某个检查类型调用本函数， debug应用构建默认为ARKUI_RUNTIME_CHECK_MODE_CRASH， release应用构建默认为ARKUI_RUNTIME_CHECK_MODE_DISABLED。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_NativeModule_RuntimeCheckType](capi-native-interface-h.md#oh_arkui_nativemodule_runtimechecktype) checkType | [入参] 指定要配置的运行时检查类型， 取值为[OH_ArkUI_NativeModule_RuntimeCheckType](capi-native-interface-h.md#oh_arkui_nativemodule_runtimechecktype)中的枚举值。 |
| [OH_ArkUI_NativeModule_RuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode) mode | [入参] 指定运行时检查模式，取值为[OH_ArkUI_NativeModule_RuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode)中的枚举值。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | 返回值：<ul><li>设置更新成功返回ARKUI_ERROR_CODE_NO_ERROR。</li><li>checkType或mode无效时返回ARKUI_ERROR_CODE_PARAM_INVALID。</li></ul> *     返回无效参数错误时，保留之前的设置。 |


