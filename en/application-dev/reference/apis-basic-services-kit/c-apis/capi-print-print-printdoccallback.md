# Print_PrintDocCallback

```c
typedef struct Print_PrintDocCallback {...} Print_PrintDocCallback
```

## Overview

Represents a callback for the printed document. This API can be used by native apps written in C or C++ to provide file generation and task status receiving capabilities for the print framework.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 13

**Related module**: [Print](capi-others-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Print_OnStartLayoutWrite](capi-ohprint-h.md#print_onstartlayoutwrite) startLayoutWriteCb | Callback invoked when the file write-back starts. When the file write-back starts, the system calls this callback to instruct the app to write the content to be printed. |
| [Print_OnJobStateChanged](capi-ohprint-h.md#print_onjobstatechanged) jobStateChangedCb | Callback invoked when the print job state changes. When the print job state changes, the system invokes this callback to notify the app of the change. |


