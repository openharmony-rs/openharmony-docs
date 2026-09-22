# ArkWeb_BlanklessInfo

```c
typedef struct ArkWeb_BlanklessInfo {...} ArkWeb_BlanklessInfo
```

## Overview

Describes the first-screen loading prediction information, including the predicted first-screen similarity value, predicted first-screen loading time, and error code. The app uses this information to decide whether to enable the blankless loading frame insertion solution, which reduces the blank screen time by inserting pre-rendered frames during page loading.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 20

**Related module**: [Web](capi-web.md)

**Header file**: [native_interface_arkweb.h](capi-native-interface-arkweb-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| ArkWeb_BlanklessErrorCode errCode | Error code of the blankless loading. The value **0** indicates no error, and a non-zero value indicates the error type. For details, see {@link ArkWeb_BlanklessErrorCode}. |
| double similarity | Similarity of the first screen. The similarity is calculated based on the first screen content of historical loads. The value ranges from [0, 1.0], where **1.0** indicates a complete match. The closer the value is to 1, the higher the similarity. This value has a lagging nature, meaning the similarity of a local load will only be reflected in the next load. It is recommended that the app does not enable the blankless loading frame insertion solution when the similarity is below a specific threshold (for example, 0.33). |
| int32_t loadingTime | Predicted loading time of the current load based on the first screen loading time of historical loads, in ms. The value must be greater than 0. |


