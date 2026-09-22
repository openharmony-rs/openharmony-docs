# ArkUI_AccessibleAction
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=5a5f201351bc507eed1f4198e52fee2b1f6735cb translatedAt=2026-09-18T11:13:47.600Z pushedAt=2026-09-20T07:09:44.704Z -->

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


