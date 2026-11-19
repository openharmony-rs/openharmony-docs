# UI信息数据格式说明

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @lushi871202-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

从API版本26.1.0开始，应用可以通过[OH_ArkUI_NativeModule_UIJsonWrapper](../reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md)对象，承载UI采集结果和控件命令，下文简称为JSONWrapper对象。该对象保存一个JSON字符串，本文提供JSON字符串构造方法，以及如何创建、读取和销毁JSONWrapper对象。

JSONWrapper保存UTF-8编码的JSON文本，应用通过接口访问数据。JSONWrapper不是具有固定节点字段的结构体，其中的字段由具体采集或命令协议定义。

> **说明：**
>
> - 本篇示例仅提供核心接口的调用方法，完整的示例工程请参考<!--RP1-->[UI信息采集和交互注入示例工程](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection)<!--RP1End-->。

## 接口说明

JSONWrapper关键接口如下表所示。具体API说明详见API参考[ui_json_wrapper.h](../reference/apis-arkui/capi-ui-json-wrapper-h.md)。

**表1** JSONWrapper接口功能介绍

| 接口名                                                                                                                                     | 描述                                                                                                  |
| -------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [OH_ArkUI_NativeModule_UIJsonWrapperCreate](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappercreate)   | 复制调用方提供的字符串，创建JSONWrapper对象（创建成功后由调用方拥有对象，输入字符串仍由调用方管理）。 |
| [OH_ArkUI_NativeModule_UIJsonWrapperGetData](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetdata) | 获取对象中的只读、以空字符结尾的JSON字符串（返回只读指针，不转移数据所有权）。                        |
| [OH_ArkUI_NativeModule_UIJsonWrapperGetSize](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetsize) | 获取JSON文本的UTF-8字节数，不含结尾空字符（不创建结果对象，不转移所有权）。                           |
| [OH_ArkUI_NativeModule_UIJsonWrapperDestroy](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy) | 销毁调用方拥有的JSONWrapper及内部数据（由所有者调用一次，调用后由该对象取得的全部指针失效）。         |

## JSONWrapper对象格式

使用JSONWrapper承载数据时，需先按对应业务场景的格式要求构造UTF-8编码的JSON字符串，再调用[OH_ArkUI_NativeModule_UIJsonWrapperCreate](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappercreate)接口将该字符串封装为JSONWrapper对象。JSONWrapper没有独立的字段设置接口，创建后如需修改内容，应重新构造新的JSON字符串并再次调用该接口创建新的对象。

输入应为有效JSON对象，顶层结构由固定字段和业务字段组成：

> **说明：**
>
> 有效JSON对象需同时满足以下条件：
>
> - 文本语法合法，可被解析为JSON；空字符串无效，JSON文本中不得包含未转义的空字节（U+0000需使用JSON转义表示）。
> - 顶层为JSON对象，即以`{`和`}`包裹的键值结构；顶层为数组、字符串、数字等其他JSON类型时不满足要求。

