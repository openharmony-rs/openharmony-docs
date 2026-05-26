# ArkTS子系统Changelog

## cl.arkts.1 JSVM Wasm解释器特性使能

**访问级别**

公开接口

**变更原因**

生态需求，支持jitless条件下执行Wasm能力，支撑坚盾守护模式下特效/直播等业务场景。

**变更影响**

从OpenHarmony SDK 7.0.0.22开始，JSVM Wasm相关接口补充了jitless下默认行为，不再返回错误码[JSVM_JIT_MODE_EXPECTED](../../../application-dev/reference/common/capi-jsvm-types-h.md#jsvm_status)，Wasm解释器正常运行。

变更前：

[OH_JSVM_CompileWasmModule](../../../application-dev/reference/common/capi-jsvm-h.md#oh_jsvm_compilewasmmodule)，返回错误码 [JSVM_JIT_MODE_EXPECTED](../../../application-dev/reference/common/capi-jsvm-types-h.md#jsvm_status)，并设置JSVM异常。<br>
[OH_JSVM_CompileWasmFunction](../../../application-dev/reference/common/capi-jsvm-h.md#oh_jsvm_compilewasmfunction)，返回错误码 [JSVM_JIT_MODE_EXPECTED](../../../application-dev/reference/common/capi-jsvm-types-h.md#jsvm_status)，并设置JSVM异常。<br>
[OH_JSVM_CreateWasmCache](../../../application-dev/reference/common/capi-jsvm-h.md#oh_jsvm_createwasmcache)，返回错误码 [JSVM_JIT_MODE_EXPECTED](../../../application-dev/reference/common/capi-jsvm-types-h.md#jsvm_status)，并设置JSVM异常。<br>

变更后：

[OH_JSVM_CompileWasmModule](../../../application-dev/reference/common/capi-jsvm-h.md#oh_jsvm_compilewasmmodule)，WasmCache不生效，其他行为与JIT模式一致。<br>
[OH_JSVM_CompileWasmFunction](../../../application-dev/reference/common/capi-jsvm-h.md#oh_jsvm_compilewasmfunction)，直接返回JSVM_OK（解释执行不依赖当前接口）。<br>
[OH_JSVM_CreateWasmCache](../../../application-dev/reference/common/capi-jsvm-h.md#oh_jsvm_createwasmcache)，直接返回JSVM_OK，并将WasmCache置为空。<br>

**起始 API Level**

12

**变更发生版本**

从OpenHarmony SDK 7.0.0.22开始。

**变更的接口/组件**

ArkTS/JSVM

**适配指导**

开发者需要检视调用OH_JSVM_CompileWasmModule，OH_JSVM_CompileWasmFunction，OH_JSVM_CreateWasmCache三个接口的代码上下文，判断接口返回值从“返回错误码”变更为“返回JSVM_OK”对代码逻辑造成的影响，按照代码预期修改代码。
