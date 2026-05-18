# ArkTS子系统Changelog

## cl.arkts.1 JSVM Wasm解释器特性使能

**访问级别**

公开接口

**变更原因**

生态需求，支持jitless条件下执行wasm能力，支撑坚盾守护模式下特效/直播等业务场景。

**变更影响**

JSVM wasm相关接口补充jitless下默认行为，从直接返回错误码变更为wasm解释器运行。

**起始 API Level**

12

**变更发生版本**

从OpenHarmony SDK 7.0.0.22开始。

**变更的接口/组件**

ArkTS/JSVM

**适配指导**

行为变更：

| 接口名称 | --jitless 原行为 | --jitless 目标行为 |
|---------|-----------------|-------------------|
| [OH_JSVM_CompileWasmModule](../../../application-dev/reference/common/capi-jsvm-h.md#oh_jsvm_compilewasmmodule) | 返回错误码 [JSVM_JIT_MODE_EXPECTED](../../../application-dev/reference/common/capi-jsvm-types-h.md#jsvm_status)，并设置JSVM异常 | WasmCache不生效，其他行为与JIT模式一致 |
| [OH_JSVM_CompileWasmFunction](../../../application-dev/reference/common/capi-jsvm-h.md#oh_jsvm_compilewasmfunction) | 返回错误码 [JSVM_JIT_MODE_EXPECTED](../../../application-dev/reference/common/capi-jsvm-types-h.md#jsvm_status)，并设置JSVM异常 | 直接返回JSVM_OK（解释执行不依赖当前接口） |
| [OH_JSVM_CreateWasmCache](../../../application-dev/reference/common/capi-jsvm-h.md#oh_jsvm_createwasmcache) | 返回错误码 [JSVM_JIT_MODE_EXPECTED](../../../application-dev/reference/common/capi-jsvm-types-h.md#jsvm_status)，并设置JSVM异常 | 直接返回JSVM_OK，并将WasmCache置为空 |
