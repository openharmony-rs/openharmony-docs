# OH_ImageProcessing

<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zy_194-->
<!--Designer: @gongzheng92-->
<!--Tester: @gongzheng92-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=d4e58d510018ab97aee0051e4f89bc85d0fa802e translatedAt=2026-11-06T02:16:22.382Z pushedAt=2026-11-12T08:35:49.418Z nl=1 -->

```c
typedef struct OH_ImageProcessing OH_ImageProcessing
```

## Overview

Declares the **OH_ImageProcessing** struct.

This struct defines an **OH_ImageProcessing** pointer initialized to null, and calls [OH_ImageProcessing_Create](capi-image-processing-h.md#oh_imageprocessing_create) to create an image processing instance. Before calling this API, ensure that the pointer passed in is null. Users can create multiple image processing instances based on different image processing types.

**Since**: 13

**Related module**: [ImageProcessing](capi-imageprocessing.md)

**Header file**: [image_processing_types.h](capi-image-processing-types-h.md)

