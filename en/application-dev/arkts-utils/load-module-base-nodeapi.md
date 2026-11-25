# Loading Modules Using Node-API
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @yao_dashuai-->
<!--Designer: @yao_dashuai-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-11-04T09:22:32.059Z pushedAt=2026-11-04T09:36:34.763Z nl=1 -->

Node-API provides multiple methods for you to load in-project modules and files on the C++ side. The **napi_load_module_with_info** API is recommended.

## napi_load_module_with_info

Loads the HAP, HSP, HAR, or native module in the main thread or child thread. When using this API, you must specify the information of the package to be loaded. It supports various scenarios.

For details, see [napi_load_module_with_info](../napi/use-napi-load-module-with-info.md).

## napi_load_module

Loads the HAP, HSP, HAR, or native module in the main thread, facilitating parameter transfer. The loading scenario is restricted. For example, this API cannot be used in a child thread.

For details, see [napi_load_module](../napi/use-napi-load-module.md).