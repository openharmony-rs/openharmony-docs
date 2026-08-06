# ArkWeb_BlanklessInfo

```c
typedef struct ArkWeb_BlanklessInfo {...} ArkWeb_BlanklessInfo
```

## 概述

Describes prediction information about blankless loading, including the first screen similarity, first screenloading duration, and error codes. The application determines whether to enable the blankless loading solution basedon the prediction information.

**起始版本：** 20

**相关模块：** [Web](capi-web.md)

**所在头文件：** [native_interface_arkweb.h](capi-native-interface-arkweb-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| ArkWeb_BlanklessErrorCode errCode | Error codes of blankless loading. For details, see {@link ArkWeb_BlanklessErrorCode}. |
| double similarity | First screen similarity, which is calculated based on the historical first screen content. The value ranges from0 to 1.0. 1.0 indicates that the content is the same. A value closer to 1 indicates a higher similarity. Thisvalue is lagging, and the similarity of the local loading is displayed in the next loading. You are advised notto enable the blankless loading frame insertion solution when the similarity is low. |
| int32_t loadingTime | Loading duration estimated based on the historical first screen loading durations, in milliseconds. The valuemust be greater than 0. |


