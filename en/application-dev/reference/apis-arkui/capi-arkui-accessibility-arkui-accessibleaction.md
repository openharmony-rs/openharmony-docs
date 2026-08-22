# ArkUI_AccessibleAction

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=86516607de4ae31b89a087b4feaa5c2b41c67026 translatedAt=2026-08-19T04:15:40.309Z pushedAt=2026-08-19T06:34:13.869Z -->

```c
typedef struct {...} ArkUI_AccessibleAction
```

## Overview

Defines an accessibility action. This struct describes the accessibility actions supported by a component. You can use this struct to define an action type (**actionType**) and the corresponding action description (**description**), so that the accessibility service can announce the executable action to users. It enables the accessibility service to present to users the actions that can be performed on a node (such as tap, long-pressing, and scroll), and provides text descriptions of the actions to help users understand their meanings.

**Since**: 13

**Related module**: [ArkUI_Accessibility](capi-arkui-accessibility.md)

**Header file**: [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

## Summary

### Member Variables

| Name                                           | Description|
|-----------------------------------------------| -- |
| [ArkUI_Accessibility_ActionType](capi-native-interface-accessibility-h.md#arkui_accessibility_actiontype) actionType | Accessibility action type. |
| const char* description | Pointer to the description of the accessibility action. |