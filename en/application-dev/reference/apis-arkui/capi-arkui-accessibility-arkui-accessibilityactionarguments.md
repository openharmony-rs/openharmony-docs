# ArkUI_AccessibilityActionArguments
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=33898b66eb6c0bf66810bb0d90faa36b55a4ad07 translatedAt=2026-11-09T11:36:32.133Z pushedAt=2026-11-10T01:15:40.532Z nl=1 -->

```c
typedef struct ArkUI_AccessibilityActionArguments ArkUI_AccessibilityActionArguments
```

## Overview

Defines accessibility action arguments. When an accessibility service (such as a screen reader or voice assistant) requests to perform an accessibility action (such as selecting text or setting the cursor position) on a specified node, the system uses this struct to pass the additional context information required by the action to a third-party platform. The third-party platform can call [OH_ArkUI_FindAccessibilityActionArgumentByKey](capi-native-interface-accessibility-h.md#oh_arkui_findaccessibilityactionargumentbykey) in the [executeAccessibilityAction](capi-arkui-accessibility-arkui-accessibilityprovidercallbacks.md#executeaccessibilityaction) callback to obtain the value of a specified argument. This struct applies to scenarios where the third-party platform needs to parse and respond to accessibility action arguments, such as text selection triggered by a screen reader and accessibility interaction triggered by a voice assistant.

**Since**: 13

**Related module**: [ArkUI_Accessibility](capi-arkui-accessibility.md)

**Header file**: [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

