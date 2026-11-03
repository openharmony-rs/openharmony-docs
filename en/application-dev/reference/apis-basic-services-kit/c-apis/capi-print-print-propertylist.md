# Print_PropertyList

```c
typedef struct Print_PropertyList {...} Print_PropertyList
```

## Overview

Defines a printer property list, which is used to store and manage printer properties. You can access and operate printer properties in batches by using the property count and the pointer to the property array. **count**<br>indicates the number of properties, and **list** is a pointer to the property array. The two parameters together indicate a complete set of printer properties, which is applicable to scenarios where multiple printer properties need to be queried or set.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Related module**: [Print](capi-others-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t count | Number of properties. The value must be the same as the actual number of elements in the property array to which **list** points. |
| Print_Property *list | Pointer to the property array, which is used to store printer properties. This parameter must be used together with **count**. The array length is specified by **count**. |


