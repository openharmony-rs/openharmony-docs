# 注入实例级交互命令
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @lushi871202 -->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

从26.1.0版本开始，可通过[OH_ArkUI_NativeModule_UIEventInjectRelaxedInteraction](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectrelaxedinteraction)向当前应用内的指定UI实例注入点击、内容切换、滚动、返回和按键命令，适用于应用内智能体和UI自动化。调用方提供实例句柄和JSON命令，由框架确定执行目标，无需提供节点ID。本接口不支持跨应用注入。

## 调用流程

1. 在目标节点所属UI线程通过[OH_ArkUI_GetContextByNode](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_getcontextbynode)获取实例句柄。获取后的有效句柄可用于从任意线程发起注入；调用期间须保证句柄自身不被销毁。
2. 构造包含schemaVersion和cmd的JSON字符串，使用[OH_ArkUI_NativeModule_UIJsonWrapperCreate](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappercreate)创建命令对象。检查创建结果，成功后调用注入接口。
3. 检查注入接口的同步返回值。返回0表示请求已受理，执行结果通过完成回调报告；返回401或190001表示请求被拒绝，不执行命令，也不触发回调。
4. 注入函数返回后，调用[OH_ArkUI_NativeModule_UIJsonWrapperDestroy](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy)释放命令对象。完成回调可设为NULL；需要结果时，须保持回调及userData有效直至回调退出。

## 命令格式

顶层必须为JSON对象，schemaVersion必须为数字1，cmd必须为对象，type区分大小写。每次请求只接受以下五类命令，不支持fallback_cmd。

```json
{"schemaVersion":1,"cmd":{"type":"click","mode":"auto","action_info":{"coordinates":{"x1":100,"y1":200}}}}
```

所有坐标均相对目标实例窗口，单位为物理像素（px）；distance也以物理像素为单位。坐标不使用vp或屏幕全局坐标。缺少必填字段、字段类型或取值非法时，注入接口同步返回401。

### 点击（click）

| 字段 | 必填 | 说明 |
| -- | -- | -- |
| cmd.mode | 否 | auto（默认）：先尝试调用命中组件的点击能力，失败后尝试模拟触摸；target：仅调用命中组件的点击能力；simulating：模拟触摸按下和抬起。 |
| cmd.action_info.coordinates.x1、y1 | 是 | 数字，点击位置的横、纵坐标。 |

```json
{"schemaVersion":1,"cmd":{"type":"click","mode":"simulating","action_info":{"coordinates":{"x1":100,"y1":200}}}}
```

### 内容切换（content_switch）

| 字段 | 必填 | 说明 |
| -- | -- | -- |
| cmd.mode | 是 | 必须显式传入target。 |
| cmd.action_info.coordinates.pos.x、y | 是 | 数字，用于定位内容切换目标的横、纵坐标。 |
| cmd.action_info.direction | 否 | forward（默认）或backward，分别表示向后或向前切换内容。 |
| cmd.action_info.count | 否 | 正整数，切换次数，默认1。 |

```json
{"schemaVersion":1,"cmd":{"type":"content_switch","mode":"target","action_info":{"coordinates":{"pos":{"x":100,"y":200}},"direction":"forward","count":1}}}
```

### 滚动（scroll）

| 字段 | 必填 | 说明 |
| -- | -- | -- |
| cmd.mode | 否 | auto（默认）：先调用目标组件的滚动能力，失败后尝试模拟滑动；target：仅调用目标组件的滚动能力；simulating：模拟触摸滑动。 |
| cmd.action_info.coordinates.x1、y1 | 是 | 数字，滚动定位点或模拟滑动起点的横、纵坐标。 |
| cmd.action_info.coordinates.x2、y2 | 否 | 数字，模拟滑动的终点。两者均提供时使用该终点；缺少任一分量时，按起点、direction和distance生成完整终点。已提供的分量仍须为数字。 |
| cmd.action_info.direction | 否 | forward（默认）、backward、left、right、up或down，表示内容滚动方向。 |
| cmd.action_info.distance | 否 | 非负数字，内容滚动距离。默认使用目标实例窗口高度的三分之一；窗口高度不可用时，按显示信息或设备物理高度计算。 |

模拟滑动时，触摸移动方向与内容滚动方向相反：left时终点x增加，right时终点x减少，backward或up时终点y增加，forward或down时终点y减少。显式提供完整终点时，模拟轨迹使用该终点。

```json
{"schemaVersion":1,"cmd":{"type":"scroll","mode":"simulating","action_info":{"coordinates":{"x1":200,"y1":500},"direction":"forward","distance":300}}}
```

### 返回（backpress）

不需要mode或action_info，向目标实例派发返回操作。

