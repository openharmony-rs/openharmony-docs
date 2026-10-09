# native_huks_param.h

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

## Overview

Provides APIs for constructing, using, and destroying a parameter set.

**File to include**: <huks/native_huks_param.h>

**Library**: libhuks_ndk.z.so

**System capability:**

- API version 20+: SystemCapability.Security.Huks.Core
- API version 9-19: SystemCapability.Security.Huks

**Since**: 9

**Related module**: [HuksParamSetApi](capi-huksparamsetapi.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [struct OH_Huks_Result OH_Huks_InitParamSet(struct OH_Huks_ParamSet **paramSet)](#oh_huks_initparamset) | Initializes a parameter set. No parameter information is required, and the default available memory space is allocated to the parameter set. The initialized parameter set needs to be released by using [OH_Huks_FreeParamSet](capi-native-huks-param-h.md#oh_huks_freeparamset). To add parameters to a parameter set, you need to use [OH_Huks_AddParams](capi-native-huks-param-h.md#oh_huks_addparams) to add parameters and use [OH_Huks_BuildParamSet](capi-native-huks-param-h.md#oh_huks_buildparamset) to construct the parameter set.|
| [struct OH_Huks_Result OH_Huks_AddParams(struct OH_Huks_ParamSet *paramSet, const struct OH_Huks_Param *params, uint32_t paramCnt)](#oh_huks_addparams) | Adds parameters to a parameter set. After the parameters are added, use [OH_Huks_BuildParamSet](capi-native-huks-param-h.md#oh_huks_buildparamset) to construct a parameter set.|
| [struct OH_Huks_Result OH_Huks_BuildParamSet(struct OH_Huks_ParamSet **paramSet)](#oh_huks_buildparamset) | Constructs a parameter set. After [OH_Huks_InitParamSet](capi-native-huks-param-h.md#oh_huks_initparamset) is called to initialize the parameter set and [OH_Huks_AddParams](capi-native-huks-param-h.md#oh_huks_addparams) is called to add parameters, serialize the parameter set and copy the data of the BLOB type to the adjacent memory area at the end of the **paramSet** structure.|
| [void OH_Huks_FreeParamSet(struct OH_Huks_ParamSet **paramSet)](#oh_huks_freeparamset) | Frees a parameter set. This function frees the memory allocated by [OH_Huks_InitParamSet](capi-native-huks-param-h.md#oh_huks_initparamset).|
| [struct OH_Huks_Result OH_Huks_CopyParamSet(const struct OH_Huks_ParamSet *fromParamSet, uint32_t fromParamSetSize, struct OH_Huks_ParamSet **paramSet)](#oh_huks_copyparamset) | Copies a parameter set (deep copy).|
| [struct OH_Huks_Result OH_Huks_GetParam(const struct OH_Huks_ParamSet *paramSet, uint32_t tag, struct OH_Huks_Param **param)](#oh_huks_getparam) | Obtains a parameter from a parameter set.|
| [struct OH_Huks_Result OH_Huks_FreshParamSet(struct OH_Huks_ParamSet *paramSet, bool isCopy)](#oh_huks_freshparamset) | Refreshes the [OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) data in the parameter set.|
| [struct OH_Huks_Result OH_Huks_IsParamSetTagValid(const struct OH_Huks_ParamSet *paramSet)](#oh_huks_isparamsettagvalid) | Checks whether the parameters in a parameter set are valid.|
| [struct OH_Huks_Result OH_Huks_IsParamSetValid(const struct OH_Huks_ParamSet *paramSet, uint32_t size)](#oh_huks_isparamsetvalid) | Checks whether a parameter set is of the valid size.|
| [struct OH_Huks_Result OH_Huks_CheckParamMatch(const struct OH_Huks_Param *baseParam, const struct OH_Huks_Param *param)](#oh_huks_checkparammatch) | Checks whether two parameters are the same.|
| [void OH_Huks_FreeKeyAliasSet(struct OH_Huks_KeyAliasSet *keyAliasSet)](#oh_huks_freekeyaliasset) | Frees a key alias set.|

## Function Description

### OH_Huks_InitParamSet()

```c
struct OH_Huks_Result OH_Huks_InitParamSet(struct OH_Huks_ParamSet **paramSet)
```

**Description**

Initializes a parameter set. No parameter information is required, and the default available memory space is allocated to the parameter set. The initialized parameter set needs to be released by using [OH_Huks_FreeParamSet](capi-native-huks-param-h.md#oh_huks_freeparamset). To add parameters to a parameter set, you need to use [OH_Huks_AddParams](capi-native-huks-param-h.md#oh_huks_addparams) to add parameters and use [OH_Huks_BuildParamSet](capi-native-huks-param-h.md#oh_huks_buildparamset) to construct the parameter set.

**Since**: 9

**Parameters**

| Name| Description|
| -- | -- |
| [struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) **paramSet | Pointer to the parameter set to initialize.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         OH_HUKS_SUCCESS = 0: Initialization successful.<br>         OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY = 12000014: Insufficient memory.<br>         OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT = 401: **paramSet** is invalid.|

### OH_Huks_AddParams()

```c
struct OH_Huks_Result OH_Huks_AddParams(struct OH_Huks_ParamSet *paramSet, const struct OH_Huks_Param *params, uint32_t paramCnt)
```

**Description**

Adds parameters to a parameter set. After the parameters are added, use [OH_Huks_BuildParamSet](capi-native-huks-param-h.md#oh_huks_buildparamset) to construct a parameter set.

**Since**: 9

**Parameters**

| Name| Description|
| -- | -- |
| [struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *paramSet | Pointer to the parameter set to which parameters are to be added. This parameter needs to be initialized by using [OH_Huks_InitParamSet](capi-native-huks-param-h.md#oh_huks_initparamset).|
| [const struct OH_Huks_Param](capi-hukstypeapi-oh-huks-param.md) *params | Pointer to an array of parameters to add.|
| uint32_t paramCnt | Number of parameters to add.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         OH_HUKS_SUCCESS = 0: Operation successful.<br>         OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT = 401: **params** is a null pointer or **paramSet** is invalid.|

### OH_Huks_BuildParamSet()

```c
struct OH_Huks_Result OH_Huks_BuildParamSet(struct OH_Huks_ParamSet **paramSet)
```

**Description**

Constructs a parameter set. After [OH_Huks_InitParamSet](capi-native-huks-param-h.md#oh_huks_initparamset) is called to initialize the parameter set and [OH_Huks_AddParams](capi-native-huks-param-h.md#oh_huks_addparams) is called to add parameters, serialize the parameter set and copy the data of the BLOB type to the adjacent memory area at the end of the **paramSet** structure.

**Since**: 9

**Parameters**

| Name| Description|
| -- | -- |
| [struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) **paramSet | Double pointer to the parameter set to build.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         OH_HUKS_SUCCESS = 0: Operation successful.<br>         OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT = 401: **paramSet** is invalid.<br>         OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY = 12000014: Insufficient memory.|

### OH_Huks_FreeParamSet()

```c
void OH_Huks_FreeParamSet(struct OH_Huks_ParamSet **paramSet)
```

**Description**

Frees a parameter set. This function frees the memory allocated by [OH_Huks_InitParamSet](capi-native-huks-param-h.md#oh_huks_initparamset).

**Since**: 9

**Parameters**

| Name| Description|
| -- | -- |
| [struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) **paramSet | Pointer to the parameter set to free.|

### OH_Huks_CopyParamSet()

```c
struct OH_Huks_Result OH_Huks_CopyParamSet(const struct OH_Huks_ParamSet *fromParamSet, uint32_t fromParamSetSize, struct OH_Huks_ParamSet **paramSet)
```

**Description**

Copies a parameter set (deep copy).

**Since**: 9

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *fromParamSet | Pointer to the parameter set to copy.|
| uint32_t fromParamSetSize | Size of the memory occupied by the copied parameter set.|
| [struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) **paramSet | Double pointer to the new parameter set generated.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         OH_HUKS_SUCCESS = 0: Operation successful.<br>         OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT = 401: **fromParamSet**, **fromParamSetSize**, or **paramSet** is invalid.<br>         OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY = 12000014: Insufficient memory.|

### OH_Huks_GetParam()

```c
struct OH_Huks_Result OH_Huks_GetParam(const struct OH_Huks_ParamSet *paramSet, uint32_t tag, struct OH_Huks_Param **param)
```

**Description**

Obtains a parameter from a parameter set.

**Since**: 9

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *paramSet | Pointer to the parameter set to check.|
| uint32_t tag | Tag value of the parameter to be obtained.|
| [struct OH_Huks_Param](capi-hukstypeapi-oh-huks-param.md) **param | Double pointer to the obtained parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         OH_HUKS_SUCCESS = 0: Operation successful.<br>         OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT = 401: **paramSet** or **param** is invalid, or **param** is not in **paramSet**.|

### OH_Huks_FreshParamSet()

```c
struct OH_Huks_Result OH_Huks_FreshParamSet(struct OH_Huks_ParamSet *paramSet, bool isCopy)
```

**Description**

Refreshes the [OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) data in the parameter set.

**Since**: 9

**Parameters**

| Name| Description|
| -- | -- |
| [struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *paramSet | Pointer to the parameter set to check.|
| bool isCopy | If the value is **true**, the address of the [OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) data is refreshed and copied to the parameter set. If the value is **false**, only the address of the [OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) data is refreshed.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         OH_HUKS_SUCCESS = 0: Operation successful.<br>         OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT = 401: **paramSet** is invalid.<br>         OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY = 12000014: Insufficient memory.|

### OH_Huks_IsParamSetTagValid()

```c
struct OH_Huks_Result OH_Huks_IsParamSetTagValid(const struct OH_Huks_ParamSet *paramSet)
```

**Description**

Checks whether the parameters in a parameter set are valid.

**Since**: 9

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *paramSet | Pointer to the parameter set to check.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         OH_HUKS_SUCCESS = 0: All parameters in **paramSet** are valid.<br>         OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT = 401: **paramSet** is invalid, or the parameter set contains invalid, duplicate, or incorrect tags.|

### OH_Huks_IsParamSetValid()

```c
struct OH_Huks_Result OH_Huks_IsParamSetValid(const struct OH_Huks_ParamSet *paramSet, uint32_t size)
```

**Description**

Checks whether a parameter set is of the valid size.

**Since**: 9

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *paramSet | Pointer to the parameter set to check.|
| uint32_t size | Memory size occupied by the parameter set.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         OH_HUKS_SUCCESS = 0: The size of the parameter set is valid.<br>         **OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT = 401**: The **paramSet** or **size** parameter is invalid.|

### OH_Huks_CheckParamMatch()

```c
struct OH_Huks_Result OH_Huks_CheckParamMatch(const struct OH_Huks_Param *baseParam, const struct OH_Huks_Param *param)
```

**Description**

Checks whether two parameters are the same.

**Since**: 9

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_Param](capi-hukstypeapi-oh-huks-param.md) *baseParam | Pointer to the first parameter to compare.|
| [const struct OH_Huks_Param](capi-hukstypeapi-oh-huks-param.md) *param | Pointer to the second parameter to compare.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         OH_HUKS_SUCCESS = 0: The two parameters to be compared are the same.<br>         **OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT = 401**: One of the parameters is invalid or the parameters do not match.|

### OH_Huks_FreeKeyAliasSet()

```c
void OH_Huks_FreeKeyAliasSet(struct OH_Huks_KeyAliasSet *keyAliasSet)
```

**Description**

Frees a key alias set.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [struct OH_Huks_KeyAliasSet](capi-hukstypeapi-oh-huks-keyaliasset.md) *keyAliasSet | Pointer to the key alias set to be destroyed.|
