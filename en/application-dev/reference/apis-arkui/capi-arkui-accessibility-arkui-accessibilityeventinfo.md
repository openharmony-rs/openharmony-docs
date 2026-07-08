# ArkUI_AccessibilityEventInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_AccessibilityEventInfo ArkUI_AccessibilityEventInfo
```

## Overview

Describes the accessibility event information. After a component completes an action requested by an accessibility service or application, it needs to send a success event to confirm the operation. Similarly, if the component needs to synchronize its state change with the accessibility service or application due to its own interactive behavior, it should actively trigger an event to communicate the change.

**Since**: 13

**Related module**: [ArkUI_Accessibility](capi-arkui-accessibility.md)

**Header file**: [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)
