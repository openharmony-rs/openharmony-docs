# JSVM_PropertyDescriptor

```c
typedef struct JSVM_PropertyDescriptor {...} JSVM_PropertyDescriptor
```

## Overview

Property descriptor.

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char* utf8name | Optional string describing the key for the property, encoded as UTF8. One of utf8name or name must be provided for the property. |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) name | Optional value that points to a JavaScript string or symbol to be used as the key for the property. |
| JSVM_Callback method | Set this to make the property descriptor object's value property to be a JavaScript function represented by method. |
| JSVM_Callback getter | A function to call when a get access of the property is performed. |
| JSVM_Callback setter | A function to call when a set access of the property is performed. |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | The value that's retrieved by a get access of the property if the property is a data property. |
| [JSVM_PropertyAttributes](capi-jsvm-types-h.md#jsvm_propertyattributes) attributes | The attributes associated with the particular property. |


