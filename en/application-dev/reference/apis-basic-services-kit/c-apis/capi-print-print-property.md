# Print_Property

```c
typedef struct Print_Property {...} Print_Property
```

## Overview

Describes the printer properties in key-value pair format. You can use this struct to obtain or set printer properties.

<!--Device-typedef struct Print_Property {...} Print_Property--><!--Device-typedef struct Print_Property {...} Print_Property-End-->

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Related module**: [Print](capi-basic-services-kit-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char *key | Property key, which identifies the type of a printer property. The value must be a valid property name defined in the OH_Print module. |
| char *value | Property value, which corresponds to the property key. The format and valid range of the value depend on the corresponding property key. |


