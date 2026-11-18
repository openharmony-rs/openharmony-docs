# 注入手势命令
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

应用可以通过NDK接口向指定的UI实例注入手势命令，模拟点击、滚动、内容切换、返回和按键等操作。手势命令通过JSON描述，由系统根据执行模式决定如何执行，执行结果通过回调通知。

## 约束与限制

| 约束项 | 说明 |
| --- | --- |
| 版本要求 | 从API版本26.1.0开始支持。 |
| 注入范围 | 只能向本应用的UI实例注入，不支持跨应用。 |
| 线程要求 | 接口线程安全，可以在任意线程调用，不会阻塞调用线程；命令的执行和回调在目标UI实例的UI线程上进行。 |
| 并发与取消 | 可以同时提交多条命令，不保证执行和回调顺序；接口不支持取消。 |
| 实例失效 | 命令被接受后，如果目标UI实例不再可用，回调返回TARGET_NOT_FOUND。 |
| 回调时机 | 回调在命令执行完成时触发一次，不等待组件的延迟效果或渲染完成；在目标UI线程上调用时，回调发生在接口返回之后，在其他线程上调用时，回调可能早于接口返回。 |
| 坐标 | 所有位置坐标相对于窗口，单位为物理像素（px）。 |

## 接口规格

| 接口 | 说明 |
| --- | --- |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIEventInjectRelaxedInteraction(ArkUI_ContextHandle uiContext, const OH_ArkUI_NativeModule_UIJsonWrapper \*command, OH_ArkUI_NativeModule_UIEventInjectionCallback callback, void \*userData)](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectrelaxedinteraction) | 向当前UI实例注入交互命令。 |

各参数的详细说明请参考[ui_event_injection.h](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectrelaxedinteraction)。

命令执行完成后，结果通过回调通知。callback可以为NULL，表示不关注执行结果。

命令通过JSON字符串描述，顶层结构如下。

```json
{
    "schemaVersion": 1,
    "cmd": {
        "type": "<命令类型>",
        "mode": "<执行模式，可选>",
        "action_info": { ... }
    }
}
```

cmd.type支持以下五类命令。

| 命令 | mode取值 | action_info关键字段 | 说明 |
| --- | --- | --- | --- |
| click | auto（默认）/ simulating / target | coordinates.x1、coordinates.y1（必填） | 点击指定坐标。 |
| scroll | auto（默认）/ simulating / target | coordinates.x1、coordinates.y1（必填），x2、y2（可选，滚动终点）；direction（可选，取值forward、backward、left、right、up、down，默认forward）；distance（可选，非负物理像素值，默认为窗口高度的1/3） | 从起点向终点滚动；未指定终点时，按direction和distance确定滚动轨迹。 |
| content_switch | target（必填） | coordinates.pos.x、coordinates.pos.y（必填）；direction（可选，forward或backward，默认forward）；count（可选，正整数，默认1） | 在指定位置切换内容，例如翻页。 |
| backpress | 不涉及 | 不涉及 | 执行返回操作。 |
| key | 不涉及 | code（必填，虚拟键码） | 注入按键事件。 |

未标注必填的字段均为可选。

mode决定命令的执行方式，仅click和scroll使用，content_switch固定为target。

| 执行模式 | 说明 |
| --- | --- |
| auto（默认） | 系统决定执行方式：优先定位坐标处命中的组件并直接执行，未命中时降级为模拟触摸事件。 |
| simulating | 不定位组件，直接派发完整的触摸事件序列（按下、移动、抬起）。 |
| target | 直接触发坐标处命中的组件手势，未命中组件时回调收到TARGET_NOT_FOUND。 |

### 命令示例

点击坐标(100, 200)的示例。

```json
{ "schemaVersion": 1, "cmd": { "type": "click", "mode": "auto",
    "action_info": { "coordinates": { "x1": 100.0, "y1": 200.0 } } } }
```

从(100, 200)滚动到(100, 400)的示例。

```json
{ "schemaVersion": 1, "cmd": { "type": "scroll", "mode": "auto",
    "action_info": { "coordinates": { "x1": 100.0, "y1": 200.0, "x2": 100.0, "y2": 400.0 } } } }
```

