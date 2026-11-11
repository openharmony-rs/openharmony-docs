# Scan_ScannerOptions
<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @Zouhaifeng1-->
<!--Designer: @baozewei-->
<!--Tester: @baozewei-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=432796cf3e6a4be981f95a7796deb982eeaff362 translatedAt=2026-11-10T03:58:25.143Z pushedAt=2026-11-10T06:01:59.223Z nl=1 -->

```cpp
typedef struct {...} Scan_ScannerOptions
```

## Overview

Represents the configurable parameter options of a scanner, used to configure scanner parameters, including the option titles, descriptions, configurable ranges, and the number of options. Each option consists of a set of titles, descriptions, and configurable ranges, which are stored as parallel arrays. optionCount indicates the total number of options. A developer can access titles[i], descriptions[i], and ranges[i] simultaneously by using the index i (where 0 ≤ i < optionCount) to obtain the complete information of the i-th option. Ensure that the lengths of the titles, descriptions, and ranges arrays are consistent and equal to optionCount; otherwise, the complete information of an option may not be obtained correctly.

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


