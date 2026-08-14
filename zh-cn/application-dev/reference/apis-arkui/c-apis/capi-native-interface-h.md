# native_interface.h

## 概述

Provides a unified entry for the native module APIs.

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_NativeAPIVariantKind](#arkui_nativeapivariantkind) | ArkUI_NativeAPIVariantKind | Defines the native API types. |

### 函数

| 名称 | 描述 |
| -- | -- |
| [void* OH_ArkUI_QueryModuleInterfaceByName(ArkUI_NativeAPIVariantKind type, const char* structName)](#oh_arkui_querymoduleinterfacebyname) | Obtains the native API set of a specified type. |
| [const char* OH_ArkUI_NativeModule_GetErrorMessage()](#oh_arkui_nativemodule_geterrormessage) | 获取最新的错误消息，该消息包含错误码、方法名称及错误原因。当其他接口返回错误码时，会保存对应的错误信息，通过此接口可获取当前存储的错误消息。此接口返回的信息可能随版本演进，仅用于输出以辅助分析和定位问题，不得用于逻辑判断。返回的字符串为系统创建的全局字符串，可能被其他线程修改。调用方不能对其内容进行修改，如果有对齐编辑的需要，自行创建字符串拷贝内容。无需调用方进行内存释放。 |
| [ OH_ArkUI_GetModuleInterface(nativeAPIVariantKind, structType, structPtr)](#oh_arkui_getmoduleinterface) | Obtains the macro function corresponding to a struct pointer based on the struct type. |

## 枚举类型说明

### ArkUI_NativeAPIVariantKind

```c
enum ArkUI_NativeAPIVariantKind
```

**描述**

Defines the native API types.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_NATIVE_NODE | API related to UI components. For details, see the struct definition in <arkui/native_node.h>. |
| ARKUI_NATIVE_DIALOG | API related to dialog boxes. For details, see the struct definition in <arkui/native_dialog.h>. |
| ARKUI_NATIVE_GESTURE | API related to gestures. For details, see the struct definition in <arkui/native_gesture.h>. |
| ARKUI_NATIVE_ANIMATE | API related to animations. For details, see the struct definition in <arkui/native_animate.h>. |
| ARKUI_MULTI_THREAD_NATIVE_NODE |  |


## 函数说明

### OH_ArkUI_QueryModuleInterfaceByName()

```c
void* OH_ArkUI_QueryModuleInterfaceByName(ArkUI_NativeAPIVariantKind type, const char* structName)
```

**描述**

Obtains the native API set of a specified type.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NativeAPIVariantKind](capi-native-interface-h.md#arkui_nativeapivariantkind) type | Indicates the type of the native API set provided by ArkUI, for example, <b>ARKUI_NATIVE_NODE</b>and <b>ARKUI_NATIVE_GESTURE</b>. |
| const char* structName | Indicates the name of a native struct defined in the corresponding header file, for example,<b>ArkUI_NativeNodeAPI_1</b> in <arkui/native_node.h>. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| void* | Returns the pointer to the abstract native API, which can be used after being converted into a specific type. |

### OH_ArkUI_NativeModule_GetErrorMessage()

```c
const char* OH_ArkUI_NativeModule_GetErrorMessage()
```

**描述**

获取最新的错误消息，该消息包含错误码、方法名称及错误原因。当其他接口返回错误码时，会保存对应的错误信息，通过此接口可获取当前存储的错误消息。此接口返回的信息可能随版本演进，仅用于输出以辅助分析和定位问题，不得用于逻辑判断。返回的字符串为系统创建的全局字符串，可能被其他线程修改。调用方不能对其内容进行修改，如果有对齐编辑的需要，自行创建字符串拷贝内容。无需调用方进行内存释放。

**起始版本：** 26.0.0

**返回：**

| 类型 | 说明 |
| -- | -- |
| const char* | 返回最新的错误信息。 |

### OH_ArkUI_GetModuleInterface()

```c
OH_ArkUI_GetModuleInterface(nativeAPIVariantKind, structType, structPtr)                     \do {                                                                                             \void* anyNativeAPI = OH_ArkUI_QueryModuleInterfaceByName(nativeAPIVariantKind, #structType) \if (anyNativeAPI) {                                                                          \structPtr = (structType*)(anyNativeAPI)                                                 \}                                                                                            \} while (0)
```

**描述**

Obtains the macro function corresponding to a struct pointer based on the struct type.

**起始版本：** 12


