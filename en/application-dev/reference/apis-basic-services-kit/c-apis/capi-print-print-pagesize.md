# Print_PageSize

```c
typedef struct Print_PageSize {...} Print_PageSize
```

## Overview

Represents the paper size information in a print task, including key attributes such as the paper ID, name, width, and height. This API can be used to specify or query paper specifications during printing configuration.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Related module**: [Print](capi-others-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char *id | Unique ID of the paper size, which is used to distinguish different paper specifications. |
| char *name | Name of the paper size, for example, **A4** or **Letter**. |
| uint32_t width | Paper width, in mils (1 mil = 1/1000 inch). The value must be greater than **0**. |
| uint32_t height | Paper height, in mils (1 mil = 1/1000 inch). The value must be greater than **0**. |


