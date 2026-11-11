# ArkUI NDK稳定性检测
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

## 简介

从API版本26.1.0开始，ArkUI NDK接口提供稳定性检测能力，帮助定位子线程调用UI接口、节点销毁后使用（Use-After-Free，简称UAF）、属性与组件类型不匹配和多线程竞争的问题。本文介绍配置ArkUI NDK稳定性检测的方法、检测场景说明，以及约束与限制。

## 配置ArkUI NDK稳定性检测

开发者可在UI线程中、待检测的ArkUI NDK接口调用之前，调用[OH_ArkUI_NativeModule_SetRuntimeCheckMode](../reference/apis-arkui/capi-native-interface-h.md#oh_arkui_nativemodule_setruntimecheckmode)，为指定检测类型设置处理模式。检测类型用于区分需要检查的误用场景，检测模式决定是否启用检测及发现误用后的处理方式，具体取值分别参见[OH_ArkUI_NativeModule_RuntimeCheckType](../reference/apis-arkui/capi-native-interface-h.md#oh_arkui_nativemodule_runtimechecktype)和[OH_ArkUI_NativeModule_RuntimeCheckMode](../reference/apis-arkui/capi-native-interface-h.md#oh_arkui_nativemodule_runtimecheckmode)。

支持的检测类型如下：

| 检测类型 | 枚举值 | 检测内容 |
| --- | --- | --- |
| [UI线程检测](#ui线程检测) | OH_ARKUI_NATIVEMODULE_CHECK_TYPE_UI_THREAD | 检测要求在UI线程调用的ArkUI NDK接口是否被非UI线程调用。 |
| [节点销毁检测](#节点销毁检测) | OH_ARKUI_NATIVEMODULE_CHECK_TYPE_NODE_DISPOSED | 检测传入ArkUI NDK接口的节点句柄是否指向已销毁的节点。 |
| [属性匹配检测](#属性匹配检测) | OH_ARKUI_NATIVEMODULE_CHECK_TYPE_ATTRIBUTE_MATCH | 检测[setAttribute](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)、[getAttribute](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)和[resetAttribute](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)传入的属性是否与节点的实际组件类型匹配。 |
| [多线程竞争检测](#多线程竞争检测) | OH_ARKUI_NATIVEMODULE_CHECK_TYPE_MULTI_THREAD | 检测调用多线程ArkUI NDK接口时，是否有其他线程正在操作同一棵游离组件树。 |

各检测类型均支持设置以下检测模式：

| 检测模式 | 枚举值 | 行为说明 |
| --- | --- | --- |
| OH_ARKUI_NATIVEMODULE_CHECK_MODE_DISABLED | 0 | 关闭指定类型的检测。 |
| OH_ARKUI_NATIVEMODULE_CHECK_MODE_LOG | 1 | 检测到误用时，输出诊断日志和调用堆栈，随后继续执行ArkUI NDK接口调用。 |
| OH_ARKUI_NATIVEMODULE_CHECK_MODE_CRASH | 2 | 检测到误用时，输出诊断日志和调用堆栈，并立即终止应用程序。 |

## 检测场景说明

ArkUI NDK稳定性检测通过HiLog输出诊断信息，可在DevEco Studio的HiLog窗口搜索ArkUI runtime check。日志包含checkName（检测类型）、apiName（触发检测的接口名称）和reason（错误原因）。以下日志格式中，冒号后的中文说明表示运行时的实际值：

```text
ArkUI runtime check hit. checkName: 检测类型, apiName: 接口名称, reason: 错误原因
```

对于UI线程检测、节点销毁检测和属性匹配检测，CRASH模式还会输出以下终止信息：

```text
ArkUI runtime check abort. checkName: 检测类型, apiName: 接口名称, reason: 错误原因
```

如果这三类检测的崩溃由未显式配置的debug默认CRASH模式触发，诊断末尾还会附加以下提示，说明默认崩溃的来源和配置入口。显式设置CRASH模式时，不附加该提示。

```text
This crash is enabled by default in debug builds. To disable it, call OH_ArkUI_NativeModule_SetRuntimeCheckMode. For guidance on fixing this issue, visit the official developer website.
```

排查时，先根据checkName确定检测类型，再结合apiName、reason和调用堆栈定位具体调用。下面分别说明四类检测的报错含义和处理方法。

### UI线程检测

当日志中的checkName为UI_THREAD时，表示当前ArkUI NDK接口调用不满足UI线程要求。

reason字段输出以下信息：

```text
C API must be called on the UI thread
```

根据日志中的apiName和native调用堆栈，定位子线程中的接口调用，将该调用调度到所属UI线程执行。需要并行构建UI时，请参考[NDK多线程创建组件](ndk-build-on-multi-thread.md)，使用多线程ArkUI NDK接口并遵守其使用约束。

### 节点销毁检测

当日志中的checkName为NODE_DISPOSED时，表示传入的节点被识别为已销毁。reason字段会根据节点在当前操作中的角色输出以下信息之一：

```text
Node has been disposed
Parent node has been disposed
Child node has been disposed
Sibling node has been disposed
```

上述信息分别表示传入节点、父节点、子节点或作为插入参照的兄弟节点被识别为已销毁。

根据apiName、调用堆栈和reason中的节点角色，检查对应节点的生命周期，定位节点销毁后仍使用旧句柄或重复销毁的调用路径。

调用[disposeNode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#disposenode)后，应清空业务侧持有的句柄，清理缓存中的别名引用，并取消或阻止异步回调继续使用旧句柄。仅将一个局部变量置空不能使其他副本失效。

### 属性匹配检测

当日志中的checkName为ATTRIBUTE_MATCH时，表示传入属性与节点的实际组件类型不匹配。该检测覆盖[setAttribute](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)、[getAttribute](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute)和[resetAttribute](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute)。

检测到属性错配时，reason字段输出以下信息。nodeType和attribute分别表示实际节点类型和属性类型的十进制枚举值：

```text
Attribute does not match node type. nodeType: 节点类型枚举值, attribute: 属性类型枚举值
```

例如，向Image节点设置Text专属的NODE_TEXT_CONTENT会触发属性匹配诊断。

根据日志中的nodeType和attribute，对照[ArkUI_NodeType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodetype)和[ArkUI_NodeAttributeType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeattributetype)，确认属性适用的组件，改用匹配的节点或属性。

### 多线程竞争检测

当日志中的checkName为MULTI_THREAD时，表示调用多线程ArkUI NDK接口时，其他线程尚未完成对同一棵游离组件树的操作。多线程ArkUI NDK接口的使用方式及约束请参见[NDK多线程创建组件](ndk-build-on-multi-thread.md)。

诊断日志中的reason为Same component tree is already operated by another thread。日志还包含nodeId（触发检测的节点ID）、stateId（冲突操作的状态标识）、currentThreadId（当前调用线程ID）和ownerThreadId（正在操作该组件树的线程ID），格式如下：

```text
ArkUI runtime check hit. checkName: MULTI_THREAD, apiName: 接口名称, reason: Same component tree is already operated by another thread, nodeId: 节点ID, stateId: 冲突操作状态标识, currentThreadId: 当前线程ID, ownerThreadId: 正在操作该组件树的线程ID
```

CRASH模式下的终止信息格式如下：

```text
ArkUI runtime check abort. checkName: MULTI_THREAD, apiName: 接口名称, stateId: 冲突操作状态标识, currentThreadId: 当前线程ID, ownerThreadId: 正在操作该组件树的线程ID
```

根据apiName、nodeId和线程ID定位冲突调用，将对同一棵树的操作安排在同一线程顺序执行，或在业务侧同步，确保前一次调用结束后再执行下一次调用。

同一棵游离组件树中的不同节点也不能由多个线程同时操作；需要并行构建时，应将任务分配到相互独立的组件树。

## 约束与限制

- UI线程检测只针对要求在UI线程执行的接口。
- 节点销毁检测针对传入的[ArkUI_NodeHandle](../reference/apis-arkui/capi-arkui-nativemodule-arkui-node8h.md)句柄，不等同于通用内存检测工具。
- 属性匹配检测用于发现可能引发崩溃的组件类型与属性错配，不代替属性值、参数数量和接口支持性的校验。
- 多线程竞争检测只针对多线程ArkUI NDK接口调用，不代替业务侧的线程同步。
