---
kits: ["ArkTS / Ark Programming Language"]
description: "Describes the cross-language interaction capability between ArkTS and C/C++, implemented based on the Node-API specification extension. It supports developers in developing and encapsulating Native modules, and importing so libraries on the ArkTS side to implement cross-language calls."
keywords: [ArkTS, cross-language interaction, Node-API, C/C++, Native module, module import, so library, cross-language call]
doctype: guide
status: active
---

# ArkTS Cross-Language Interaction
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @shilei123; @liudachuan3-->
<!--Designer: @shilei123-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=da641289f51d20c4f9fd6f0614d722cdc941f200 translatedAt=2026-11-06T10:15:39.000Z pushedAt=2026-11-09T08:58:35.444Z nl=1 -->

In addition to using ArkTS for development, you can also use Node-API to implement cross-language interaction between ArkTS and C/C++ (native).

OpenHarmony Node-API is an extended version of Node API in the Node.js community but does not fully align with it.

You can refer to [Cross-Language Development Process Using Node-API](../napi/use-napi-process.md) to develop and encapsulate native capabilities based on [Data Types Supported by Node-API](../napi/napi-data-types-interfaces.md#data-types) and [Node-API Interfaces](../reference/native-lib/napi.md), and implement cross-language calls by importing native modules on the ArkTS side.

[Node-API extension APIs](../napi/use-napi-about-extension.md) provide enhanced features for more flexible ArkTS interactions and custom object creation. You can also refer to [Node-API Development Specifications](../napi/napi-guidelines.md) and [Node-API FAQs](../napi/use-napi-faqs.md) when developing cross-language features using extended Node-API capabilities.
