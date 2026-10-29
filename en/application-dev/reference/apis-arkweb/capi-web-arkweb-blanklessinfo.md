# ArkWeb_BlanklessInfo
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @Shenxiaoliang1-->
<!--Designer: @kurli1-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=834fb8867c57c74a3b50ed24000e6570d97317a8 translatedAt=2026-10-09T12:41:40.736Z pushedAt=2026-10-12T12:05:43.573Z -->

```c
typedef struct {...} ArkWeb_BlanklessInfo
```

## Overview

Describes the first-screen loading prediction information, including the predicted first-screen similarity value, predicted first-screen loading time, and error code. The app uses this information to decide whether to enable the blankless loading frame insertion solution, which reduces the blank screen time by inserting pre-rendered frames during page loading.

**Since**: 20

**Related module**: [Web](capi-web.md)

**Header file**: [native_interface_arkweb.h](capi-native-interface-arkweb-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| ArkWeb_BlanklessErrorCode errCode | Error code of blankless loading. The value **0** indicates no error, and a non-zero value indicates the error type. For details, see [ArkWeb_BlanklessErrorCode](./capi-arkweb-error-code-h.md#arkweb_blanklesserrorcode). |
| double similarity | Similarity of the first screen. The similarity is calculated based on the first screen content of historical loads. The value ranges from [0, 1.0], where **1.0** indicates a complete match. The closer the value is to 1, the higher the similarity. This value has a lagging nature, meaning the similarity of a local load will only be reflected in the next load. It is recommended that the app does not enable the blankless loading frame insertion solution when the similarity is below a specific threshold (for example, 0.33). |
| int32_t loadingTime | Predicted loading duration of the current load, calculated based on the first screen loading duration of historical loads. Unit: ms. The value must be greater than 0. |

