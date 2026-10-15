# OH_ArkUI_NativeModule_UIJsonWrapper

```c
typedef struct OH_ArkUI_NativeModule_UIJsonWrapper OH_ArkUI_NativeModule_UIJsonWrapper
```

## Overview

Defines an opaque, immutable JSON data object.<br> The object holds a JSON string. It is used both to carry data delivered by the framework (UI sensing) and to carry commands injected by the application (UI control). The JSON object must contain a top-level schemaVersion field for version control and future compatibility. This requirement applies both to JSON supplied by the application and to JSON returned or delivered through callbacks by the framework, including results with no collected content.<br> The object is not reference-counted. Copying its pointer creates a borrowed alias, not an independent object or an additional ownership claim. The owner must destroy the object exactly once. Destruction invalidates all aliases and data pointers; do not use or destroy them again.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [ui_json_wrapper.h](capi-ui-json-wrapper-h.md)

