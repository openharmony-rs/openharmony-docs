# Print_PrintDocCallback
<!--Kit: Basic Services Kit-->	
<!--Subsystem: Print-->	
<!--Owner: @guoshengbang-->	
<!--Designer: @Q-haosu-->	
<!--Tester: @Q-haosu-->	
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} Print_PrintDocCallback
```

## Overview

Defines the print job callback struct.

**Since**: 13

**Related module**: [OH_Print](capi-oh-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [Print_OnStartLayoutWrite](capi-ohprint-h.md#print_onstartlayoutwrite) startLayoutWriteCb | Callback to be invoked when the file write-back starts.|
| [Print_OnJobStateChanged](capi-ohprint-h.md#print_onjobstatechanged) jobStateChangedCb | Callback to be invoked when the print job state changes.|
