# ArkUI_LayoutConstraint

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fenglinbailu-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=75a7d62c0702c21a06ca0119552a942305a023cc translatedAt=2026-08-19T08:24:03.835Z pushedAt=2026-08-20T02:11:23.673Z -->

```c
typedef struct ArkUI_LayoutConstraint ArkUI_LayoutConstraint
```

## Overview

Defines the layout constraint for limiting the size range during component layout. It supports setting minimum and maximum sizes, with the values being non-negative floating-point numbers. During component layout, the system limits the final size range of the component based on the constraint values, ensuring that the layout result meets the constraint conditions. This is applicable to controlling the size range of child components in custom layout containers, including the height of image cards in waterfall layouts, cell sizes in grid layouts, and scenario where upper and lower size need to be imposed on components, for example, limiting the maximum width of an image display component to prevent stretching, or restricting the minimum size in responsive layouts to ensure readability. It prevents component sizes from exceeding the expected range, enables more precise layout control, improves layout predictability and stability, and enhances UI controllability.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type.h](capi-native-type-h.md)