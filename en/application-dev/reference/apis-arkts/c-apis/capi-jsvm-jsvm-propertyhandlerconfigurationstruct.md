# JSVM_PropertyHandlerConfigurationStruct

```c
typedef struct JSVM_PropertyHandlerConfigurationStruct {...} JSVM_PropertyHandlerConfigurationStruct
```

## Overview

When the object's getter, setter, deleter, and enumerator operations are performed, the corresponding callback will be triggered.

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 12

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) namedPropertyData | data will be utilized by the named property callbacks in this struct. |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) indexedPropertyData | data will be utilized by the indexed property callbacks in this struct. |


### Member functions

| Name | Description |
| -- | -- |
| [JSVM_Value(JSVM_CDECL* genericNamedPropertyGetterCallback)(JSVM_Env env,JSVM_Value name,JSVM_Value thisArg,JSVM_Value namedPropertyData)](#genericnamedpropertygettercallback) | A callback function triggered by getting a named property of an instance object. |
| [JSVM_Value(JSVM_CDECL* genericNamedPropertySetterCallback)(JSVM_Env env,JSVM_Value name,JSVM_Value property,JSVM_Value thisArg,JSVM_Value namedPropertyData)](#genericnamedpropertysettercallback) | A callback function triggered by setting a named property of an instance object. |
| [JSVM_Value(JSVM_CDECL* genericNamedPropertyDeleterCallback)(JSVM_Env env,JSVM_Value name,JSVM_Value thisArg,JSVM_Value namedPropertyData)](#genericnamedpropertydeletercallback) | A callback function triggered by deleting a named property of an instance object. |
| [JSVM_Value(JSVM_CDECL* genericNamedPropertyEnumeratorCallback)(JSVM_Env env,JSVM_Value thisArg,JSVM_Value namedPropertyData)](#genericnamedpropertyenumeratorcallback) | A callback function triggered by getting all named properties requests on an object. |
| [JSVM_Value(JSVM_CDECL* genericIndexedPropertyGetterCallback)(JSVM_Env env,JSVM_Value index,JSVM_Value thisArg,JSVM_Value indexedPropertyData)](#genericindexedpropertygettercallback) | A callback function triggered by getting an indexed property of an instance object. |
| [JSVM_Value(JSVM_CDECL* genericIndexedPropertySetterCallback)(JSVM_Env env,JSVM_Value index,JSVM_Value property,JSVM_Value thisArg,JSVM_Value indexedPropertyData)](#genericindexedpropertysettercallback) | A callback function triggered by setting an indexed property of an instance object. |
| [JSVM_Value(JSVM_CDECL* genericIndexedPropertyDeleterCallback)(JSVM_Env env,JSVM_Value index,JSVM_Value thisArg,JSVM_Value indexedPropertyData)](#genericindexedpropertydeletercallback) | A callback function triggered by deleting an indexed property of an instance object. |
| [JSVM_Value(JSVM_CDECL* genericIndexedPropertyEnumeratorCallback)(JSVM_Env env,JSVM_Value thisArg,JSVM_Value indexedPropertyData)](#genericindexedpropertyenumeratorcallback) | A callback function triggered by getting all indexed properties requests on an object. |

## Member function description

### genericNamedPropertyGetterCallback()

```c
JSVM_Value(JSVM_CDECL* genericNamedPropertyGetterCallback)(JSVM_Env env,JSVM_Value name,JSVM_Value thisArg,JSVM_Value namedPropertyData)
```

**Description**

A callback function triggered by getting a named property of an instance object.

### genericNamedPropertySetterCallback()

```c
JSVM_Value(JSVM_CDECL* genericNamedPropertySetterCallback)(JSVM_Env env,JSVM_Value name,JSVM_Value property,JSVM_Value thisArg,JSVM_Value namedPropertyData)
```

**Description**

A callback function triggered by setting a named property of an instance object.

### genericNamedPropertyDeleterCallback()

```c
JSVM_Value(JSVM_CDECL* genericNamedPropertyDeleterCallback)(JSVM_Env env,JSVM_Value name,JSVM_Value thisArg,JSVM_Value namedPropertyData)
```

**Description**

A callback function triggered by deleting a named property of an instance object.

### genericNamedPropertyEnumeratorCallback()

```c
JSVM_Value(JSVM_CDECL* genericNamedPropertyEnumeratorCallback)(JSVM_Env env,JSVM_Value thisArg,JSVM_Value namedPropertyData)
```

**Description**

A callback function triggered by getting all named properties requests on an object.

### genericIndexedPropertyGetterCallback()

```c
JSVM_Value(JSVM_CDECL* genericIndexedPropertyGetterCallback)(JSVM_Env env,JSVM_Value index,JSVM_Value thisArg,JSVM_Value indexedPropertyData)
```

**Description**

A callback function triggered by getting an indexed property of an instance object.

### genericIndexedPropertySetterCallback()

```c
JSVM_Value(JSVM_CDECL* genericIndexedPropertySetterCallback)(JSVM_Env env,JSVM_Value index,JSVM_Value property,JSVM_Value thisArg,JSVM_Value indexedPropertyData)
```

**Description**

A callback function triggered by setting an indexed property of an instance object.

### genericIndexedPropertyDeleterCallback()

```c
JSVM_Value(JSVM_CDECL* genericIndexedPropertyDeleterCallback)(JSVM_Env env,JSVM_Value index,JSVM_Value thisArg,JSVM_Value indexedPropertyData)
```

**Description**

A callback function triggered by deleting an indexed property of an instance object.

### genericIndexedPropertyEnumeratorCallback()

```c
JSVM_Value(JSVM_CDECL* genericIndexedPropertyEnumeratorCallback)(JSVM_Env env,JSVM_Value thisArg,JSVM_Value indexedPropertyData)
```

**Description**

A callback function triggered by getting all indexed properties requests on an object.


