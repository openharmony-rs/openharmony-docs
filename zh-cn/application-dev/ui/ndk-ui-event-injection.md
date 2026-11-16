---
kits: ["ArkUI"]
description: "介绍如何使用NDK接口向指定UI实例异步注入非精确目标的交互命令,适用于应用内智能体与UI自动化场景。"
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

UI事件注入接口为应用内智能体(In-App Agent)与UI自动化场景提供UI控制能力:应用可通过C API向指定UI实例异步注入非精确目标的交互命令(点击、滚动、内容切换、返回、按键)。命令以JSON描述,表达"在何处执行何种高层意图",不针对特定组件,由系统依据执行模式决定具体执行方式;命令执行结果通过完成回调异步返回。

## 约束与前提

| 约束项 | 说明 |
| --- | --- |
| 版本要求 | 接口始于 26.1.0,使用前需确认设备支持。 |
| 注入范围 | 仅支持向本应用自身的UI实例注入,不支持跨应用注入。 |
| 线程要求 | 接口线程安全,可从任意线程调用,不会阻塞调用线程。 |
| 并发与取消 | 多条命令可入队执行,执行顺序不保证;接口不提供取消操作,也没有固定的完成超时。 |
| 实例失效 | 命令被接受后,若UI实例失效,回调返回TARGET_NOT_FOUND。 |
| 回调时序 | 每个被接受的请求在注入函数返回后,在原UI线程恰好回调一次;回调通知命令的派发结果和组件的即时处理结果,不等待渲染或动画完成。 |
| 坐标语义 | 坐标相对当前窗口,单位为物理像素(px)。 |

## 接口说明

| 接口 | 说明 |
| --- | --- |
| [OH_ArkUI_NativeModule_UIEventInjectRelaxedInteraction](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectrelaxedinteraction) | 异步向UI实例注入非精确目标的交互命令,是本能力的唯一入口。 |
| [OH_ArkUI_NativeModule_UIJsonWrapperCreate](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappercreate) | 从JSON字符串创建命令数据对象。 |
| [OH_ArkUI_NativeModule_UIJsonWrapperDestroy](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy) | 销毁命令数据对象并释放资源。 |

命令执行结果通过[OH_ArkUI_NativeModule_UIEventInjectionCallback](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectioncallback)回调返回,取值为[OH_ArkUI_NativeModule_UIEventInjection_ResultCode](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjection_resultcode)枚举;回调为可选参数,不需要结果通知时可传NULL。

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

顶层`schemaVersion`字段必填且取值为`1`。`cmd.type`仅支持以下五类命令,未知命令类型会被拒绝:

| 命令类型 | mode(可选值) | action_info关键字段 | 说明 |
| --- | --- | --- | --- |
| click | auto(默认)/ simulating / target | `coordinates.x1`、`coordinates.y1`(必填) | 点击指定坐标。 |
| scroll | auto(默认)/ simulating / target | `coordinates.x1`、`coordinates.y1`(必填);`coordinates.x2`、`coordinates.y2`(可选,滚动终点);`direction`(forward(默认)/ backward / left / right / up / down,可选);`distance`(非负物理像素值,默认为窗口高度的1/3,可选) | 从起点向终点滚动;终点不完整时,按`direction`和`distance`推导默认轨迹。 |
| content_switch | target(必填) | `coordinates.pos.x`、`coordinates.pos.y`(必填);`direction`(forward(默认)/ backward,可选);`count`(正整数,默认1,可选) | 在指定位置切换内容(如翻页)。 |
| backpress | 不涉及 | 不涉及 | 执行返回操作。 |
| key | 不使用mode字段,传入时不影响执行 | `code`(必填,须为有效键码) | 注入按键事件。 |

除标注必填外,`action_info`中的字段均为可选。所有位置坐标均相对窗口,单位为物理像素(px)。

`mode`表示命令的执行方式,仅对支持`mode`的命令(click、scroll、content_switch)生效,取值如下:

| 执行模式 | 说明 |
| --- | --- |
| auto(默认) | 由系统决策执行方式:优先定位坐标命中的组件直接执行,未命中时降级为派发模拟触摸事件。 |
| simulating | 不定位组件,直接构造并派发完整触摸事件序列(按下、移动、抬起)完成操作。 |
| target | 直接触发坐标命中组件的手势;未命中组件时,回调返回TARGET_NOT_FOUND。 |

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

