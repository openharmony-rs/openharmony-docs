# OH_Drawing_String

```c
typedef struct OH_Drawing_String {...} OH_Drawing_String
```

## Overview

This struct describes a string of characters encoded in UTF-16.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 14

**Related module**: [Drawing](capi-others-drawing.md)

**Header file**: [drawing_types.h](capi-drawing-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t* strData | Pointer to a byte array that stores characters in the UTF-16 encoding format.<br>**Since**: 14 |
| uint32_t strLen | Actual length of the string that **strData** points to, in bytes.<br>**Since**: 14 |


