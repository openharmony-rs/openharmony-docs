# ArkUI_AccessibilityActionArguments

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e98b791a1f57fab5012a75ce7d9ff0a0466dd410 translatedAt=2026-07-16T08:44:52.584Z pushedAt=2026-07-16T08:52:38.902Z -->

```c
typedef struct ArkUI_AccessibilityActionArguments ArkUI_AccessibilityActionArguments
```

## Overview

Sets the arguments of accessibility actions. When an accessibility action is performed, this struct is used to transfer additional context information required by the action to the accessibility service. It is suitable for scenarios where you need to precisely describe the details of an accessibility action to the accessibility service, such as screen reader announcements in custom components, operation parameter transfer in assistant services, and interactions triggered by voice assistants.

**Since**: 13

**Related module**: [ArkUI_Accessibility](capi-arkui-accessibility.md)

**Header file**: [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)