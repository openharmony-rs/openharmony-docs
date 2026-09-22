# ArkUI_NodeComponentEvent

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @wangyang2022-->
<!--Designer: @piggyguy; @wangyang2022-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=10a20f217ecf0e77e23c0c78c466ce20e1033d43 translatedAt=2026-08-19T08:26:43.698Z pushedAt=2026-08-20T03:58:39.207Z -->

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