# ArkUI_GridItemRect

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zcdqs-->
<!--Designer: @zcdqs-->
<!--Tester: @liuzhenshuo-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_GridItemRect
```

## Overview

Defines the return value structure for the **onGetRectByIndex** callback in **Grid** layout options.

**Since**: 22

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type.h](capi-native-type-h.md)

**Sample**: <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t rowStart | Starting row position of the **GridItem** component.|
| uint32_t columnStart | Starting column position of the **GridItem** component.|
| uint32_t rowSpan | Number of rows occupied by the **GridItem** component.|
| uint32_t columnSpan | Number of columns occupied by the **GridItem** component.|
