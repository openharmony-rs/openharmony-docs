# OH_ImageProcessing

<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zy_194-->
<!--Designer: @gongzheng92-->
<!--Tester: @gongzheng92-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=4cd4cb90c88f953e1b5edbcf7d31625a056fa066 translatedAt=2026-11-13T03:37:48.787Z pushedAt=2026-11-13T10:43:56.739Z nl=1 -->

```c
typedef struct OH_ImageProcessing OH_ImageProcessing
```

## Overview

The OH_ImageProcessing struct provides its declaration.

This struct defines an **OH_ImageProcessing** pointer initialized to null, and calls [OH_ImageProcessing_Create](capi-image-processing-h.md#oh_imageprocessing_create) to create an image processing instance. Before calling this API, ensure that the pointer passed in is null. Users can create multiple image processing instances based on different image processing types.

**Since**: 13

**Related module**: [ImageProcessing](capi-imageprocessing.md)

**Header file**: [image_processing_types.h](capi-image-processing-types-h.md)

