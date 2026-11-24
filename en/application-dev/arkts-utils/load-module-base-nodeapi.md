---
kits: ["ArkTS / Ark Programming Language"]
description: "Describes the APIs for loading modules in a project on the C++ side based on Node-API. It is recommended to use the napi_load_module_with_info API, which supports loading hap/hsp/har/native modules on the main thread or a subthread."
keywords: [Node-API, module loading, napi_load_module_with_info, napi_load_module, C++ module loading, hap, hsp, har, native module]
doctype: guide
status: active
---

# Loading Modules Using Node-API
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @shilei123-->
<!--Designer: @shilei123-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=da641289f51d20c4f9fd6f0614d722cdc941f200 translatedAt=2026-11-06T10:36:15.446Z pushedAt=2026-11-12T07:44:23.494Z nl=1 -->

Node-API provides multiple methods for you to load in-project modules and files on the C++ side. The **napi_load_module_with_info** API is recommended.

## napi_load_module_with_info

Loads the HAP, HSP, HAR, or native module in the main thread or child thread. When using this API, you must specify the information of the package to be loaded. It supports various scenarios.

For details, see [napi_load_module_with_info](../napi/use-napi-load-module-with-info.md).

## napi_load_module

Loads the HAP, HSP, HAR, or native module in the main thread, facilitating parameter transfer. The loading scenario is restricted. For example, this API cannot be used in a child thread.

For details, see [napi_load_module](../napi/use-napi-load-module.md).