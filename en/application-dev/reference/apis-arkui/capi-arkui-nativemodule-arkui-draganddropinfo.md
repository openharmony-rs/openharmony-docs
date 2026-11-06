# ArkUI_DragAndDropInfo

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=307c96700aa31ceaed2d16437f8e9e4fabcbd960 translatedAt=2026-08-19T04:17:32.057Z pushedAt=2026-08-19T07:21:09.250Z -->

```c
typedef struct ArkUI_DragAndDropInfo ArkUI_DragAndDropInfo
```

## Overview

Defines drag and drop information returned through a drag status listener after dragging is proactively initiated. You can obtain the drag start or end status and the drag event data when the drag ends from this struct, and perform subsequent processing based on the status. For details about how to register the drag callback, see [drag_and_drop.h](capi-drag-and-drop-h.md).

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [drag_and_drop.h](capi-drag-and-drop-h.md)