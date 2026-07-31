# OH_Filter_ColorMatrix

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanamaru-->
<!--Designer: @chensiyi_CE-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=cb84f8fe2e38bbeba25c5506a75a0804a063c158 translatedAt=2026-07-16T06:36:06.446Z pushedAt=2026-07-16T07:33:44.965Z -->

```c
struct OH_Filter_ColorMatrix {
    // ...
};
```

## Overview

Defines a 4x5 matrix used to create a filter effect, with elements of floating-point values.

**Usage scenarios**

- Filter processing in image editing apps (such as vintage, black and white, warm tone, and other effects)
- Real-time filter effects in video apps
- Beautification and color adjustment features in camera apps
- Image processing scenarios that require custom color transformation effects

The color matrix structure is as follows:

```plaintext
| R' |   | a00 a01 a02 a03 a04 |   | R |
| G' | = | a10 a11 a12 a13 a14 | * | G |
| B' |   | a20 a21 a22 a23 a24 |   | B |
| A' |   | a30 a31 a32 a33 a34 |   | A |
                                   | 1 |
```

The four rows of the matrix correspond to the output color channels R (red), G (green), B (blue), and A (alpha) in sequence; the first four columns correspond to the transformation coefficients of the input color channels R, G, B, and A in sequence, and the fifth column is the constant offset value.

**Since**: 12

**Related module**: [effectKit](capi-effectkit.md)

**Header file**: [effect_types.h](capi-effect-types-h.md)

## Summary

### Member Variables

| Name         | Description                              |
| ------------- | ---------------------------------- |
| float val[20] | Custom color matrix used to implement image color transformation effects. The array contains 20 float elements, stored in row-major order, forming a 4x5 matrix. The first four columns correspond to the transformation coefficients of the R, G, B, and A channels, and the fifth column is the constant offset value. It is recommended that the element values be in the range [-1, 1]. Values outside this range may cause color value overflow or unexpected effects. |