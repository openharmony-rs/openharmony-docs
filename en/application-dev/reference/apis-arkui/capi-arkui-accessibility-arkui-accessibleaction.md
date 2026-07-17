# ArkUI_AccessibleAction

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e98b791a1f57fab5012a75ce7d9ff0a0466dd410 translatedAt=2026-07-16T10:41:55.534Z pushedAt=2026-07-17T02:19:16.513Z -->

```c
typedef struct {...} ArkUI_AccessibleAction
```

## Overview

Defines an accessibility action. This struct describes the action types supported by an accessibility node and their descriptions. It enables the accessibility service to present to users the actions that a node can perform (such as tap, long-pressing, and scrolling), and provides text descriptions of the actions to help users understand their meanings.

**Since**: 13

**Related module**: [ArkUI_Accessibility](capi-arkui-accessibility.md)

**Header file**: [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

## Summary

### Member Variables

| Name                                           | Description|
|-----------------------------------------------| -- |
| [ArkUI_Accessibility_ActionType](capi-native-interface-accessibility-h.md#arkui_accessibility_actiontype) actionType | Action type.|
| const char* description                       | Pointer to the action description.|