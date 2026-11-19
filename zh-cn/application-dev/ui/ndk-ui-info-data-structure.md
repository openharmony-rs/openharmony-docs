# UI信息数据格式说明

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @lushi871202-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

从API版本26.1.0开始，应用可以使用[OH_ArkUI_NativeModule_UIJsonWrapper](../reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md)承载UI采集结果和控件命令。本文将该对象称为JSONWrapper，介绍业务JSON的构造，以及对象的创建、读取和销毁方式。

JSONWrapper保存UTF-8编码的JSON文本，应用通过公开函数访问数据。业务字段由具体采集或命令协议定义，不能把JSONWrapper看作具有固定节点字段的结构体。

## 接口说明

使用`<arkui/ui_json_wrapper.h>`头文件，链接libace_ndk.z.so。完整声明、参数与起始版本见[ui_json_wrapper.h](../reference/apis-arkui/capi-ui-json-wrapper-h.md)。

| 接口                                                                                                                                       | 用途                                          | 所有权                                                 |
| -------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------- | -------------------------------------------------------- |
| [OH_ArkUI_NativeModule_UIJsonWrapperCreate](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappercreate)   | 复制调用方提供的字符串，创建JSONWrapper对象。 | 创建成功后，调用方拥有对象。输入字符串仍由调用方管理。 |
| [OH_ArkUI_NativeModule_UIJsonWrapperGetData](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetdata) | 获取对象中的只读、以空字符结尾的JSON字符串。  | 返回只读指针，不转移数据所有权。                       |
| [OH_ArkUI_NativeModule_UIJsonWrapperGetSize](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetsize) | 获取JSON文本的UTF-8字节数，不含结尾空字符。   | 不创建结果对象，不转移所有权。                         |
| [OH_ArkUI_NativeModule_UIJsonWrapperDestroy](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy) | 销毁调用方拥有的JSONWrapper及内部数据。       | 由所有者调用一次，随后由该对象取得的全部指针失效。     |

这四个接口处理数据对象本身，不执行树采集或命令注入。调用业务接口时，仍需满足相应Context、节点和线程要求。

## JSONWrapper对象基础格式

先根据业务协议构造JSON文本，再调用创建接口封装。JSONWrapper没有独立的字段设置接口，创建后需要修改内容时，应构造新的JSON文本并创建另一个对象。

