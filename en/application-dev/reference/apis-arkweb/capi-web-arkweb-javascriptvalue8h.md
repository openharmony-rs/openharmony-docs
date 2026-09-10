# ArkWeb_JavaScriptValue*

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=3cf0e4d31df69a8bda793fe15a55a60676b46acc translatedAt=2026-08-03T09:52:21.745Z pushedAt=2026-08-06T09:29:33.773Z -->

```c
typedef struct ArkWeb_JavaScriptValue* ArkWeb_JavaScriptValuePtr
```

## Overview

ArkWeb_JavaScriptValue is a struct used to encapsulate JavaScript values in native code. It provides basic creation and manipulation capabilities for JavaScript values. This struct supports converting native data into a JavaScript-recognizable format, addressing type safety and format compatibility issues in bidirectional data transfer between native and JavaScript. As the fundamental data transfer type in JavaScript bridge communication, it helps reduce manual conversion costs, improve bridge communication efficiency, and enhance maintainability.

**Since**: 18

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_type.h](capi-arkweb-type-h.md)