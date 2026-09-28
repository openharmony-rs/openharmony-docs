# ArkUI_AccessibleRangeInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=c18a4e1567d098b4c6780d709d006d4ba2f2faab translatedAt=2026-09-18T11:16:52.226Z pushedAt=2026-09-20T07:14:25.654Z -->

```c
typedef struct {...} ArkUI_AccessibleRangeInfo
```

## Overview

Represents the range value information of a specific component (such as [Slider](arkui-ts/ts-basic-components-slider.md), [Rating](arkui-ts/ts-basic-components-rating.md), and [Progress](arkui-ts/ts-basic-components-progress.md)), including the current value, maximum value, and minimum value, for the accessibility service to read and announce to users.

**Since**: 13

**Related module**: [ArkUI_Accessibility](capi-arkui-accessibility.md)

**Header file**: [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| double min | Minimum value of the component.|
| double max | Maximum value of the component.|
| double current | Current value of the component.|


