# Print_PropertyList
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @Zouhaifeng1-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=432796cf3e6a4be981f95a7796deb982eeaff362 translatedAt=2026-11-10T03:57:14.963Z pushedAt=2026-11-10T05:59:32.143Z nl=1 -->

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


