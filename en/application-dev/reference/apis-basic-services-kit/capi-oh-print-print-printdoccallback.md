# Print_PrintDocCallback
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @Zouhaifeng1-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=cfbd32eaf8f6889081f1f689234b5a5bcadff8c8 translatedAt=2026-11-23T01:10:19.457Z pushedAt=2026-11-23T10:56:13.157Z nl=1 -->

```cpp
typedef struct {...} Print_PrintDocCallback
```

## Overview

Represents a callback for the printed document. This API can be used by native apps written in C or C++ to provide file generation and task status receiving capabilities for the print framework.

**Since**: 13

**Related module**: [OH_Print](capi-oh-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member Variables

| Name                                                        | Description              |
| ------------------------------------------------------------ | ------------------ |
| [Print_OnStartLayoutWrite](capi-ohprint-h.md#print_onstartlayoutwrite) startLayoutWriteCb | Callback invoked when the file write-back starts. When the file write-back starts, the system calls this callback to instruct the app to write the content to be printed. |
| [Print_OnJobStateChanged](capi-ohprint-h.md#print_onjobstatechanged) jobStateChangedCb | Callback invoked when the print job state changes. When the print job state changes, the system invokes this callback to notify the app of the change. |
