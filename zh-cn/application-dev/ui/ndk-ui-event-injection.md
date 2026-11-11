---
kits: ["ArkUI"]
description: "介绍如何使用NDK接口向指定UI实例的目标节点异步注入UI控制命令,适用于应用内智能体与UI自动化场景。"
keywords: [UI事件注入, NDK, 命令注入, 智能体, UI自动化, C API]
doctype: guide
status: active
---

# UI事件注入(C/C++)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @lushi871202-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

UI事件注入接口为应用内智能体(In-App Agent)与UI自动化场景提供UI控制能力:应用可通过C API向指定UI实例的目标节点异步注入控制命令(点击、滚动、内容切换、返回、按键),命令执行结果通过完成回调异步返回。注入命令以JSON描述,表达"在何处执行何种高层意图",由系统决策具体执行方式。

## 约束与前提

| 约束项 | 说明 |
| --- | --- |
| 版本要求 | 接口始于 26.1.0,使用前需确认设备支持。 |
| 注入范围 | 仅支持向本应用自身的UI实例注入,不支持跨应用注入。 |
| 线程要求 | 调用方必须处于目标`uiContext`所在UI线程;检测到线程违规将触发致命错误(fatal abort)。 |
| 并发限制 | 同一进程内同一时刻仅接受一条命令:命令被接受后、完成回调触发前,其他有效请求均返回`ARKUI_ERROR_CODE_COMMAND_UNFINISHED`。回调中可再次注入。 |
| 取消与超时 | 接口不提供取消操作,也没有固定的完成超时;调用方自行等待超时不会取消已接受的命令,也不会阻止回调触发。 |
| 实例销毁 | UI实例销毁不取消已接受请求的完成回调。 |
| 坐标语义 | 坐标相对当前窗口,单位为物理像素(px)。 |

## 接口说明

| 接口 | 说明 |
| --- | --- |
| [OH_ArkUI_NativeModule_UIEventInjectCompositeCommand](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectcompositecommand) | 向目标UI节点异步注入控制命令,是本能力的唯一入口。 |
| [OH_ArkUI_NativeModule_UIJsonWrapperCreate](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappercreate) | 从JSON字符串创建命令数据对象。 |
| [OH_ArkUI_NativeModule_UIJsonWrapperDestroy](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy) | 销毁命令数据对象并释放资源。 |
| [OH_ArkUI_NodeUtils_GetNodeUniqueId](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeutils_getnodeuniqueid) | 获取目标节点的唯一ID,作为注入接口的`uniqueId`入参。 |

命令执行结果通过[OH_ArkUI_NativeModule_UIEventInjectionCallback](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectioncallback)回调返回,取值为[OH_ArkUI_NativeModule_UIEventInjection_ResultCode](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjection_resultcode)枚举。

## 命令格式

命令JSON的顶层结构固定为:

```json
{
    "schemaVersion": 1,
    "cmd": {
        "type": "<命令类型>",
        "mode": "<执行模式,可选>",
        "action_info": { ... }
    }
}
```

顶层`schemaVersion`字段必填,当前取值为`1`;缺失或版本不支持时命令被拒绝。`cmd.type`支持以下五类命令:

| 命令类型 | mode(可选值) | action_info关键字段 | 说明 |
| --- | --- | --- | --- |
| click | auto(默认)/ simulating / target | `coordinates.x1`、`coordinates.y1`(必填) | 点击指定坐标。 |
| scroll | auto(默认)/ simulating / target | `coordinates.x1`、`coordinates.y1`(必填);`coordinates.x2`、`coordinates.y2`(可选,滚动终点) | 从起点向终点滚动。 |
| content_switch | target(必填) | `coordinates.pos.x`、`coordinates.pos.y`(必填);`direction`(forward(默认)/ backward,可选) | 在指定位置执行内容切换(如翻页)。 |
| backpress | 不涉及 | 不涉及 | 执行返回操作。 |
| key | 不涉及 | `code`(必填,整数键码) | 注入按键事件。 |

各命令JSON示例如下:

```json
// click:点击(100, 200)
{ "schemaVersion": 1, "cmd": { "type": "click", "mode": "auto",
    "action_info": { "coordinates": { "x1": 100.0, "y1": 200.0 } } } }

// scroll:从(100, 200)滚动到(100, 400)
{ "schemaVersion": 1, "cmd": { "type": "scroll", "mode": "auto",
    "action_info": { "coordinates": { "x1": 100.0, "y1": 200.0, "x2": 100.0, "y2": 400.0 } } } }

// content_switch:在(100, 200)处向前切换内容
{ "schemaVersion": 1, "cmd": { "type": "content_switch", "mode": "target",
    "action_info": { "coordinates": { "pos": { "x": 100.0, "y": 200.0 } }, "direction": "forward" } } }

// backpress:返回
{ "schemaVersion": 1, "cmd": { "type": "backpress" } }

// key:注入键码为2049的按键
{ "schemaVersion": 1, "cmd": { "type": "key", "action_info": { "code": 2049 } } }
```

