# ArkUI_NodeComponentEvent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @wangyang2022-->
<!--Designer: @piggyguy; @wangyang2022-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=9e1b445f5d1c75d7b2fd296696329924c2407a0b translatedAt=2026-09-20T09:20:44.628Z pushedAt=2026-09-21T12:32:33.868Z -->

```c
typedef struct {...} ArkUI_NodeComponentEvent
```

## Overview

Defines the parameter type of a component callback event, which is used to pass event-related data when the component callback is triggered, so that the application can obtain the callback event parameters.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## Summary

### Member Variables

| Name                                                     | Description|
|---------------------------------------------------------| -- |
| [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) data[[MAX_COMPONENT_EVENT_ARG_NUM](capi-native-node-h.md#macros)] | Stores the parameter data of the component callback event. The array elements are arranged in the order of the parameters defined by the callback event. For details about the parameter definitions of each event type, see [native_node.h](capi-native-node-h.md). |