输入应为有效JSON对象，顶层包含schemaVersion，当前协议使用值1。具体格式内容参照各个业务场景的格式要求，以下是[控件命令](./ndk-ui-command-injection.md#公共结构)的格式示例。

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

## 创建与使用JSONWrapper对象

以下片段与[示例工程](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection)中的Native桥接同源。它们依赖工程中的辅助函数和页面状态，辅助函数不是SDK新增接口。

### 创建JSONWrapper对象

创建时按[OH_ArkUI_NativeModule_UIJsonWrapperCreate](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappercreate)的参数说明准备data、size和outOwned；size以UTF-8字节数计，中文等非ASCII文本不能用字符个数代替，覆盖outOwned中先前拥有的对象指针前，先销毁旧对象，避免丢失所有权。示例在ArkTS侧准备完整JSON字符串，Native侧由N-API读取函数得到字节缓冲和字节数，调用该接口完成创建并检查返回码。代码中其余部分是N-API桥接和一次使用示例：创建所得的command对象被传给[OH_ArkUI_NativeModule_UIEventInjectCompositeCommand](../reference/apis-arkui/capi-ui-event-injection-h.md#oh_arkui_nativemodule_uieventinjectcompositecommand)，提交与回调的完整说明见[注入控件命令](ndk-ui-command-injection.md)。

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

示例函数在注入调用返回后销毁自己创建的JSONWrapper，该时机遵循注入接口对输入对象的生命周期要求，见[注入控件命令](ndk-ui-command-injection.md)。其他异步接口的输入对象按各自接口的生命周期要求管理；非空userData和完成回调的生命周期也应另行管理。

### 读取JSONWrapper内容

[OH_ArkUI_NativeModule_UIJsonWrapperGetData](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetdata)与[OH_ArkUI_NativeModule_UIJsonWrapperGetSize](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetsize)的返回值说明见接口声明；两个接口都不创建结果对象，也不转移所有权。以下JsonString是示例的辅助函数，使用GetData取得以空字符结尾的字符串并以strlen计算长度，将已有JSONWrapper内容复制为ArkTS字符串；它只读取参数内容，不负责销毁对象。

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

通过N-API复制为ArkTS字符串后，可以使用JSON.parse解析，并按业务协议检查schemaVersion、字段类型和可选字段。解析失败应由应用处理，不把GetData返回的指针保留到对象销毁之后。

### 管理JSONWrapper内存

判断是否负责释放，应看对象来源所对应接口的所有权说明，不能只看指针类型。

| 来源或操作                                                                                                                                             | 处理方式                                                                                                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 应用调用创建接口成功得到的对象                                                                                                                         | 应用持有所有权，不再使用时调用[OH_ArkUI_NativeModule_UIJsonWrapperDestroy](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy)。 |
| 同步控件树采集成功返回的对象                                                                                                                           | 对应采集接口向应用转移所有权，应用读取后销毁。                                                                                                                             |
| 异步控件树采集成功回调中的对象                                                                                                                         | 回调向应用转移所有权；示例在回调内读取后销毁，也可以明确转移到业务所有者后再销毁。                                                                                         |
| 没有取得所有权的对象或指针别名                                                                                                                         | 仅在对象销毁前使用，不独立销毁；保存指针副本不会延长有效期。                                                                                                               |
| [OH_ArkUI_NativeModule_UIJsonWrapperGetData](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetdata)返回的字符串 | 随JSONWrapper存活，不能单独释放；销毁对象后，原指针失效。                                                                                                                  |
| 创建时传入的原始data                                                                                                                                   | 仍由调用方管理；销毁JSONWrapper不会代替调用方释放原始输入缓冲区。                                                                                                          |

销毁后应停止使用对象及其所有别名，避免重复销毁。向[OH_ArkUI_NativeModule_UIJsonWrapperDestroy](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy)传入空指针没有效果，已释放的指针也不能再次使用或再次销毁。

## 约束与限制

对象生命周期、并发访问和业务接口的线程要求需要分别处理。

- JSONWrapper对象不会被自动共享。把同一指针传给多个模块时，明确唯一销毁责任方，其他模块只在对象销毁前使用。
- 公开包装接口在满足对象生命周期要求的前提下可以在任意线程调用；同一有效对象的只读查询可以并发，销毁时不能有其他代码正在读取该对象或其数据。
- 包装接口不会调用应用回调，也不提供异步完成或取消操作；不得从信号处理函数调用。
- 不同对象可独立操作。创建和销毁需要申请或释放内存，耗时会随系统状态波动，不能假定总能很快完成。
- 包装对象可跨线程使用，不代表控件树采集或命令注入可以从任意线程调用。应分别遵循业务指南的线程约束。
- 空采集内容仍可能对应成功的JSON对象；例如控件树返回带schemaVersion且treeInfo为null的结果，仍需按所有权释放包装对象。

## 异常处理

本节只说明对应公开包装接口声明的返回结果。

### 处理创建返回值

调用[OH_ArkUI_NativeModule_UIJsonWrapperCreate](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappercreate)后按返回值判断结果，各错误码及可能原因见接口声明的返回值说明。失败时输出对象为空指针，不继续使用它执行采集或注入；重试策略见接口描述。

### 处理读取和销毁结果

读取函数不返回[ArkUI_ErrorCode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)；空输入时的返回值见[OH_ArkUI_NativeModule_UIJsonWrapperGetData](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetdata)与[OH_ArkUI_NativeModule_UIJsonWrapperGetSize](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetsize)声明的返回值说明，这类结果不能解释为已经成功采集到空业务内容。[OH_ArkUI_NativeModule_UIJsonWrapperDestroy](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy)没有返回值。
