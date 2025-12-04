# JSVM_PropertyHandlerConfigurationStruct
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} JSVM_PropertyHandlerConfigurationStruct
```

## Overview

Defines a struct for triggering the corresponding callback when the getter, setter, deleter, or enumerator of an object is executed.

**Since**: 12

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name                              | Description|
|----------------------------------| -- |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) namedPropertyData | Data used for name property callback.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) indexedPropertyData   | Data used for index property callback.|


### Member Functions

| Name| Description|
| -- | -- |
| [JSVM_Value (JSVM_CDECL* genericNamedPropertyGetterCallback)(JSVM_Env env,JSVM_Value name,JSVM_Value thisArg,JSVM_Value namedPropertyData)](#genericnamedpropertygettercallback) | Callback triggered by obtaining the name property of an instance object.|
| [JSVM_Value (JSVM_CDECL* genericNamedPropertySetterCallback)(JSVM_Env env,JSVM_Value name,JSVM_Value property,JSVM_Value thisArg,JSVM_Value namedPropertyData)](#genericnamedpropertysettercallback) | Callback triggered by setting the name property of an instance object.|
| [JSVM_Value (JSVM_CDECL* genericNamedPropertyDeleterCallback)(JSVM_Env env,JSVM_Value name,JSVM_Value thisArg,JSVM_Value namedPropertyData)](#genericnamedpropertydeletercallback) | Callback triggered by deleting the name property of an instance object.|
| [JSVM_Value (JSVM_CDECL* genericNamedPropertyEnumeratorCallback)(JSVM_Env env,JSVM_Value thisArg,JSVM_Value namedPropertyData)](#genericnamedpropertyenumeratorcallback) | Callback triggered by obtaining all name properties of an object.|
| [JSVM_Value (JSVM_CDECL* genericIndexedPropertyGetterCallback)(JSVM_Env env,JSVM_Value index,JSVM_Value thisArg,JSVM_Value indexedPropertyData)](#genericindexedpropertygettercallback) | Callback triggered by obtaining the index property of an instance object.|
| [JSVM_Value (JSVM_CDECL* genericIndexedPropertySetterCallback)(JSVM_Env env,JSVM_Value index,JSVM_Value property,JSVM_Value thisArg,JSVM_Value indexedPropertyData)](#genericindexedpropertysettercallback) | Callback triggered by setting the index property of an instance object.|
| [JSVM_Value (JSVM_CDECL* genericIndexedPropertyDeleterCallback)(JSVM_Env env,JSVM_Value index,JSVM_Value thisArg,JSVM_Value indexedPropertyData)](#genericindexedpropertydeletercallback) | Callback triggered by deleting the index property of an instance object.|
| [JSVM_Value (JSVM_CDECL* genericIndexedPropertyEnumeratorCallback)(JSVM_Env env,JSVM_Value thisArg,JSVM_Value indexedPropertyData)](#genericindexedpropertyenumeratorcallback) | Callback triggered by obtaining all index properties of an object.|

## Member Function Description

### genericNamedPropertyGetterCallback()

```
JSVM_Value (JSVM_CDECL* genericNamedPropertyGetterCallback)(JSVM_Env env,JSVM_Value name,JSVM_Value thisArg,JSVM_Value namedPropertyData)
```

**Description**

Callback triggered by obtaining the name property of an instance object.

### genericNamedPropertySetterCallback()

```
JSVM_Value (JSVM_CDECL* genericNamedPropertySetterCallback)(JSVM_Env env,JSVM_Value name,JSVM_Value property,JSVM_Value thisArg,JSVM_Value namedPropertyData)
```

**Description**

Callback triggered by setting the name property of an instance object.

### genericNamedPropertyDeleterCallback()

```
JSVM_Value (JSVM_CDECL* genericNamedPropertyDeleterCallback)(JSVM_Env env,JSVM_Value name,JSVM_Value thisArg,JSVM_Value namedPropertyData)
```

**Description**

Callback triggered by deleting the name property of an instance object.

### genericNamedPropertyEnumeratorCallback()

```
JSVM_Value (JSVM_CDECL* genericNamedPropertyEnumeratorCallback)(JSVM_Env env,JSVM_Value thisArg,JSVM_Value namedPropertyData)
```

**Description**

Callback triggered by obtaining all name properties on an object.

### genericIndexedPropertyGetterCallback()

```
JSVM_Value (JSVM_CDECL* genericIndexedPropertyGetterCallback)(JSVM_Env env,JSVM_Value index,JSVM_Value thisArg,JSVM_Value indexedPropertyData)
```

**Description**

Callback triggered by obtaining the index property of an instance object.

### genericIndexedPropertySetterCallback()

```
JSVM_Value (JSVM_CDECL* genericIndexedPropertySetterCallback)(JSVM_Env env,JSVM_Value index,JSVM_Value property,JSVM_Value thisArg,JSVM_Value indexedPropertyData)
```

**Description**

Callback triggered by setting the index property of an instance object.

### genericIndexedPropertyDeleterCallback()

```
JSVM_Value (JSVM_CDECL* genericIndexedPropertyDeleterCallback)(JSVM_Env env,JSVM_Value index,JSVM_Value thisArg,JSVM_Value indexedPropertyData)
```

**Description**

Callback triggered by deleting the index property of an instance object.

### genericIndexedPropertyEnumeratorCallback()

```
JSVM_Value (JSVM_CDECL* genericIndexedPropertyEnumeratorCallback)(JSVM_Env env,JSVM_Value thisArg,JSVM_Value indexedPropertyData)
```

**Description**

Callback triggered by obtaining all index properties on an object.
