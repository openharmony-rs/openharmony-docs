# ArkUI_AccessibilityActionArguments
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=c18a4e1567d098b4c6780d709d006d4ba2f2faab translatedAt=2026-09-18T09:25:14.070Z pushedAt=2026-09-18T10:25:05.015Z -->

```c
typedef struct ArkUI_AccessibilityActionArguments ArkUI_AccessibilityActionArguments
```

## Overview

Sets the arguments of accessibility actions. When an accessibility action is performed, this struct is used to transfer additional context information required by the action to the accessibility service. It is suitable for scenarios where you need to precisely describe the details of an accessibility action to the accessibility service, such as screen reader announcements in custom components, operation parameter transfer in assistant services, and interactions triggered by voice assistants.

**Since**: 13

**Related module**: [ArkUI_Accessibility](capi-arkui-accessibility.md)

**Header file**: [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

