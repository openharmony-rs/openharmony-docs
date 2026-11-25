# ArkUI_LayoutConstraint
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fenglinbailu-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=2ef784f0bdab28245033ef8be92f653a500e646d translatedAt=2026-11-23T07:05:12.283Z pushedAt=2026-11-24T09:24:35.279Z nl=1 -->

```c
typedef struct ArkUI_LayoutConstraint ArkUI_LayoutConstraint
```

## Overview

Defines the layout constraint, which is used to limit the size range during component layout. You can set the minimum and maximum size constraints. The constraint values are non-negative floating-point numbers. During component layout, the system limits the final size range of the component based on the constraint values to ensure that the layout result meets the constraints. This struct is applicable to scenarios where the size range of child components needs to be controlled during custom layout container design. For example, in a waterfall layout, the height of image cards can be limited; in a grid layout, the size of cells can be limited. It is also applicable to scenarios where the upper and lower limits of the component size need to be restricted. For example, the maximum width of an image display component can be limited to prevent stretching, and the minimum size can be limited in a responsive layout to ensure readability. This prevents the component size from exceeding the expected range, enabling more precise layout control, improving the predictability and stability of the layout, and enhancing the controllability of the interface.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [common_type.h](capi-common-type-h.md)
