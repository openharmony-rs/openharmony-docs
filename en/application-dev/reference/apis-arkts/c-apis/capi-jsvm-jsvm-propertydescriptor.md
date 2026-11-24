# JSVM_PropertyDescriptor

```c
typedef struct JSVM_PropertyDescriptor {...} JSVM_PropertyDescriptor
```

## Overview

Property descriptor.

<!--Device-typedef struct JSVM_PropertyDescriptor {...} JSVM_PropertyDescriptor--><!--Device-typedef struct JSVM_PropertyDescriptor {...} JSVM_PropertyDescriptor-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-arkts-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char* utf8name | Optional string describing the key for the property, encoded as UTF8. One of utf8name or name must be provided for the property.<br><!--Device-const char* utf8name--><!--Device-const char* utf8name-End--> |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) name | Optional value that points to a JavaScript string or symbol to be used as the key for the property.<br><!--Device-JSVM_Value name--><!--Device-JSVM_Value name-End--> |
| JSVM_Callback method | Set this to make the property descriptor object's value property to be a JavaScript function represented by method.<br><!--Device-JSVM_Callback method--><!--Device-JSVM_Callback method-End--> |
| JSVM_Callback getter | A function to call when a get access of the property is performed.<br><!--Device-JSVM_Callback getter--><!--Device-JSVM_Callback getter-End--> |
| JSVM_Callback setter | A function to call when a set access of the property is performed.<br><!--Device-JSVM_Callback setter--><!--Device-JSVM_Callback setter-End--> |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | The value that's retrieved by a get access of the property if the property is a data property.<br><!--Device-JSVM_Value value--><!--Device-JSVM_Value value-End--> |
| [JSVM_PropertyAttributes](capi-jsvm-types-h.md#jsvm_propertyattributes) attributes | The attributes associated with the particular property.<br><!--Device-JSVM_PropertyAttributes attributes--><!--Device-JSVM_PropertyAttributes attributes-End--> |


