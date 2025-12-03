# Scan_ScannerOptions
<!--Kit: Basic Services Kit-->	
<!--Subsystem: Print-->	
<!--Owner: @guoshengbang-->	
<!--Designer: @Q-haosu-->	
<!--Tester: @Q-haosu-->	
<!--Adviser: @fang-jinxu-->

```
typedef struct {...} Scan_ScannerOptions
```

## Overview

Defines all parameter options of a scanner.

**Since**: 12

**Related module**: [OH_Scan](capi-oh-scan.md)

**Header file**: [ohscan.h](capi-ohscan-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char** titles | Option titles.|
| char** descriptions | Option descriptions.|
| char** ranges | Ranges of options.|
| int32_t optionCount | Number of configurable parameter options.|
