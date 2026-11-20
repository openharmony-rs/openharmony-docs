# 注入交互命令
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

从API版本26.1.0开始，可以通过[OH_ArkUI_NativeModule_UIEventInjectRelaxedInteraction](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectrelaxedinteraction)接口向指定的UI实例注入交互命令，模拟点击、滚动、内容切换、返回和按键等操作。交互命令通过JSON描述，由系统根据执行模式决定如何执行，执行结果通过回调通知。

## 约束与限制

| 约束项 | 说明 |
| --- | --- |
| 注入范围 | 只能向本应用的UI实例注入，不支持跨应用。 |
| 线程要求 | 接口线程安全，可以在任意线程调用，不会阻塞调用线程；命令的执行和回调在目标UI实例的UI线程上进行。 |
| 并发与取消 | 可以同时提交多条命令，不保证执行和回调顺序；接口不支持取消。 |
| 实例失效 | 命令被接受后，如果目标UI实例不再可用，回调返回[TARGET_NOT_FOUND](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjection_resultcode)。 |
| 回调时机 | 回调在命令执行完成时触发一次，不等待组件的延迟效果或渲染完成；在目标UI线程上调用时，回调发生在接口返回之后，在其他线程上调用时，回调可能早于接口返回。 |
| 坐标 | 所有位置坐标相对于窗口，单位为物理像素（px）。 |

## 接口说明

[OH_ArkUI_NativeModule_UIEventInjectRelaxedInteraction](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectrelaxedinteraction)([ArkUI_ContextHandle](../reference/apis-arkui/capi-arkui-nativemodule-arkui-context8h.md) uiContext, const [OH_ArkUI_NativeModule_UIJsonWrapper](../reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) \*command, [OH_ArkUI_NativeModule_UIEventInjectionCallback](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectioncallback) callback, void \*userData) 向指定的UI实例注入交互命令，各参数的详细说明请参考[ui_event_injection.h](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectrelaxedinteraction)。

命令执行完成后，结果通过回调通知。callback可以为NULL，表示不关注执行结果。

## 交互命令说明

命令通过JSON字符串描述，顶层结构如下。

```json
{
    "schemaVersion": 1,
    "cmd": {
        "type": "<命令类型>",
        "mode": "<执行模式>",
        "action_info": {}
    }
}
```

其中，schemaVersion表示命令格式的版本号，当前固定为1；type表示命令类型；mode表示执行模式，仅click、scroll、content_switch使用；action_info表示命令参数，不同命令的字段不同。

type取值及对应说明如下。

| 命令 | mode取值 | action_info关键字段 | 说明 |
| --- | --- | --- | --- |
| click | auto（默认）、simulating、target | coordinates.x1、coordinates.y1（必填） | 点击指定坐标。 |
| scroll | auto（默认）、simulating、target | coordinates.x1、coordinates.y1（必填），coordinates.x2、coordinates.y2（可选，滚动终点）；direction（可选，取值forward、backward、left、right、up、down，默认forward）；distance（可选，非负物理像素值，默认为窗口高度的1/3） | 从起点向终点滚动。 |
| content_switch | target（必填） | coordinates.pos.x、coordinates.pos.y（必填）；direction（可选，forward或backward，默认forward）；count（可选，正整数，默认1） | 在指定位置切换内容，例如翻页。 |
| backpress | 不涉及 | 不涉及 | 执行返回操作。 |
| key | 不涉及 | code（必填，虚拟键码） | 注入按键事件。 |

click和scroll的mode可选（默认为auto），content_switch的mode必填且只能为target，backpress和key不使用mode。

mode取值及含义如下。

| 执行模式 | 说明 |
| --- | --- |
| auto（默认） | 系统决定执行方式：优先定位坐标处命中的组件并直接执行，未命中时降级为模拟触摸事件。 |
| simulating | 不定位组件，直接派发完整的触摸事件序列（按下、移动、抬起）。 |
| target | 直接触发坐标处命中的组件手势，未命中组件时回调收到[TARGET_NOT_FOUND](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjection_resultcode)。 |

