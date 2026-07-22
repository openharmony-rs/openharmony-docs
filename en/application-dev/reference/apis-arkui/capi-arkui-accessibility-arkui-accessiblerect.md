# ArkUI_AccessibleRect

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e98b791a1f57fab5012a75ce7d9ff0a0466dd410 translatedAt=2026-07-16T10:42:37.823Z pushedAt=2026-07-17T02:36:04.423Z -->

```c
typedef struct {...} ArkUI_AccessibleRect
```

## Overview

Provides the coordinate position of the rectangular area of a node on a screen. This struct is used to describe the bounding rectangle of an accessibility node, define the visible area of the node on the screen through the coordinates of the upper-left and lower-right corners, and support the accessibility service in obtaining the position and size information of the node.

**Since**: 13

**Related module**: [ArkUI_Accessibility](capi-arkui-accessibility.md)

**Header file**: [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t leftTopX | X-coordinate of the upper left corner.|
| int32_t leftTopY | Y-coordinate of the upper left corner. |
| int32_t rightBottomX | X-coordinate of the lower right corner.|
| int32_t rightBottomY | Y-coordinate of the lower right corner. |