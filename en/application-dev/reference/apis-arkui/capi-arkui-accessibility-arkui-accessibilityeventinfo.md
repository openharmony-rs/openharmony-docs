# ArkUI_AccessibilityEventInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=33898b66eb6c0bf66810bb0d90faa36b55a4ad07 translatedAt=2026-11-09T11:36:32.035Z pushedAt=2026-11-10T01:16:50.229Z nl=1 -->

```c
typedef struct ArkUI_AccessibilityEventInfo ArkUI_AccessibilityEventInfo
```

## Overview

Defines accessibility event information. It carries the content of an accessibility event reported by an application to an accessibility service, and can be reported through the [OH_ArkUI_SendAccessibilityAsyncEvent](capi-native-interface-accessibility-h.md#oh_arkui_sendaccessibilityasyncevent) API. It applies to scenarios where an accessibility service or assistive application requires a component to perform an action and then sends an execution result event to notify the operation result. It also applies to scenarios where events need to be reported to the accessibility service, such as component state changes (for example, tap, selection, text update, page switch, and focus change), proactive announcements, and focus requests.

**Since**: 13

**Related module**: [ArkUI_Accessibility](capi-arkui-accessibility.md)

**Header file**: [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

