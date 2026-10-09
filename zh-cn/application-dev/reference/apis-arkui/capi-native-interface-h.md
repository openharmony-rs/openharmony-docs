# native_interface.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

提供NativeModule接口的统一入口函数，用于初始化C-API环境、获取指定类型的Native模块接口集合，以及获取最新一次的报错信息。

**引用文件：** <arkui/native_interface.h>

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**相关示例：** <!--RP1-->[NativeNodeInterfaceSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/NativeNodeInterfaceSample)<!--RP1End-->

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_NativeAPIVariantKind](#arkui_nativeapivariantkind) | ArkUI_NativeAPIVariantKind | 定义Native接口集合类型。 |
| [OH_ArkUI_NativeModule_RuntimeCheckType](#oh_arkui_nativemodule_runtimechecktype) | OH_ArkUI_NativeModule_RuntimeCheckType | ArkUI C API的运行时检查类型枚举。<br>每种检查类型对应一种ArkUI C API的不当使用场景，用于在运行时检测开发者对C API的误用行为（如跨线程调用、访问已销毁对象等）。可通过[OH_ArkUI_NativeModule_SetRuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_setruntimecheckmode)为每种检查类型独立配置运行时检查模式，检查失败时的行为由所配置的运行时检查模式决定，模式取值见[OH_ArkUI_NativeModule_RuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode)。 |
| [OH_ArkUI_NativeModule_RuntimeCheckMode](#oh_arkui_nativemodule_runtimecheckmode) | OH_ArkUI_NativeModule_RuntimeCheckMode | ArkUI C API运行时检查的模式枚举。<br>所有C API的运行时检查类型均使用本枚举中定义的相同模式集合设置检查失败时的行为，即每种检查类型都可以独立设置为以下三种模式之一。默认模式取决于应用程序的构建类型：以debug模式构建的应用默认为[OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode)，以release模式构建的应用默认为[OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode)。 |

### 函数

| 名称  | 描述   |
|--------------|-----------|
| [void* OH_ArkUI_QueryModuleInterfaceByName(ArkUI_NativeAPIVariantKind type, const char* structName)](#oh_arkui_querymoduleinterfacebyname) | 需调用该函数初始化C-API环境，并获取指定类型的Native模块接口集合。 |
| [const char* OH_ArkUI_NativeModule_GetErrorMessage()](#oh_arkui_nativemodule_geterrormessage) | 获取最新一次的报错信息，包括错误码、方法名称和错误原因。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_SetRuntimeCheckMode(OH_ArkUI_NativeModule_RuntimeCheckType checkType, OH_ArkUI_NativeModule_RuntimeCheckMode mode)](#oh_arkui_nativemodule_setruntimecheckmode) | 设置ArkUI C API的进程级运行时检查模式。<br>本函数配置特定运行时检查类型在检测到误用时的行为。该设置为进程级，在针对同一检查类型的下一次成功调用之前持续有效。<br>线程要求：本函数必须在UI线程上调用。从其他线程调用将立即终止应用程序，不会返回。线程检查在参数校验之前执行。<br>默认行为：如果未针对某个检查类型调用本函数，debug应用构建默认为[OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode)，<br>release应用构建默认为[OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode)。 |

### 宏定义

| 名称  | 描述   |
|--------------|-----------|
| [OH_ArkUI_GetModuleInterface(nativeAPIVariantKind, structType, structPtr)](#oh_arkui_getmoduleinterface)      | 初始化C-API环境，并基于结构体类型获取对应结构体指针。 |

## 枚举类型说明

### ArkUI_NativeAPIVariantKind

```c
enum ArkUI_NativeAPIVariantKind
```

**描述：**


定义Native接口集合类型。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_NATIVE_NODE = 0 | UI组件相关接口类型，详见[native_node.h](./capi-native-node-h.md)中的[结构体](./capi-native-node-h.md#结构体)类型定义。 |
| ARKUI_NATIVE_DIALOG = 1 | 弹窗相关接口类型，详见[native_dialog.h](./capi-native-dialog-h.md)中的[结构体](./capi-native-dialog-h.md#结构体)类型定义。 |
| ARKUI_NATIVE_GESTURE = 2 | 手势相关接口类型，详见[native_gesture.h](./capi-native-gesture-h.md)中的[结构体](./capi-native-gesture-h.md#结构体)类型定义。 |
| ARKUI_NATIVE_ANIMATE = 3 | 动画相关接口类型，详见[native_animate.h](./capi-native-animate-h.md)中的[结构体](./capi-native-animate-h.md#结构体)类型定义。 |
| ARKUI_MULTI_THREAD_NATIVE_NODE = 4 | 多线程UI组件相关接口类型，详见[native_node.h](./capi-native-node-h.md)中的[结构体](./capi-native-node-h.md#结构体)类型定义。<br>**起始版本：** 22 |

### OH_ArkUI_NativeModule_RuntimeCheckType

```c
enum OH_ArkUI_NativeModule_RuntimeCheckType
```

**描述：**

ArkUI C API的运行时检查类型枚举。<br>每种检查类型对应一种ArkUI C API的不当使用场景，用于在运行时检测开发者对C API的误用行为（如跨线程调用、访问已销毁对象等）。可通过[OH_ArkUI_NativeModule_SetRuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_setruntimecheckmode)为每种检查类型独立配置运行时检查模式，检查失败时的行为由所配置的运行时检查模式决定，模式取值见[OH_ArkUI_NativeModule_RuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode)。

**起始版本：** 26.2.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_NATIVEMODULE_CHECK_TYPE_UI_THREAD = 0 | UI线程检查类型：部分ArkUI C API要求必须在UI线程调用，此类型用于检测这些API是否被非UI线程调用。 |
| OH_ARKUI_NATIVEMODULE_CHECK_TYPE_NODE_DISPOSED = 1 | 节点销毁检查类型：检测传递给C API的[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)是否已经被销毁。 |

### OH_ArkUI_NativeModule_RuntimeCheckMode

```c
enum OH_ArkUI_NativeModule_RuntimeCheckMode
```

**描述：**

ArkUI C API运行时检查的模式枚举。<br>所有C API的运行时检查类型均使用本枚举中定义的相同模式集合设置检查失败时的行为，即每种检查类型都可以独立设置为以下三种模式之一。默认模式取决于应用程序的构建类型：以debug模式构建的应用默认为[OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode)，以release模式构建的应用默认为[OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode)。

**起始版本：** 26.2.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED = 0 | 禁用指定的运行时检查。C API行为与引入该检查之前一致。 |
| OH_ARKUI_NATIVEMODULE_CHECK_MODE_LOG = 1 | 打印诊断日志（检查类型、API名称、原因、native堆栈）并继续C API调用。 |
| OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH = 2 | 打印诊断日志并立即终止应用程序。 |

## 函数说明

### OH_ArkUI_QueryModuleInterfaceByName()

```c
void* OH_ArkUI_QueryModuleInterfaceByName(ArkUI_NativeAPIVariantKind type, const char* structName)
```

**描述：**


需调用该函数初始化C-API环境，并获取指定类型的Native模块接口集合。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NativeAPIVariantKind](#arkui_nativeapivariantkind) type | ArkUI提供的Native接口集合大类，例如UI组件接口类：ARKUI_NATIVE_NODE，手势类：ARKUI_NATIVE_GESTURE。 |
| const char* structName | Native接口结构体的名称，可通过查询对应头文件内的结构体定义获取，例如位于[native_node.h](./capi-native-node-h.md)中的"ArkUI_NativeNodeAPI_1"。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| void* | 返回Native接口抽象指针，在转换为具体类型后进行使用。 |

### OH_ArkUI_GetModuleInterface()

```c
#define OH_ArkUI_GetModuleInterface(nativeAPIVariantKind, structType, structPtr)                     \
do {                                                                                                 \
        void* anyNativeAPI = OH_ArkUI_QueryModuleInterfaceByName(nativeAPIVariantKind, #structType); \
        if (anyNativeAPI) {                                                                          \
            structPtr = (structType*)(anyNativeAPI);                                                 \
        }                                                                                            \
    } while (0)                                                                      
```

**描述：**


初始化C-API环境，并基于结构体类型获取对应结构体指针。

适用于已确定Native接口集合类型和接口结构体类型，需要获取具体Native接口结构体指针以调用ArkUI Native C API的场景。此宏函数接收[ArkUI_NativeAPIVariantKind](#arkui_nativeapivariantkind)类型枚举参数nativeAPIVariantKind、结构体类型参数structType、结构体指针变量structPtr；structPtr需与structType类型匹配。该宏调用[OH_ArkUI_QueryModuleInterfaceByName](#oh_arkui_querymoduleinterfacebyname)初始化C-API环境并获取Native接口抽象指针，转换为structType\*类型后赋值给structPtr。

**起始版本：** 12

### OH_ArkUI_NativeModule_GetErrorMessage()

```c
const char* OH_ArkUI_NativeModule_GetErrorMessage()
```

**描述：**

获取最新一次的报错信息，包括错误码、方法名称和错误原因。错误码相关信息请参考[ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)。当其他接口返回错误码时，会保存对应的报错信息，通过此接口可获取当前存储的报错信息。返回的字符串是由系统创建的线程局部全局字符串，不得修改其内容。如需任何编辑，请自行创建字符串内容的副本。该接口返回的信息可能随版本演进而变化，仅用于输出以辅助分析与故障排查，不应作为逻辑判断依据。返回的报错信息无需手动释放。

**起始版本：** 26.0.0

**返回：**

| 类型 | 说明 |
| -- | -- |
| const char* | 最新一次的报错信息，包括错误码、方法名称和错误原因。 |

### OH_ArkUI_NativeModule_SetRuntimeCheckMode()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_SetRuntimeCheckMode(OH_ArkUI_NativeModule_RuntimeCheckType checkType, OH_ArkUI_NativeModule_RuntimeCheckMode mode)
```

**描述：**

设置ArkUI C API的进程级运行时检查模式。<br>本函数配置特定运行时检查类型在检测到误用时的行为。该设置为进程级，在针对同一检查类型的下一次成功调用之前持续有效。<br>线程要求：本函数必须在UI线程上调用。从其他线程调用将立即终止应用程序，不会返回。线程检查在参数校验之前执行。<br>默认行为：如果未针对某个检查类型调用本函数，debug应用构建默认为[OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode)，<br>release应用构建默认为[OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode)。

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_NativeModule_RuntimeCheckType](capi-native-interface-h.md#oh_arkui_nativemodule_runtimechecktype) checkType | [入参] 指定要配置的运行时检查类型，取值为[OH_ArkUI_NativeModule_RuntimeCheckType](capi-native-interface-h.md#oh_arkui_nativemodule_runtimechecktype)中的枚举值。 |
| [OH_ArkUI_NativeModule_RuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode) mode | [入参] 指定运行时检查模式，取值为[OH_ArkUI_NativeModule_RuntimeCheckMode](capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode)中的枚举值。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | 返回值：<br>设置更新成功返回[ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)。<br>checkType或mode无效时返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)。<br>返回无效参数错误时，保留之前的设置。 |