命令JSON非法(如非合法JSON、缺少必填字段、命令类型未知)时,注入接口同步返回`ARKUI_ERROR_CODE_PARAM_INVALID`,不触发回调。

## 开发步骤

### 添加动态链接库

在CMakeLists.txt中链接`libace_ndk.z.so`:

```Text
target_link_libraries(entry PUBLIC libace_ndk.z.so)
```

### 头文件

```C++
#include <arkui/ui_event_injection.h>
#include <arkui/ui_json_wrapper.h>
#include <arkui/native_node.h>
```

### 完整示例

以向当前UI实例的某目标节点注入一次点击为例:

```C++
// 1. 定义完成回调:每个被接受的请求在发起线程(UI线程)上恰好回调一次
static void OnInjectionResult(OH_ArkUI_NativeModule_UIEventInjection_ResultCode result, void* userData)
{
    // result为执行结果:SUCCESS(0)、TARGET_NOT_FOUND(1)、COMMAND_NOT_SUPPORTED(2)、INTERRUPTED_BY_USER(3)
    int* finished = static_cast<int*>(userData); // userData由调用方管理,回调返回前须保持有效
    if (finished != nullptr) {
        *finished = 1;
    }
}

// 2. 获取目标节点的uniqueId(本示例中targetNode为已获取的ArkUI_NodeHandle)
int32_t nodeId = -1;
if (OH_ArkUI_NodeUtils_GetNodeUniqueId(targetNode, &nodeId) != 0) {
    return; // 获取失败,处理错误
}

// 3. 构造命令JSON并创建命令数据对象(JSON内部会被拷贝)
const char* json = R"({"schemaVersion":1,"cmd":{"type":"click","mode":"auto",)"
                  R"("action_info":{"coordinates":{"x1":100.0,"y1":200.0}}}})";
OH_ArkUI_NativeModule_UIJsonWrapper* command = nullptr;
ArkUI_ErrorCode ret = OH_ArkUI_NativeModule_UIJsonWrapperCreate(json, strlen(json), &command);
if (ret != ARKUI_ERROR_CODE_NO_ERROR || command == nullptr) {
    return; // JSON非法或内存分配失败,command为nullptr
}

// 4. 注入命令(须在目标uiContext的UI线程调用)
int finished = 0;
ret = OH_ArkUI_NativeModule_UIEventInjectCompositeCommand(
    uiContext, static_cast<uint32_t>(nodeId), command, OnInjectionResult, &finished);

// 5. 注入接口返回后命令JSON已被内部拷贝,可立即销毁命令对象
OH_ArkUI_NativeModule_UIJsonWrapperDestroy(command);

if (ret != ARKUI_ERROR_CODE_NO_ERROR) {
    return; // 请求被同步拒绝,不会触发回调
}
// 6. 等待回调通知执行结果(finished在回调中被置位)
```

上述示例中,`uiContext`为目标UI实例的`ArkUI_ContextHandle`,`targetNode`为目标节点句柄。注入接口返回`ARKUI_ERROR_CODE_NO_ERROR`仅代表请求被接受,最终执行结果以回调中的`result`为准。

## 结果与错误处理

注入接口的同步返回值与回调结果码含义不同,需分别处理:

**同步返回值(请求是否被接受):**

| 返回值 | 说明 |
| --- | --- |
| ARKUI_ERROR_CODE_NO_ERROR | 请求被接受,执行结果经回调返回。 |
| ARKUI_ERROR_CODE_PARAM_INVALID | 命令对象为空、命令数据非法、回调为空或提交失败。 |
| ARKUI_ERROR_CODE_NODE_NOT_FOUND | uniqueId在目标UI实例中无法解析到节点。 |
| ARKUI_ERROR_CODE_UI_CONTEXT_INVALID | uiContext为空,或对应UI实例正在销毁、已失效。 |
| ARKUI_ERROR_CODE_COMMAND_UNFINISHED | 前序命令尚未完成(进程内同一时刻仅接受一条命令)。解除限制后可重试。 |

**回调结果码(命令执行结果):**

| 结果码 | 说明 |
| --- | --- |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_SUCCESS | 命令执行成功。 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_TARGET_NOT_FOUND | 未找到可响应命令的组件或目标(如坐标未命中任何组件)。 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_COMMAND_NOT_SUPPORTED | 命令在当前UI状态下不可执行(如目标所需的执行模式无法定位)。 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_INTERRUPTED_BY_USER | 命令被用户操作中断。 |

**生命周期注意事项:**

- 命令JSON在注入接口返回前即被拷贝,返回后调用方可立即销毁`command`对象;若调用方在回调中复用同一命令,需重新创建命令对象。
- `callback`被接受后必须保持可调用,直到其返回;调用方等待超时也不会解除该要求。
- `userData`由调用方管理,框架仅透传指针,不访问、不拷贝、不释放;请求被接受后至回调返回前,非空的`userData`须保持有效。

## 相关资料

- [ui_event_injection.h API参考](../reference/apis-arkui/capi-ui-event-injection-h.md)
- [ui_json_wrapper.h API参考](../reference/apis-arkui/capi-ui-json-wrapper-h.md)
- [NDK UI开发概述](ndk-build-ui-overview.md)
