# JSVM_PropertyHandler

```c
typedef struct JSVM_PropertyHandler {...} JSVM_PropertyHandler
```

## Overview

The property-handler used to define class.

<!--Device-typedef struct JSVM_PropertyHandler {...} JSVM_PropertyHandler--><!--Device-typedef struct JSVM_PropertyHandler {...} JSVM_PropertyHandler-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 18

**Related module**: [JSVM](capi-arkts-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| JSVM_PropertyHandlerCfg propertyHandlerCfg | The instance object triggers the corresponding callback function. |
| JSVM_Callback callAsFunctionCallback | Calling an instance object as a function will trigger this callback. |