- **固定字段**：`schemaVersion`，协议版本，固定取值1。无论JSONWrapper承载控件命令还是采集结果，顶层均包含该字段；创建接口校验该字段，缺失或取值不受支持时返回[ARKUI_ERROR_CODE_PARAM_INVALID](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)，解析时应先校验其取值。
- **业务字段**：顶层其余字段由具体场景的协议定义，字段名称、必填性与取值随场景而异，详细结构见对应的业务开发指南：控件命令见[注入控件命令](./ndk-ui-command-injection.md#jsonwrapper对象格式)，采集结果见[采集控件树信息](./ndk-ui-info-collect-tree.md)。

构造与解析遵循相同的公共逻辑：构造时按场景协议组织业务字段，并在顶层写入`schemaVersion`；解析时先校验`schemaVersion`取值，再按场景协议解析业务字段。

## 创建与使用JSONWrapper对象

本节代码片段摘自示例工程。

### 创建JSONWrapper对象

示例在ArkTS侧准备完整JSON字符串，Native侧由NAPI接口[napi_get_value_string_utf8](../napi/use-napi-about-string.md#napi_get_value_string_utf8)（将ArkTS string类型数据转为UTF-8编码的C字符串）得到字节缓冲和字节数，调用[OH_ArkUI_NativeModule_UIJsonWrapperCreate](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappercreate)完成创建并检查返回码。代码中其余部分是NAPI桥接和一次使用示例：创建所得的command对象被传给[OH_ArkUI_NativeModule_UIEventInjectCompositeCommand](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectcompositecommand)，提交与回调的完整说明见[注入控件命令](ndk-ui-command-injection.md)。

示例函数在注入调用返回后销毁自己创建的JSONWrapper，该时机遵循注入接口对输入对象的生命周期要求，见[注入控件命令](ndk-ui-command-injection.md)。其他异步接口的输入对象按各自接口的生命周期要求管理；非空userData和完成回调的生命周期也应另行管理。

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

### 读取JSONWrapper内容

[OH_ArkUI_NativeModule_UIJsonWrapperGetData](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetdata)与[OH_ArkUI_NativeModule_UIJsonWrapperGetSize](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetsize)的返回值说明见接口声明；两个接口都不创建结果对象，也不转移所有权。以下JsonString是示例的辅助函数，使用OH_ArkUI_NativeModule_UIJsonWrapperGetData取得以空字符结尾的字符串，并通过std::strlen计算长度，将已有JSONWrapper内容复制为ArkTS字符串；辅助函数JsonString只读取参数内容，不负责销毁对象。

``` C++
napi_value JsonString(napi_env env, const OH_ArkUI_NativeModule_UIJsonWrapper* json)
{
    const char* data = OH_ArkUI_NativeModule_UIJsonWrapperGetData(json);
    if (data == nullptr) {
        napi_throw_error(env, nullptr, "Cannot read the collected JSON payload");
        return nullptr;
    }
    napi_value result = nullptr;
    if (napi_create_string_utf8(env, data, std::strlen(data), &result) != napi_ok) {
        return nullptr;
    }
    return result;
}
```

在目标对象仍有效的期间使用这两个读取接口。返回的数据指针不可写，也不能单独free或delete；需要在对象销毁后继续使用内容时，先复制到应用自己的字符串或其他存储。

通过NAPI接口[napi_create_string_utf8](../napi/use-napi-about-string.md#napi_create_string_utf8)（将UTF-8编码的C字符串转换为ArkTS string类型）复制为ArkTS字符串后，可以使用`JSON.parse`解析。解析校验分两步：先校验固定字段`schemaVersion`的取值；再按业务协议校验业务字段的类型与可选性（是否必填、是否可能缺席）。业务协议指具体场景的业务字段定义：控件命令见[注入控件命令](ndk-ui-command-injection.md)，采集结果见[采集控件树信息](ndk-ui-info-collect-tree.md)。解析失败应由应用处理，不把`OH_ArkUI_NativeModule_UIJsonWrapperGetData`返回的指针保留到对象销毁之后。

### 管理JSONWrapper内存

判断是否负责释放，应看对象来源所对应接口的所有权说明，不能只看指针类型。

| JSONWrapper对象来源或操作                                                                                                                                             | 处理方式                                                                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 应用调用创建接口成功得到的对象                                                                                                                         | 应用持有所有权，不再使用时调用[OH_ArkUI_NativeModule_UIJsonWrapperDestroy](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy)。 |
| 同步控件树采集成功返回的对象                                                                                                                           | 对应采集接口向应用转移所有权，应用读取后销毁。                                                                                                                             |
| 异步控件树采集成功回调中的对象                                                                                                                         | 回调向应用转移所有权；示例在回调内读取后销毁，也可以明确转移到业务所有者后再销毁。                                                                                         |
| 没有取得所有权的对象或指针别名                                                                                                                         | 仅在对象销毁前使用，不独立销毁；保存指针副本不会延长有效期。                                                                                                               |
| [OH_ArkUI_NativeModule_UIJsonWrapperGetData](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetdata)返回的字符串 | 随JSONWrapper存活，不能单独释放；销毁对象后，原指针失效。                                                                                                                  |
| 创建时传入的原始data                                                                                                                                   | 仍由调用方管理；销毁JSONWrapper不会代替调用方释放原始输入缓冲区。                                                                                                          |

销毁后应停止使用对象及其所有别名，避免重复销毁。向[OH_ArkUI_NativeModule_UIJsonWrapperDestroy](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy)传入空指针没有效果，已释放的指针也不能再次使用或再次销毁。

## 约束与限制

- JSONWrapper对象不会被自动共享。把同一指针传给多个模块时，明确唯一销毁责任方，其他模块仅支持在对象销毁前使用。
- JSONWrapper接口在满足对象生命周期要求的前提下可以在任意线程调用；同一有效对象的只读查询可以并发，销毁时不能有其他代码正在读取该对象或其数据。
- JSONWrapper接口不会调用应用回调，也不提供异步完成或取消操作；不得从[信号处理函数](../dfx/cppcrash-guidelines.md#基本概念)调用。
- 不同对象可独立操作。创建和销毁需要申请或释放内存，耗时会随系统状态波动，无法保证执行时长。
- JSONWrapper对象可跨线程使用，不代表控件树采集或命令注入可以从任意线程调用。应分别遵循业务指南的线程约束。
- 空采集内容仍可能对应成功的JSON对象；例如控件树返回带schemaVersion且treeInfo为null的结果，仍需按所有权释放JSONWrapper对象。

## 异常处理

本节只说明对应JSONWrapper接口声明的返回结果。

### 处理创建返回值

调用[OH_ArkUI_NativeModule_UIJsonWrapperCreate](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappercreate)后按返回值判断结果，各错误码及可能原因见接口声明的返回值说明。失败时输出对象为空指针，不得继续使用它执行采集或注入。

### 处理读取和销毁结果

读取函数不返回[ArkUI_ErrorCode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)；空输入时的返回值见[OH_ArkUI_NativeModule_UIJsonWrapperGetData](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetdata)与[OH_ArkUI_NativeModule_UIJsonWrapperGetSize](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetsize)声明的返回值说明，这类结果不能解释为已经成功采集到空业务内容。[OH_ArkUI_NativeModule_UIJsonWrapperDestroy](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy)没有返回值。
