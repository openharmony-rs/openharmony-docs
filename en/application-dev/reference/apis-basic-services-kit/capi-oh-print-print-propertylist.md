# Print_PropertyList
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=f172f47675a58f89bb693013f28ad2465486c311 translatedAt=2026-10-09T11:44:59.182Z pushedAt=2026-10-10T03:46:28.744Z -->

```cpp
typedef struct {...} Print_PropertyList
```

## Overview

Defines a printer property list, which is used to store and manage printer properties. You can access and operate printer properties in batches by using the property count and the pointer to the property array. **count** indicates the number of properties, and **list** is a pointer to the property array. The two parameters together indicate a complete set of printer properties, which is applicable to scenarios where multiple printer properties need to be queried or set.

**Since**: 12

**Related module**: [OH_Print](capi-oh-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t count | Number of properties. The value must be the same as the actual number of elements in the property array to which **list** points. |
| [Print_Property](capi-oh-print-print-property.md) \*list | Pointer to the property array, which is used to store printer properties. This parameter must be used together with **count**. The array length is specified by **count**. |


