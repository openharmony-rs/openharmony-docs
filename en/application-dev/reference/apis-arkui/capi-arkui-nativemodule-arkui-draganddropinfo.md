# ArkUI_DragAndDropInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=3b17ae247298f1cf952b1cbdcb60f1ff0e80beac translatedAt=2026-11-09T11:41:17.387Z pushedAt=2026-11-10T02:03:05.915Z nl=1 -->

```c
typedef struct ArkUI_DragAndDropInfo ArkUI_DragAndDropInfo
```

## Overview

Defines drag and drop information returned through a drag status listener after dragging is proactively initiated. You can obtain the drag start or end status and the drag event data when the drag ends from this struct, and perform subsequent processing based on the status. For details about how to register the drag callback, see [drag_and_drop.h](capi-drag-and-drop-h.md).

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [drag_and_drop.h](capi-drag-and-drop-h.md)

