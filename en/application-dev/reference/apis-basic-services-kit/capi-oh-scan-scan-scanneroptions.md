# Scan_ScannerOptions
<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @baozewei-->
<!--Tester: @baozewei-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=a077482f26289b96749dbeb1a0c6856695ebea0a translatedAt=2026-09-01T03:12:56.175Z pushedAt=2026-09-03T12:33:26.352Z -->

```cpp
typedef struct {...} Scan_ScannerOptions
```

## Overview

Defines the configurable parameters of a scanner. You can configure the title, description, value range, and number of options for each parameter. Each option includes the **titles**, **descriptions**, and **ranges** fields, which are stored as parallel arrays. The **optionCount** field indicates the total number of options. You can use the index i (which must be within the range of [0, **optionCount**)) to access **titles[i]**, **descriptions[i]**, and **ranges[i]** simultaneously to obtain the complete information about option i. Ensure that the array lengths of **titles**, **descriptions**, and **ranges** are the same and equal to the value of **optionCount**. Otherwise, the complete information about the options may not be obtained correctly.

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
| int32_t optionCount | Number of options. |