在(100, 200)处向前切换内容的示例。

```json
{ "schemaVersion": 1, "cmd": { "type": "content_switch", "mode": "target",
    "action_info": { "coordinates": { "pos": { "x": 100.0, "y": 200.0 } }, "direction": "forward" } } }
```

返回操作的示例。

```json
{ "schemaVersion": 1, "cmd": { "type": "backpress" } }
```

注入Tab键（键码2049）的示例。

```json
{ "schemaVersion": 1, "cmd": { "type": "key", "action_info": { "code": 2049 } } }
```

如果JSON不合法、缺少必填字段或数值超出有效范围，接口同步返回ARKUI_ERROR_CODE_PARAM_INVALID，命令不会执行，也不会触发回调。

### 错误码

同步返回值表示命令是否被接受。

| 返回值 | 说明 |
| --- | --- |
| ARKUI_ERROR_CODE_NO_ERROR | 命令已入队，执行结果通过回调返回。 |
| ARKUI_ERROR_CODE_PARAM_INVALID | command为空、JSON不合法或缺少必填字段、命令投递失败。 |
| ARKUI_ERROR_CODE_UI_CONTEXT_INVALID | uiContext为空，或对应的UI实例不可用。 |

回调结果码表示命令的实际执行结果。

| 结果码 | 说明 |
| --- | --- |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_SUCCESS | 命令执行成功。 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_TARGET_NOT_FOUND | 未找到能响应命令的组件或目标，例如target模式下坐标未命中组件，或命令被接受后UI实例已不可用。 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_COMMAND_NOT_SUPPORTED | 命令本身合法，但当前UI状态下无法执行。 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_INTERRUPTED_BY_USER | 命令被用户操作中断。 |

## 开发步骤

以注入一次点击为例。

```C++
#include <arkui/ui_event_injection.h>
#include <arkui/ui_json_wrapper.h>

// 定义完成回调：命令执行完成后回调一次，result为执行结果
static void OnInjectionResult(OH_ArkUI_NativeModule_UIEventInjection_ResultCode result, void* userData)
{
    int* finished = static_cast<int*>(userData);
    if (finished != nullptr) {
        *finished = 1;
    }
}

// 构造命令JSON并创建命令对象
const char* json = R"({"schemaVersion":1,"cmd":{"type":"click","mode":"auto",)"
                  R"("action_info":{"coordinates":{"x1":100.0,"y1":200.0}}}})";
OH_ArkUI_NativeModule_UIJsonWrapper* command = nullptr;
ArkUI_ErrorCode ret = OH_ArkUI_NativeModule_UIJsonWrapperCreate(json, strlen(json), &command);
if (ret != ARKUI_ERROR_CODE_NO_ERROR || command == nullptr) {
    return; // JSON不合法或内存分配失败
}

// 注入命令
int finished = 0;
ret = OH_ArkUI_NativeModule_UIEventInjectRelaxedInteraction(uiContext, command, OnInjectionResult, &finished);

// JSON在接口返回前已被复制，返回后可立即销毁命令对象
OH_ArkUI_NativeModule_UIJsonWrapperDestroy(command);
if (ret != ARKUI_ERROR_CODE_NO_ERROR) {
    return; // 请求被拒绝，不会触发回调
}
```

示例中的uiContext为目标UI实例的ArkUI_ContextHandle。接口返回ARKUI_ERROR_CODE_NO_ERROR只表示命令已入队，实际执行结果以回调中的result为准。

## 异常处理

接口不支持取消，命令被接受后无法撤销，高频调用时请自行控制频率。同步返回值非ARKUI_ERROR_CODE_NO_ERROR表示命令未被接受，回调结果码非SUCCESS表示命令执行失败，二者需要分别处理。

接口返回前会完成JSON的校验和复制，返回后可以立即销毁命令对象；回调被接受后要保持可调用，用户数据在回调返回前要保持有效。

## 相关资料

- [ui_event_injection.h API参考](../reference/apis-arkui/capi-ui-event-injection-h.md)
- [ui_json_wrapper.h API参考](../reference/apis-arkui/capi-ui-json-wrapper-h.md)
- [NDK UI开发概述](ndk-build-ui-overview.md)
