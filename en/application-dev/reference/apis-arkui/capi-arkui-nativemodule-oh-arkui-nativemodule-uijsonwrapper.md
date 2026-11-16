# OH_ArkUI_NativeModule_UIJsonWrapper
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @lushi871202 -->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=37a41c7e4764d3e7f831e1f47fc28c3acf56e6c1 translatedAt=2026-11-03T08:42:34.224Z pushedAt=2026-11-03T09:14:14.308Z nl=1 -->

```c
typedef struct OH_ArkUI_NativeModule_UIJsonWrapper OH_ArkUI_NativeModule_UIJsonWrapper
```

## Overview

Defines an immutable JSON data object whose internal structure is not exposed.<br>The object holds a JSON string, which is used both to carry data passed by the framework (UI awareness) and to carry commands injected by the application (UI control). The top level of the JSON object must contain the **schemaVersion** field for version control and subsequent compatibility maintenance. JSON passed in by the application, as well as JSON returned by the framework through APIs or passed in through callbacks, must meet this requirement. Even if no content is collected, the returned JSON must carry this field.<br>The object does not use reference counting. Copying an object pointer only produces a borrowed alias, without creating an independent object or increasing ownership. The owner of the object must destroy the object exactly once. After destruction, all aliases and data pointers become invalid and must not be used or destroyed again.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since:** 26.1.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file:** [ui_json_wrapper.h](capi-ui-json-wrapper-h.md)