命令JSON非法(如非合法JSON、缺少必填字段或数值超出有效范围)时,注入接口同步返回`ARKUI_ERROR_CODE_PARAM_INVALID`,命令不会被执行,也不触发回调。

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
```

### 完整示例

以向当前UI实例注入一次点击为例:

```C++
// 1. 定义完成回调:每个被接受的请求在注入函数返回后,在原UI线程恰好回调一次
//    (回调为可选参数,不需要结果通知时注入接口的callback可传NULL)
static void OnInjectionResult(OH_ArkUI_NativeModule_UIEventInjection_ResultCode result, void* userData)
{
    // result为执行结果:SUCCESS(0)、TARGET_NOT_FOUND(1)、COMMAND_NOT_SUPPORTED(2)、INTERRUPTED_BY_USER(3)
    int* finished = static_cast<int*>(userData); // userData由调用方管理,回调返回前须保持有效
    if (finished != nullptr) {
        *finished = 1;
    }
}

// 2. 构造命令JSON并创建命令数据对象
const char* json = R"({"schemaVersion":1,"cmd":{"type":"click","mode":"auto",)"
                  R"("action_info":{"coordinates":{"x1":100.0,"y1":200.0}}}})";
OH_ArkUI_NativeModule_UIJsonWrapper* command = nullptr;
ArkUI_ErrorCode ret = OH_ArkUI_NativeModule_UIJsonWrapperCreate(json, strlen(json), &command);
if (ret != ARKUI_ERROR_CODE_NO_ERROR || command == nullptr) {
    return; // JSON非法或内存分配失败,command为nullptr
}

// 3. 注入命令(接口线程安全,可在任意线程调用,不会阻塞)
int finished = 0;
ret = OH_ArkUI_NativeModule_UIEventInjectRelaxedInteraction(uiContext, command, OnInjectionResult, &finished);

// 4. 命令JSON在注入接口返回前已被内部拷贝,返回后可立即销毁命令对象
OH_ArkUI_NativeModule_UIJsonWrapperDestroy(command);

if (ret != ARKUI_ERROR_CODE_NO_ERROR) {
    return; // 请求被同步拒绝,不会触发回调
}
// 5. 等待回调通知执行结果(finished在回调中被置位)
```

上述示例中,`uiContext`为目标UI实例的`ArkUI_ContextHandle`。注入接口返回`ARKUI_ERROR_CODE_NO_ERROR`仅代表命令入队成功,最终执行结果以回调中的`result`为准。

## 结果与错误处理

注入接口的同步返回值与回调结果码含义不同,需分别处理:

**同步返回值(命令是否入队成功):**

| 返回值 | 说明 |
| --- | --- |
| ARKUI_ERROR_CODE_NO_ERROR | 命令入队成功,执行结果经回调返回。 |
| ARKUI_ERROR_CODE_PARAM_INVALID | 参数无效或缺少必填字段。 |
| ARKUI_ERROR_CODE_UI_CONTEXT_INVALID | UI上下文无效。 |

**回调结果码(命令执行结果):**

| 结果码 | 说明 |
| --- | --- |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_SUCCESS | 命令执行成功。 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_TARGET_NOT_FOUND | 未找到能够响应注入命令的组件或目标,例如无法定位执行模式所需的目标,或命令被接受后UI实例已失效。 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_COMMAND_NOT_SUPPORTED | 命令结构有效,但当前UI状态不支持该命令的类型或执行模式。 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_INTERRUPTED_BY_USER | 命令被用户操作中断。 |

**生命周期注意事项:**

- 命令JSON在注入接口返回前即被拷贝;返回后调用方可立即销毁`command`对象。若需再次注入相同命令,须重新创建命令对象。
- `callback`为可选参数;传入非NULL回调时,请求被接受后回调须保持可调用,直到其返回。
- `userData`由调用方管理,框架仅透传指针,不访问、不拷贝、不释放;请求被接受后至回调返回前,非空的`userData`须保持有效。
- 多条命令可入队执行,执行顺序不保证;接口不提供取消操作。

## 相关资料

- [ui_event_injection.h API参考](../reference/apis-arkui/capi-ui-event-injection-h.md)
- [ui_json_wrapper.h API参考](../reference/apis-arkui/capi-ui-json-wrapper-h.md)
- [NDK UI开发概述](ndk-build-ui-overview.md)
