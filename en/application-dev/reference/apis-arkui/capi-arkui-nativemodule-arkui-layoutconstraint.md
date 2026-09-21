# ArkUI_LayoutConstraint
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fenglinbailu-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=45ec2d938cfede23d9ca90fe41c0d1f3e7b2b01d translatedAt=2026-09-20T08:55:23.743Z pushedAt=2026-09-20T10:56:09.647Z -->

```c
typedef struct ArkUI_LayoutConstraint ArkUI_LayoutConstraint
```

## Overview

Defines the layout constraint, which is used to limit the size range during component layout. You can set the minimum and maximum size constraints. The constraint values are non-negative floating-point numbers. During component layout, the system limits the final size range of the component based on the constraint values to ensure that the layout result meets the constraints. This struct is applicable to scenarios where the size range of child components needs to be controlled during custom layout container design. For example, in a waterfall layout, the height of image cards can be limited; in a grid layout, the size of cells can be limited. It is also applicable to scenarios where the upper and lower limits of the component size need to be restricted. For example, the maximum width of an image display component can be limited to prevent stretching, and the minimum size can be limited in a responsive layout to ensure readability. This prevents the component size from exceeding the expected range, enabling more precise layout control, improving the predictability and stability of the layout, and enhancing the controllability of the interface.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type.h](capi-native-type-h.md)

