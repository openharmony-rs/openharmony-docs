# Print_PrintDocCallback
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @Zouhaifeng1-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=8ee0eefda2c8f7c51afc8d61427d4e7289d6c89f translatedAt=2026-11-12T03:56:36.150Z pushedAt=2026-11-12T12:10:51.810Z nl=1 -->

```cpp
typedef struct {...} Print_PrintDocCallback
```

## Overview

Represents a callback for the printed document. This API can be used by native apps written in C or C++ to provide file generation and task status receiving capabilities for the print framework.

**Since**: 13

**Related module**: [Print](capi-oh-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member Variables

| Name                                                        | Description              |
| ------------------------------------------------------------ | ------------------ |
| [Print_OnStartLayoutWrite](capi-ohprint-h.md#print_onstartlayoutwrite) startLayoutWriteCb | Callback invoked when the file write-back starts. When the file write-back starts, the system calls this callback to instruct the app to write the content to be printed. |
| [Print_OnJobStateChanged](capi-ohprint-h.md#print_onjobstatechanged) jobStateChangedCb | Callback invoked when the print job state changes. When the print job state changes, the system invokes this callback to notify the app of the change. |
