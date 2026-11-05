# OH_Drawing_String
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=3b75f30d038321e59d140485862ef0f48205e17e translatedAt=2026-11-04T10:31:22.673Z pushedAt=2026-11-04T10:32:38.299Z nl=1 -->

```c
typedef struct {...} OH_Drawing_String
```

## Overview

This struct describes a string of characters encoded in UTF-16.

**Since**: 14

**Related module**: [Drawing](capi-drawing.md)

**Header file**: [drawing_types.h](capi-drawing-types-h.md)

## Summary

### Member Variables

| Name            | Description                                         |
| ---------------- | --------------------------------------------- |
| uint8_t* strData | Pointer to a byte array that stores characters in the UTF-16 encoding format.         |
| uint32_t strLen  | Actual length of the string that **strData** points to, in bytes.|

