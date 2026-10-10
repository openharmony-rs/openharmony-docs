# Print_PrintDocCallback
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=f172f47675a58f89bb693013f28ad2465486c311 translatedAt=2026-10-09T11:42:34.750Z pushedAt=2026-10-10T03:42:30.105Z -->

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