各命令的JSON示例依次如下。

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

如果JSON不合法、缺少必填字段或数值超出有效范围，接口同步返回[ARKUI_ERROR_CODE_PARAM_INVALID](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)，命令不会执行，也不会触发回调。

## 开发步骤

以注入一次点击为例，先引入头文件。

```C++
#include <hilog/log.h>
#include <sstream>
#include <string>
#include <arkui/ui_event_injection.h>
#include <arkui/ui_json_wrapper.h>

#define LOG_DOMAIN 0x0000
#define LOG_TAG "NdkInject"
```

<!-- @[inject_click](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/InjectGestureCommand/entry/src/main/cpp/NativeEntry.cpp) -->

```C++
// 定义完成回调，命令执行完成后回调一次，result为执行结果。
static void OnInjectionResult(OH_ArkUI_NativeModule_UIEventInjection_ResultCode result, void* userData)
{
    OH_LOG_Print(LOG_APP, LOG_INFO, LOG_DOMAIN, LOG_TAG, "injection result: %{public}d",
        static_cast<int>(result));
}

// 通过ArkUI_ContextHandle在指定坐标（相对窗口的物理像素）注入一次点击手势命令。
void InjectClickCommand(ArkUI_ContextHandle uiContext, double x, double y)
{
    // 构造命令JSON并创建命令对象。
    std::ostringstream oss;
    oss << R"({"schemaVersion":1,"cmd":{"type":"click","mode":"auto",)"
        << R"("action_info":{"coordinates":{"x1":)" << x << R"(,"y1":)" << y << R"(}}})";
    std::string json = oss.str();
    OH_ArkUI_NativeModule_UIJsonWrapper* command = nullptr;
    ArkUI_ErrorCode ret = OH_ArkUI_NativeModule_UIJsonWrapperCreate(
        json.c_str(), static_cast<uint32_t>(json.length()), &command);
    if (ret != ARKUI_ERROR_CODE_NO_ERROR || command == nullptr) {
        return; // JSON不合法或内存分配失败。
    }

    // 注入命令。
    ret = OH_ArkUI_NativeModule_UIEventInjectRelaxedInteraction(uiContext, command, OnInjectionResult, nullptr);

    // JSON在接口返回前已被复制，返回后可立即销毁命令对象。
    OH_ArkUI_NativeModule_UIJsonWrapperDestroy(command);
    if (ret != ARKUI_ERROR_CODE_NO_ERROR) {
        return; // 请求被拒绝，不会触发回调。
    }
}
```

示例中uiContext为目标UI实例的ArkUI_ContextHandle，x、y为注入点相对窗口的物理像素坐标。接口返回[ARKUI_ERROR_CODE_NO_ERROR](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)只表示命令已入队，命令执行完成后会触发回调，回调中的result表示实际执行结果。

同步返回值表示命令是否被接受，回调结果码表示命令的实际执行结果，二者含义不同，各取值如下：

- 同步返回值：[ARKUI_ERROR_CODE_NO_ERROR](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)、[ARKUI_ERROR_CODE_PARAM_INVALID](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)、[ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)
- 回调结果码：[SUCCESS](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjection_resultcode)、[TARGET_NOT_FOUND](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjection_resultcode)、[COMMAND_NOT_SUPPORTED](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjection_resultcode)、[INTERRUPTED_BY_USER](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjection_resultcode)

接口返回前会完成JSON的校验和复制，返回后可以立即销毁命令对象；命令被接受后，回调需保持可调用。接口不支持取消，命令被接受后无法撤销，高频调用时请自行控制频率。

## 相关资料

- [ui_event_injection.h](../reference/apis-arkui/capi-ui-event-injection-h.md)
- [ui_json_wrapper.h](../reference/apis-arkui/capi-ui-json-wrapper-h.md)
- [NDK UI开发概述](ndk-build-ui-overview.md)