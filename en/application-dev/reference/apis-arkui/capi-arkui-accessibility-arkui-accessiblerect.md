# ArkUI_AccessibleRect

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=86516607de4ae31b89a087b4feaa5c2b41c67026 translatedAt=2026-08-19T04:16:10.821Z pushedAt=2026-08-19T06:36:28.282Z -->

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
| int32_t leftTopX | X-coordinate of the upper left corner. Unit: px. |
| int32_t leftTopY | Y-coordinate of the upper left corner. Unit: px. |
| int32_t rightBottomX | X-coordinate of the lower right corner. Unit: px. |
| int32_t rightBottomY | Y-coordinate of the lower right corner. Unit: px. |