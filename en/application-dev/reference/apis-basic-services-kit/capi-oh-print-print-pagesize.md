# Print_PageSize
<!--Kit: Basic Services Kit-->  
<!--Subsystem: Print--> 
<!--Owner: @guoshengbang--> 
<!--Designer: @Q-haosu-->   
<!--Tester: @Q-haosu--> 
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} Print_PageSize
```

## Overview

Defines a struct for the page size.

**Since**: 12

**Related module**: [OH_Print](capi-oh-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char *id | Page ID.|
| char *name | Page name.|
| uint32_t width | Page width.|
| uint32_t height | Page height.|
