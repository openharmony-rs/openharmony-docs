# ArkWeb_JavaScriptValue*
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=5191f5de3eca0919d8d5e44823dbef1bf6b74270 translatedAt=2026-11-04T11:52:58.064Z pushedAt=2026-11-04T11:55:10.639Z nl=1 -->

```c
typedef struct ArkWeb_JavaScriptValue* ArkWeb_JavaScriptValuePtr
```

## Overview

ArkWeb_JavaScriptValue is a struct used to encapsulate JavaScript values in native code. It provides basic creation and manipulation capabilities for JavaScript values. This struct supports converting native data into a JavaScript-recognizable format, addressing type safety and format compatibility issues in bidirectional data transfer between native and JavaScript. As the fundamental data transfer type in JavaScript bridge communication, it helps reduce manual conversion costs, improve bridge communication efficiency, and enhance maintainability.

**Since**: 18

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_type.h](capi-arkweb-type-h.md)

