---
kits: ["ArkTS / 方舟编程语言"]
description: "介绍基于Node-API在C++侧加载工程内模块的接口，推荐使用napi_load_module_with_info接口，支持在主线程或子线程加载hap/hsp/har/native模块。"
keywords: [Node-API, 模块加载, napi_load_module_with_info, napi_load_module, C++加载模块, hap, hsp, har, native模块]
doctype: guide
status: active
---

# 基于Node-API加载模块
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @shilei123-->
<!--Designer: @shilei123-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

Node-API中有多种方式支持开发者在C++侧加载工程内模块及文件。推荐使用napi_load_module_with_info接口。

## napi_load_module_with_info

在主线程或子线程内加载hap/hsp/har/native模块，使用时必须标记所加载的包的信息，支持多种场景。

具体参考：[napi_load_module_with_info](../napi/use-napi-load-module-with-info.md)。

## napi_load_module

在主线程内加载hap/hsp/har/native模块，参数传递简便。加载场景有限制，例如无法在子线程中使用该接口。

具体参考：[napi_load_module](../napi/use-napi-load-module.md)。