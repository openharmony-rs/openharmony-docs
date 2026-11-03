# Print_Margin

```c
typedef struct Print_Margin {...} Print_Margin
```

## Overview

Represents the margin information of a printed page. You can set the margins in the left, top, right, and bottom directions to control the print content area. This API can be used to precisely control the distance between the content and the paper edge during printing. Proper margin settings can prevent content overflow or clipping.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Related module**: [Print](capi-others-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t leftMargin | Left margin, in millimeters. The value must be greater than **0**. |
| uint32_t topMargin | Top margin, in millimeters. The value must be greater than **0**. |
| uint32_t rightMargin | Right margin, in millimeters. The value must be greater than **0**. |
| uint32_t bottomMargin | Bottom margin, in millimeters. The value must be greater than **0**. |


