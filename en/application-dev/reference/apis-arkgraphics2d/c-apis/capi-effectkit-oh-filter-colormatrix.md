# OH_Filter_ColorMatrix

```c
struct OH_Filter_ColorMatrix {...}
```

## Overview

Defines a 4x5 matrix for creating a filter effect, with elements of floating-point numbers.

**Since**: 12

**Related module**: [effectKit](capi-effectkit.md)

**Header file**: [effect_types.h](capi-effect-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| float val[20] | Custom color matrix used to implement image color transformation effects. The array contains 20 float elements, stored in row-major order, forming a 4x5 matrix. The first 4 columns correspond to the transformation coefficients of the R, G, B, and A channels, and the 5th column is the constant offset value. It is recommended that the element values be within [-1, 1]. Values outside this range may cause color values to overflow or produce unexpected effects. |


