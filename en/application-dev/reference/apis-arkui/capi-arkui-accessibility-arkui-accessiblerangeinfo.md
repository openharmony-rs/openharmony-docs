# ArkUI_AccessibleRangeInfo

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e98b791a1f57fab5012a75ce7d9ff0a0466dd410 translatedAt=2026-07-16T10:42:23.467Z pushedAt=2026-07-17T02:31:01.902Z -->

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