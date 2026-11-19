# 注入控件命令

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @lushi871202-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

从API版本26.1.0开始，应用可以向自身UI实例中的目标节点注入控件命令。

本指南说明从节点定位到效果验证的命令注入流程；命令参数与组件行为见附录[控件命令参数与行为](ndk-ui-appendix.md#控件命令参数与行为)。

阅读时，建议先了解[约束与限制](#约束与限制)，再查阅[接口说明](#接口说明)和[控件命令格式](#控件命令格式)，最后参照[开发步骤](#开发步骤)完成接入。

> **说明：**
>
> - 本篇示例仅提供核心接口的调用方法，完整的示例工程请参考<!--RP1-->[UI信息采集和交互注入示例工程](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection)<!--RP1End-->。

## 约束与限制

调用前应确认目标实例、线程和节点有效性，并按下列要求管理请求及回调。

> **说明：**
>
> 目标实例、线程和节点有效性的可行确认方式：
>
> - **目标实例**：上下文从当前页面的[UIContext](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md)获取，获取与复用限制见[管理上下文生命周期](ndk-ui-info-collect-tree.md#管理上下文生命周期)，不跨实例缓存；实例失效时注入接口同步返回[ARKUI_ERROR_CODE_UI_CONTEXT_INVALID](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)，应重新获取有效实例的上下文后再提交。
> - **线程**：在目标实例的UI线程上调用。可行方式是从ArkTS页面事件（如onClick）中发起调用，页面事件回调在UI线程执行，正常提交示例见[注入控件命令](#注入控件命令)；注入接口检测到线程违规会终止进程，该错误无法通过返回值确认或补救，只能通过调用来源保证。
> - **节点**：注入前从最新一次采集结果中定位目标节点并读取整数节点ID，页面变化后重新采集定位；节点失效时注入接口同步返回[ARKUI_ERROR_CODE_NODE_NOT_FOUND](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)，应重新定位后再决定是否提交，处理建议见[处理返回值](#处理返回值)。

- 在目标Context的UI线程调用注入接口，非UI线程调用会终止进程；线程要求见[OH_ArkUI_NativeModule_UIEventInjectCompositeCommand](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectcompositecommand)的参数说明。
- uniqueId必须属于传入的Context，具体见[OH_ArkUI_NativeModule_UIEventInjectCompositeCommand](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectcompositecommand)的参数说明。应从当前树结果或节点查询接口取得整数ID，不使用组件`.id()`的字符串值代替。
- 同一进程内，前一条命令完成前提交的新请求会返回[ARKUI_ERROR_CODE_COMMAND_UNFINISHED](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)；限制解除时机与重试规则见[OH_ArkUI_NativeModule_UIEventInjectCompositeCommand](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectcompositecommand)的返回值说明。
- 完成回调报告命令的即时处理结果，回调语义见[OH_ArkUI_NativeModule_UIEventInjectionCallback](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectioncallback)。验证最终效果时使用组件已有业务回调或后续业务操作，不阻塞UI线程等待。
- 已受理请求的完成回调可能在实例销毁后到达；userData的所有权与有效性规则见[OH_ArkUI_NativeModule_UIEventInjectCompositeCommand](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectcompositecommand)的参数说明，不能因页面退出提前释放。

## 接口说明

控件命令注入关键接口如下表所示。具体API说明详见API参考[ui_event_injection.h](../reference/apis-arkui/capi-ui-event-injection-h.md)和[ui_json_wrapper.h](../reference/apis-arkui/capi-ui-json-wrapper-h.md)。JSONWrapper对象的构造、创建、读取和销毁统一见[UI信息数据格式说明](ndk-ui-info-data-structure.md)。

**表1** 控件命令注入接口功能介绍

| 接口名 | 描述 |
| --- | --- |
| [OH_ArkUI_NativeModule_UIJsonWrapperCreate](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappercreate) | 从JSON字符串创建JSONWrapper对象。 |
| [OH_ArkUI_NativeModule_UIEventInjectCompositeCommand](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectcompositecommand) | 向指定Context中的节点提交一条异步命令。 |
| [OH_ArkUI_NativeModule_UIJsonWrapperDestroy](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy) | 销毁应用拥有的JSONWrapper对象。 |

## 控件命令格式

本节说明公共JSON结构、命令选择方法和使用建议。详细命令参数、组件行为和边界规则统一见附录[控件命令参数与行为](ndk-ui-appendix.md#控件命令参数与行为)。

### JSONWrapper对象格式

每次请求使用一个JSON对象描述一条命令：顶层为协议版本字段`schemaVersion`（固定取值1）和命令对象`cmd`；`cmd`包含命令类型`type`和命令参数`action_info`，即使命令不需要额外参数，也需保留空的`action_info`对象。顶层结构与固定字段、业务字段的公共说明见[UI信息数据格式说明](ndk-ui-info-data-structure.md#jsonwrapper对象格式)。

以下以设置文本命令setText为例：

```json
{
  "schemaVersion": 1,
  "cmd": {
    "type": "setText",
    "action_info": {
      "value": "示例文本"
    }
  }
}
```

样例中各字段的含义：

| 字段 | 类别 | 含义 |
|---|---|---|
| `schemaVersion` | 固定字段 | 协议版本，固定取值1。 |
| `cmd` | 业务字段 | 命令对象，承载命令类型和参数。 |
| `cmd.type` | 业务字段 | 命令类型字符串，取值为支持的命令名，本例为setText。 |
| `cmd.action_info` | 业务字段 | 命令参数对象；即使命令不需要额外参数，也需保留空对象。 |
| `cmd.action_info.value` | 业务字段 | setText的必填参数：要设置的文本内容；空字符串表示将内容设置为空。 |

各命令业务参数的必填与可选定义见附录[控件命令参数与行为](ndk-ui-appendix.md#控件命令参数与行为)。

### 命令选择

根据目标组件和操作目的，在附录[控件命令参数与行为](ndk-ui-appendix.md#控件命令参数与行为)中查阅支持的命令、必填和可选参数、边界行为。文本索引、越界处理和业务拦截规则因组件而异，构造action_info前应确认对应说明。

### 命令使用建议

在连续编辑、选择、复制或切换内容时，按以下要求管理前置条件、请求顺序和资源。

- 缺少必填字段或字段类型不符时，请求会被拒绝，返回值语义见[OH_ArkUI_NativeModule_UIEventInjectCompositeCommand](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectcompositecommand)的返回值说明。
- 整数参数必须是有符号32位范围内的JSON整数，不能传入字符串或小数；可选字段省略与传入`null`含义不同，通用约定见[控件命令参数与行为](ndk-ui-appendix.md#控件命令参数与行为)。
- 文本位置按目标组件的索引语义处理，不是UTF-8字节偏移；TextInput、TextArea使用UTF-16文本位置。
- 参数类型校验不等于组件范围校验。负数、超出文本长度或超出子项数量的参数，按各命令的组件规则处理。
- 提交前检查目标组件类型和当前状态。格式正确的命令发给不支持该命令的组件，也会在执行阶段失败，例如向Text提交setText。
- 使用当前内容长度和子项数量校验参数，不依赖不同组件的越界回退规则。尤其不要把RichEditor的选区规则用于TextInput，也不要把Tabs的索引规则用于Swiper。
- 有前后依赖的命令应分步执行。设置文本后需先确认内容变更，再按新长度选择；Text 组件的文本选择可能依赖布局完成，因此即使收到注入完成回调，也不能立即假定已满足复制条件。
- 复制不会自动选择全部文本。需先建立有效选区，并检查组件复制配置和业务回调；完成结果不返回剪贴板数据。
- `setText`、`addText` 等修改可能受输入过滤、长度限制或业务回调影响。[OH_ARKUI_NATIVE_MODULE_UI_EVENT_INJECTION_RESULT_SUCCESS](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjection_resultcode) 仅表示组件已处理该命令，不保证传入的所有字符均已按原样显示。
- 只对明确被拒绝的请求，在修正条件后决定是否重试。请求已受理但尚未观察到界面变化时，不要直接重新提交addText、deleteText等命令，以免重复修改内容。

## 开发步骤

通用NDK接入、ArkTS与Native桥接及构建配置见[基于NDK构建UI概述](ndk-build-ui-overview.md)和[接入ArkTS页面](ndk-access-the-arkts-page.md)。以下基于UI信息采集和交互注入示例工程，说明如何定位目标节点，以及如何提交控件命令并处理结果；代码片段需结合完整工程使用。

### 定位目标节点

打开示例工程，选择需要操作的组件。页面为当前目标设置统一的字符串标识commandTarget。提交时通过控件树查找该标识，读取真实整数节点ID，再使用同一个[UIContext](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md)提交命令。

节点定位逻辑可以参考[采集控件树信息](ndk-ui-info-collect-tree.md#解析结果并从页面调用)中的解析与查找函数。页面变化后应重新定位，不缓存旧节点ID作为长期有效引用；上下文获取与复用仍需遵循[管理上下文生命周期](ndk-ui-info-collect-tree.md#管理上下文生命周期)中的限制。

### 构造控件命令

示例的 `InjectCommand` 是自行定义的NAPI桥接函数。它读取 Context、节点 ID 和 JSON 字符串，创建 `JSONWrapper` 对象后调用公开接口，并在调用返回后销毁自建 `JSONWrapper` 对象。示例中 64 KiB 的命令大小限制仅为应用层示例约束，并非平台本身新增的规格限制。

Arguments、ReadNodeId、GetContext、AddPending、RejectSubmission及参数计数与下标常量等辅助定义均位于同一源文件中。它们分别处理桥接参数、上下文复用和Promise任务，不属于SDK新增接口。

<!-- @[ui_command_inject_native](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/cpp/napi_init.cpp) -->

``` C++
napi_value InjectCommand(napi_env env, napi_callback_info info)
{
    napi_value args[3];
    if (!Arguments(env, info, COMMAND_ARG_COUNT, args)) {
        return nullptr;
    }
    int32_t nodeId = 0;
    if (!ReadNodeId(env, args[NODE_ID_ARG], nodeId)) {
        return nullptr;
    }
    size_t length = 0;
    if (napi_get_value_string_utf8(env, args[COMMAND_ARG], nullptr, 0, &length) != napi_ok ||
        length == 0 || length > MAX_COMMAND_BYTES) {
        napi_throw_range_error(env, nullptr, "Sample command must contain 1 to 65536 UTF-8 bytes");
        return nullptr;
    }
    std::vector<char> bytes(length + 1);
    size_t copied = 0;
    if (napi_get_value_string_utf8(env, args[COMMAND_ARG], bytes.data(), bytes.size(), &copied) != napi_ok) {
        return nullptr;
    }
    auto context = GetContext(env, args[CONTEXT_ARG]);
    if (!context) {
        return nullptr;
    }
    OH_ArkUI_NativeModule_UIJsonWrapper* command = nullptr;
    auto code = OH_ArkUI_NativeModule_UIJsonWrapperCreate(bytes.data(), static_cast<uint32_t>(copied), &command);
    if (code != ARKUI_ERROR_CODE_NO_ERROR) {
        return Throw(env, "JSON creation", code);
    }

    napi_value promise = nullptr;
    auto token = AddPending(env, promise);
    if (token) {
        code = OH_ArkUI_NativeModule_UIEventInjectCompositeCommand(context, static_cast<uint32_t>(nodeId), command,
            OnCommand, reinterpret_cast<void*>(token));
        RejectSubmission(token, code);
    }
    OH_ArkUI_NativeModule_UIJsonWrapperDestroy(command);
    return promise;
}
```

### 处理完成回调

同一文件中的OnCommand接收[OH_ArkUI_NativeModule_UIEventInjectionCallback](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectioncallback)参数，把执行结果写入示例的CommandResult对象，并通过`napi_resolve_deferred`兑现`injectCommand`返回的Promise，ArkTS侧await的代码随即拿到执行结果。Promise与deferred的桥接机制见[使用Node-API接口处理异步操作](../napi/use-napi-about-promise.md)。TakePending用于取出当前请求对应的示例业务任务，避免将迟到结果交给已经退出的页面。

<!-- @[ui_command_completion](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/cpp/napi_init.cpp) -->

``` C++
void OnCommand(OH_ArkUI_NativeModule_UIEventInjection_ResultCode resultCode, void* userData)
{
    auto job = TakePending(reinterpret_cast<uintptr_t>(userData));
    if (!job) {
        return;
    }
    napi_env env = job->owner->env;
    napi_handle_scope scope = nullptr;
    if (napi_open_handle_scope(env, &scope) != napi_ok) {
        return;
    }
    napi_value result = nullptr;
    if (napi_create_object(env, &result) == napi_ok && NumberProperty(env, result, "result", resultCode)) {
        napi_resolve_deferred(env, job->deferred, result);
    } else {
        Reject(job, "command bridge", -1);
    }
    napi_close_handle_scope(env, scope);
}
```

### 注入控件命令

示例的 `injectCommand` 返回 `Promise<CommandResult>`，其中 `result` 字段用于返回异步回调的执行结果，而非注入接口的同步返回值。`CommandResult` 和 `UIContext` 的定义及导入见示例文件。

<!-- @[ui_command_bridge_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/cpp/types/libentry/Index.d.ts) -->

``` TypeScript
export const injectCommand: (context: UIContext, nodeId: number, command: string) => Promise<CommandResult>;
```

示例的submit方法从页面事件发起请求。collectTree、parseTree、requireNodeId及failure的导入和页面状态定义位于示例完整工程中，以下片段摘自该方法。

<!-- @[ui_command_submit_ets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/ets/pages/CommandPage.ets) -->

``` TypeScript
private async submit(): Promise<void> {
  if (this.busy) { return; }
  this.busy = true;
  this.status = 'pending';
  try {
    const context = this.getUIContext();
    const tree = parseTree(nativeUi.collectTree(context, FULL_TREE));
    const id = requireNodeId(tree, 'commandTarget');
    const value = await nativeUi.injectCommand(context, id, this.command);
    if (this.active) { this.status = `result=${value.result}; node=${id}`; }
  } catch (error) {
    if (this.active) { this.status = failure(error); }
  } finally {
    if (this.active) { this.busy = false; }
  }
}
```

示例通过异常路径处理参数或提交阶段失败，通过CommandResult.result显示异步执行结果。页面操作采用串行提交，并另行显示目标文本或选中索引，用于核对实际业务效果。

创建JSONWrapper对象、提交命令和执行完成是三个阶段。排查时先确定失败发生在哪个阶段。错误码和结果码的定义分别见[ArkUI_ErrorCode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)与[OH_ArkUI_NativeModule_UIEventInjection_ResultCode](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjection_resultcode)。

创建JSONWrapper对象的返回值和参数处理见[处理创建返回值](ndk-ui-info-data-structure.md#处理创建返回值)。对象创建失败时不继续提交命令；下文专门说明命令提交及执行结果。

### 处理返回值

命令注入接口的直接返回值用于判断请求是否受理。请求受理后，命令将进入异步执行流程。应用应先记录提交结果，再等待完成回调，切勿在提交后立即认为文字修改或动画已完成。

| 处理场景             | 应用侧判断                                            | 建议处理                                                               |
| ---------------------- | ------------------------------------------------------- | ------------------------------------------------------------------------ |
| 请求参数或命令不适用 | 命令格式、参数、目标组件或组件状态不满足要求。        | 按附录核对参数和目标组件，修正条件后再决定是否提交。                   |
| 目标或Context无效    | 节点已销毁、节点不属于当前Context，或页面实例已退出。 | 在当前有效实例中重新获取Context和节点，不向旧实例重试。                |
| 前一条命令尚未完成   | 同一进程内仍有未完成请求。                            | 等前一条命令完成后再决定是否提交，不循环重试或阻塞UI线程。             |

从非目标UI线程调用会终止进程（见[约束与限制](#约束与限制)），不属于上述可通过返回值处理的失败；不能依靠捕获异常或等待错误码来补救跨线程调用。

命令执行完成后，框架通过完成回调报告执行结果，结果码的定义和取值见[OH_ArkUI_NativeModule_UIEventInjection_ResultCode](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjection_resultcode)。命令处理完成时，部分场景（如追加空字符串、删除空范围、RichEditor 无焦点时执行选择、Tabs 无子项时切换等）可能不会产生预期的内容变化。因此，应通过组件内容、选区或索引等实际业务状态来判断目标是否达成。可分别检查请求返回值、执行日志和组件的最终内容进行核对。例如，对至少包含两项的 Swiper、Tabs 提交索引切换命令后，应以最终选中项为核对依据，切勿将回调结果等同于绘制、复制或动画完成证明。

| 处理场景           | 开发者可能遇到的情况                                                                           | 建议处理                                                                                           |
| -------------------- | ------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------- |
| 目标在执行前失效   | 提交时目标存在，但执行前节点被移除、页面退出，或目标与指定实例的关联发生变化。                 | 重新获取当前实例和目标节点，再判断是否需要提交新请求；与提交阶段的节点不存在错误分开记录。         |
| 命令无法由组件处理 | 命令与组件不匹配，或组件状态、边界和配置不满足执行条件。                                       | 根据目标类型、参数和组件状态逐项检查，修正条件后再决定是否提交新请求。                             |

自定义userData时，接口仅保留指针值，所有权与有效性要求见[OH_ArkUI_NativeModule_UIEventInjectionCallback](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectioncallback)的参数说明。

## 常见问题

以下问题用于区分组件业务事件、注入完成回调和最终界面效果，避免在条件未满足时重复提交。

### 为什么不能在组件回调内立即提交下一条命令

前一条命令可能仍在执行，组件自身的回调不等于注入接口的完成回调。应等待注入完成回调，或在后续独立业务操作中提交。

### 为什么复制命令执行后没有预期内容

复制依赖有效选区和组件的复制配置。先通过目标组件确认选区，再提交复制命令。切勿将注入完成回调的结果等同于剪贴板内容的读取结果。
