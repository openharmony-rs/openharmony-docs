# ArkUI_AccessibleAction
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=33898b66eb6c0bf66810bb0d90faa36b55a4ad07 translatedAt=2026-11-09T11:37:27.531Z pushedAt=2026-11-10T01:52:43.453Z nl=1 -->

```c
typedef struct {...} ArkUI_AccessibleAction
```

## Overview

Defines an accessibility action. This struct describes the accessibility actions supported by a component. You can use this struct to define an action type (**actionType**) and the corresponding action description (**description**), so that the accessibility service can present and announce to users the actions that can be performed on a node (such as tap, long-pressing, and scroll), and provide text descriptions of the actions to help users understand their meanings.

**Since**: 13

**Related module**: [ArkUI_Accessibility](capi-arkui-accessibility.md)

**Header file**: [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

## Summary

### Member Variables

| Name                                           | Description|
|-----------------------------------------------| -- |
| [ArkUI_Accessibility_ActionType](capi-native-interface-accessibility-h.md#arkui_accessibility_actiontype) actionType | Accessibility action type. |
| const char* description | Pointer to the description of the accessibility action. |


