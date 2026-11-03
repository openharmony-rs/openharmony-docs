# Print_StringList

```c
typedef struct Print_StringList {...} Print_StringList
```

## Overview

Represents a string list, which is used to transfer multiple strings in the print module. This struct uses the **count** field to record the number of strings and the **list** field to point to the string array. It can be used to transfer multiple strings in batches. For details about related APIs, see OH_Print.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Related module**: [Print](capi-others-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t count | String count, which indicates the number of elements in the **list** array. |
| char **list | Pointer to the string array. The number of elements in the array must be the same as the value of **count**. |


