# Print_PrintDocCallback

```c
typedef struct Print_PrintDocCallback {...} Print_PrintDocCallback
```

## Overview

Defines a struct for the print job state callback.

**Since**: 13

**Related module**: [Print](capi-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Print_OnStartLayoutWrite](capi-ohprint-h.md#print_onstartlayoutwrite) startLayoutWriteCb | Callback to be invoked when the file write-back starts. |
| [Print_OnJobStateChanged](capi-ohprint-h.md#print_onjobstatechanged) jobStateChangedCb | Callback to be invoked when the print job state changes. |


