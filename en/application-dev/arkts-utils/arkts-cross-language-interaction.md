# ArkTS Cross-Language Interaction
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @shilei123; @liudachuan3-->
<!--Designer: @shilei123-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=3383cf6b2a36933eae9d88e06bbfad5f09f5363a translatedAt=2026-11-04T09:02:15.287Z pushedAt=2026-11-04T09:27:18.279Z nl=1 -->

In addition to using ArkTS for development, you can also use Node-API to implement cross-language interaction between ArkTS and C/C++ (native).

OpenHarmony Node-API is an extended version of Node API in the Node.js community but does not fully align with it.

You can refer to [Cross-Language Development Process Using Node-API](../napi/use-napi-process.md) to develop and encapsulate native capabilities based on [Data Types Supported by Node-API](../napi/napi-data-types-interfaces.md#data-types) and [Node-API Interfaces](../reference/native-lib/napi.md), and implement cross-language calls by importing native modules on the ArkTS side.

[Node-API extension APIs](../napi/use-napi-about-extension.md) provide enhanced features for more flexible ArkTS interactions and custom object creation. You can also refer to [Node-API Development Specifications](../napi/napi-guidelines.md) and [Node-API FAQs](../napi/use-napi-faqs.md) when developing cross-language features using extended Node-API capabilities.