```json
{"schemaVersion":1,"cmd":{"type":"backpress"}}
```

### 按键（key）

| 字段 | 必填 | 说明 |
| -- | -- | -- |
| cmd.action_info.code | 是 | 有效的整数键码，参见[KeyCode](../reference/apis-input-kit/js-apis-keycode.md#keycode)。例如2017表示A键。 |

向目标实例依次派发按键按下和抬起事件，任一事件被处理即报告成功，两者均未处理时报告COMMAND_NOT_SUPPORTED。

```json
{"schemaVersion":1,"cmd":{"type":"key","action_info":{"code":2017}}}
```

## 处理执行结果

注入接口的同步返回值与完成回调的result是两套不同的结果。同步返回0不能用于判断组件是否响应命令。callback非NULL时，执行完成后在目标实例的UI线程回调一次，result使用[OH_ArkUI_NativeModule_UIEventInjection_ResultCode](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjection_resultcode)。

| result枚举项 | 值 | 含义 |
| -- | -- | -- |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_SUCCESS | 0 | 命令派发及即时处理成功，不表示动画、绘制或页面展示已经完成。 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_TARGET_NOT_FOUND | 1 | 无法找到执行目标，或请求受理后目标实例失效。 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_COMMAND_NOT_SUPPORTED | 2 | 命令结构有效，但当前UI状态不支持执行该命令。 |
| OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_INTERRUPTED_BY_USER | 3 | 尚未完成的命令被真实用户操作中断。 |

UI线程发起调用时，回调在注入函数返回后执行；其他线程发起时，回调可能在注入函数返回前执行。因此，userData必须在发起调用前准备好。不要将跨调用后失效的栈变量作为userData，也不要在UI线程阻塞等待回调。

多个请求可同时提交，但不保证执行或回调顺序。若后续命令依赖前一命令的结果，可在前一命令的回调中提交；若依赖动画或页面变化，还需通过相应业务事件确认页面已满足条件。

接口不提供主动取消或固定完成超时。实例销毁不会取消已受理请求的完成通知：尚未完成的请求报告TARGET_NOT_FOUND，已判定用户中断的请求仍报告INTERRUPTED_BY_USER。通知依赖UI线程继续处理任务；UI任务运行环境退出时不承诺通知时限，调用方须同步运行环境关闭及回调退出后再释放相关资源。

## 调用示例

以下C++示例向已取得有效句柄的实例注入一次点击。使用前，须确保目标页面在窗口坐标（100，200）处有可响应点击的组件。示例通过日志区分同步受理结果和异步执行结果，不包含组件创建过程。

```cpp
#include <arkui/ui_event_injection.h>
#include <arkui/ui_json_wrapper.h>
#include <cstdint>
#include <cstdio>

static void OnInjectionFinished(OH_ArkUI_NativeModule_UIEventInjection_ResultCode result, void *userData)
{
    (void)userData;
    switch (result) {
        case OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_SUCCESS:
            std::printf("Click completed\n");
            break;
        case OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_TARGET_NOT_FOUND:
            std::printf("Target unavailable\n");
            break;
        case OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_COMMAND_NOT_SUPPORTED:
            std::printf("Command not supported\n");
            break;
        case OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_INTERRUPTED_BY_USER:
            std::printf("Interrupted by user\n");
            break;
    }
}

ArkUI_ErrorCode InjectClick(ArkUI_ContextHandle uiContext)
{
    const char json[] =
        R"({"schemaVersion":1,"cmd":{"type":"click","mode":"auto","action_info":{"coordinates":{"x1":100,"y1":200}}}})";
    OH_ArkUI_NativeModule_UIJsonWrapper *command = nullptr;
    ArkUI_ErrorCode result = OH_ArkUI_NativeModule_UIJsonWrapperCreate(
        json, static_cast<uint32_t>(sizeof(json) - 1), &command);
    if (result != ARKUI_ERROR_CODE_NO_ERROR) {
        std::printf("Create command failed: %d\n", static_cast<int>(result));
        return result;
    }

    result = OH_ArkUI_NativeModule_UIEventInjectRelaxedInteraction(
        uiContext, command, OnInjectionFinished, nullptr);
    OH_ArkUI_NativeModule_UIJsonWrapperDestroy(command);
    if (result != ARKUI_ERROR_CODE_NO_ERROR) {
        std::printf("Injection rejected: %d\n", static_cast<int>(result));
    }
    return result;
}
```

在工程的CMakeLists.txt中链接libace_ndk.z.so，并将示例所在源文件加入构建目标。entry为示例动态库目标名，使用时替换为工程的实际目标名。

```cmake
target_link_libraries(entry PUBLIC libace_ndk.z.so)
```
