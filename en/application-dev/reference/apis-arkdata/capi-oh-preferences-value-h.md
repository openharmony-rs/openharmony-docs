# oh_preferences_value.h
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @ding_dong_dong-->
<!--Designer: @ding_dong_dong-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

## Overview

Provides APIs, enums, and structs for accessing the **PreferencesValue** object.

**File to include**: <database/preferences/oh_preferences_value.h>

**Library**: libohpreferences.so

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Since**: 13

**Related module**: [Preferences](capi-preferences.md)

## Summary

### Structs

| Name                                              | typedef Keyword      | Description                                 |
| -------------------------------------------------- | ------------------- | ------------------------------------- |
| [OH_PreferencesPair](capi-preferences-oh-preferencespair.md)   | OH_PreferencesPair  | Defines a struct for the **Preferences** data in KV format.|
| [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) | OH_PreferencesValue | Defines a struct for the **PreferencesValue** object.       |

### Enums

| Name                                         | typedef Keyword       | Description                            |
| --------------------------------------------- | -------------------- | -------------------------------- |
| [Preference_ValueType](#preference_valuetype) | Preference_ValueType | Enumerates the data types of **PreferencesValue**.|

### Functions

| Name                                                        | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [const char *OH_PreferencesPair_GetKey(const OH_PreferencesPair *pairs, uint32_t index)](#oh_preferencespair_getkey) | Obtains the key based on the specified index from the KV data.                              |
| [const OH_PreferencesValue *OH_PreferencesPair_GetPreferencesValue(const OH_PreferencesPair *pairs, uint32_t index)](#oh_preferencespair_getpreferencesvalue) | Obtains the value based on the specified index from the KV pairs.                              |
| [Preference_ValueType OH_PreferencesValue_GetValueType(const OH_PreferencesValue *object)](#oh_preferencesvalue_getvaluetype) | Obtains the data type of an **OH_PreferencesValue** instance.                        |
| [int OH_PreferencesValue_GetInt(const OH_PreferencesValue *object, int *value)](#oh_preferencesvalue_getint) | Obtains an integer from an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| [int OH_PreferencesValue_GetBool(const OH_PreferencesValue *object, bool *value)](#oh_preferencesvalue_getbool) | Obtains a Boolean value from an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| [int OH_PreferencesValue_GetString(const OH_PreferencesValue *object, char **value, uint32_t *valueLen)](#oh_preferencesvalue_getstring) | Obtains a string from an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| [void OH_PreferencesPair_Destroy(OH_PreferencesPair *pairs, uint32_t count)](#oh_preferencespair_destroy) | Destroys an [OH_PreferencesPair](capi-preferences-oh-preferencespair.md) instance.|
| [OH_PreferencesValue* OH_PreferencesValue_Create(void)](#oh_preferencesvalue_create) | Creates an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| [void OH_PreferencesValue_Destroy(OH_PreferencesValue *value)](#oh_preferencesvalue_destroy) | Destroys an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| [int OH_PreferencesValue_SetInt(const OH_PreferencesValue *object, int value)](#oh_preferencesvalue_setint) | Sets an integer value for an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| [int OH_PreferencesValue_SetBool(const OH_PreferencesValue *object, bool value)](#oh_preferencesvalue_setbool) | Sets a boolean value for an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| [int OH_PreferencesValue_SetString(const OH_PreferencesValue *object, const char *value)](#oh_preferencesvalue_setstring) | Sets a string value for an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| [int OH_PreferencesValue_SetInt64(const OH_PreferencesValue *object, int64_t value)](#oh_preferencesvalue_setint64) | Sets an int64 value for an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| [int OH_PreferencesValue_GetInt64(const OH_PreferencesValue *object, int64_t *value)](#oh_preferencesvalue_getint64) | Obtains an int64 value from an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| [int OH_PreferencesValue_SetDouble(const OH_PreferencesValue *object, double value)](#oh_preferencesvalue_setdouble) | Sets a double value for an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| [int OH_PreferencesValue_GetDouble(const OH_PreferencesValue *object, double *value)](#oh_preferencesvalue_getdouble) | Obtains a double value from an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| [int OH_PreferencesValue_SetIntArray(const OH_PreferencesValue *object, const int *value, uint32_t count)](#oh_preferencesvalue_setintarray) | Sets an integer array for an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| [int OH_PreferencesValue_GetIntArray(const OH_PreferencesValue *object, int **value, uint32_t *count)](#oh_preferencesvalue_getintarray) | Obtains an integer array from an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| [int OH_PreferencesValue_SetBoolArray(const OH_PreferencesValue *object, const bool *value, uint32_t count)](#oh_preferencesvalue_setboolarray) | Sets a boolean array for an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| [int OH_PreferencesValue_GetBoolArray(const OH_PreferencesValue *object, bool **value, uint32_t *count)](#oh_preferencesvalue_getboolarray) | Obtains a boolean array from an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| [int OH_PreferencesValue_SetStringArray(const OH_PreferencesValue *object, const char **value, uint32_t count)](#oh_preferencesvalue_setstringarray) | Sets a string array for an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| [int OH_PreferencesValue_GetStringArray(const OH_PreferencesValue *object, char ***value, uint32_t *count)](#oh_preferencesvalue_getstringarray) | Obtains a string array of an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| [int OH_PreferencesValue_SetInt64Array(const OH_PreferencesValue *object, const int64_t *value, uint32_t count)](#oh_preferencesvalue_setint64array) | Sets an int64 array for an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| [int OH_PreferencesValue_GetInt64Array(const OH_PreferencesValue *object, int64_t **value, uint32_t *count)](#oh_preferencesvalue_getint64array) | Obtains an int64 array from an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| [int OH_PreferencesValue_SetDoubleArray(const OH_PreferencesValue *object, const double *value, uint32_t count)](#oh_preferencesvalue_setdoublearray) | Sets a double array for an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| [int OH_PreferencesValue_GetDoubleArray(const OH_PreferencesValue *object, double **value, uint32_t *count)](#oh_preferencesvalue_getdoublearray) | Obtains a double array of an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| [int OH_PreferencesValue_SetBlob(const OH_PreferencesValue *object, const uint8_t *value, uint32_t count)](#oh_preferencesvalue_setblob) | Sets a blob value for an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| [int OH_PreferencesValue_GetBlob(const OH_PreferencesValue *object, uint8_t **value, uint32_t *count)](#oh_preferencesvalue_getblob) | Obtains a blob value from an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|

## Enum Description

### Preference_ValueType

```c
enum Preference_ValueType
```

**Description**

Enumerates the data types of **PreferencesValue**.

**Since**: 13

| Enum Item                  | Description        |
| ------------------------ | ------------ |
| PREFERENCE_TYPE_NULL = 0 | Null.    |
| PREFERENCE_TYPE_INT      | Integer.  |
| PREFERENCE_TYPE_BOOL     | Boolean.  |
| PREFERENCE_TYPE_STRING   | String.|
| PREFERENCE_TYPE_INT64 | 64-bit integer.<br>**Since**: 23|
| PREFERENCE_TYPE_DOUBLE | Double.<br>**Since**: 23|
| PREFERENCE_TYPE_INT_ARRAY | Integer array.<br>**Since**: 23|
| PREFERENCE_TYPE_BOOL_ARRAY | Boolean array.<br>**Since**: 23|
| PREFERENCE_TYPE_STRING_ARRAY | String array.<br>**Since**: 23|
| PREFERENCE_TYPE_INT64_ARRAY | 64-bit integer array.<br>**Since**: 23|
| PREFERENCE_TYPE_DOUBLE_ARRAY | Double array.<br>**Since**: 23|
| PREFERENCE_TYPE_BLOB | Blob.<br>**Since**: 23|
| PREFERENCE_TYPE_BUTT     | End type.  |


## Function Description

### OH_PreferencesPair_GetKey()

```c
const char *OH_PreferencesPair_GetKey(const OH_PreferencesPair *pairs, uint32_t index)
```

**Description**

Obtains the key based on the specified index from the KV data.

**Since**: 13


**Parameters**

| Name                                                      | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const [OH_PreferencesPair](capi-preferences-oh-preferencespair.md) *pairs | Pointer to the target [OH_PreferencesPair](capi-preferences-oh-preferencespair.md).|
| uint32_t index                                               | Index of the target [OH_PreferencesPair](capi-preferences-oh-preferencespair.md).|

**Returns**

| Type        | Description                                                        |
| ------------ | ------------------------------------------------------------ |
| const char * | Returns the pointer to the key obtained if the operation is successful; returns a null pointer if the operation fails or invalid parameters are specified.|

### OH_PreferencesPair_GetPreferencesValue()

```c
const OH_PreferencesValue *OH_PreferencesPair_GetPreferencesValue(const OH_PreferencesPair *pairs, uint32_t index)
```

**Description**

Obtains the value based on the specified index from the KV pairs.

**Since**: 13


**Parameters**

| Name                                                      | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const [OH_PreferencesPair](capi-preferences-oh-preferencespair.md) *pairs | Pointer to the target [OH_PreferencesPair](capi-preferences-oh-preferencespair.md).|
| uint32_t index                                               | Index of the target [OH_PreferencesPair](capi-preferences-oh-preferencespair.md).|

**Returns**

| Type                                                    | Description                                                        |
| -------------------------------------------------------- | ------------------------------------------------------------ |
| const [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) | Returns the pointer to the value obtained if the operation is successful; returns a null pointer if the operation fails or invalid parameters are specified.|


### OH_PreferencesValue_GetValueType()

```c
Preference_ValueType OH_PreferencesValue_GetValueType(const OH_PreferencesValue *object)
```

**Description**

Obtains the data type of a **PreferencesValue** instance.

**Since**: 13


**Parameters**

| Name                                                      | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | Pointer to the [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|

**Returns**

| Type                                         | Description                                                        |
| --------------------------------------------- | ------------------------------------------------------------ |
| [Preference_ValueType](#preference_valuetype) | Returns the obtained data type. If **PREFERENCE_TYPE_NULL** is returned, invalid parameters are passed in.|

### OH_PreferencesValue_GetInt()

```c
int OH_PreferencesValue_GetInt(const OH_PreferencesValue *object, int *value)
```

**Description**

Obtains an integer from an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 13


**Parameters**

| Name                                                      | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | Pointer to the [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| int *value                                                   | Pointer to the integer value obtained.          |

**Returns**

| Type| Description                                                        |
| ---- | ------------------------------------------------------------ |
| int  | Returns an error code.<br>**PREFERENCES_OK** indicates the operation is successful.<br>**PREFERENCES_ERROR_INVALID_PARAM** indicates invalid parameters are specified.<br>**PREFERENCES_ERROR_STORAGE** indicates a storage exception.<br>**PREFERENCES_ERROR_MALLOC** indicates a failure in memory allocation.|

### OH_PreferencesValue_GetBool()

```c
int OH_PreferencesValue_GetBool(const OH_PreferencesValue *object, bool *value)
```

**Description**

Obtains a Boolean value from an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 13


**Parameters**

| Name                                                      | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | Pointer to the [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| bool *value                                                  | Pointer to the Boolean value obtained.          |

**Returns**

| Type| Description                                                        |
| ---- | ------------------------------------------------------------ |
| int  | Returns an error code.<br>**PREFERENCES_OK** indicates the operation is successful.<br>**PREFERENCES_ERROR_INVALID_PARAM** indicates invalid parameters are specified.<br>**PREFERENCES_ERROR_STORAGE** indicates a storage exception.<br>**PREFERENCES_ERROR_MALLOC** indicates a failure in memory allocation.|

### OH_PreferencesValue_GetString()

```c
int OH_PreferencesValue_GetString(const OH_PreferencesValue *object, char **value, uint32_t *valueLen)
```

**Description**

Obtains a string from an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 13


**Parameters**

| Name                                                      | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | Pointer to the [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| char **value                                                 | Double pointer to the string obtained. If the string is not required, you can use [OH_Preferences_FreeString](capi-oh-preferences-h.md#oh_preferences_freestring) to free the string (release the memory occupied by the string).|
| uint32_t *valueLen                                           | Pointer to the length of the string obtained.      |

**Returns**

| Type| Description                                                        |
| ---- | ------------------------------------------------------------ |
| int  | Returns an error code.<br>**PREFERENCES_OK** indicates the operation is successful.<br>**PREFERENCES_ERROR_INVALID_PARAM** indicates invalid parameters are specified.<br>**PREFERENCES_ERROR_STORAGE** indicates a storage exception.<br>**PREFERENCES_ERROR_MALLOC** indicates a failure in memory allocation.|

### OH_PreferencesPair_Destroy()

```c
void OH_PreferencesPair_Destroy(OH_PreferencesPair *pairs, uint32_t count)
```

**Description**

Destroys an [OH_PreferencesPair](capi-preferences-oh-preferencespair.md) instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_PreferencesPair](capi-preferences-oh-preferencespair.md) *pairs | Pointer to the target [OH_PreferencesPair](capi-preferences-oh-preferencespair.md) instance.|
| uint32_t count | Size of the KV array to be destroyed.|

### OH_PreferencesValue_Create()

```c
OH_PreferencesValue* OH_PreferencesValue_Create(void)
```

**Description**

Creates an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 23

**Returns**

| Type| Description|
| -- | -- |
| [OH_PreferencesValue*](capi-preferences-oh-preferencesvalue.md) | Returns the pointer to the [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) object; returns a null pointer otherwise.|

### OH_PreferencesValue_Destroy()

```c
void OH_PreferencesValue_Destroy(OH_PreferencesValue *value)
```

**Description**

Destroys an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *value | Pointer to the target [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|

### OH_PreferencesValue_SetInt()

```c
int OH_PreferencesValue_SetInt(const OH_PreferencesValue *object, int value)
```

**Description**

Sets an integer value for an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | Pointer to the target [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| int value | Integer value to be set.|

**Returns**

| Type| Description|
| -- | -- |
| int | Returns an error code.<br>**PREFERENCES_OK** indicates the operation is successful.<br>**PREFERENCES_ERROR_INVALID_PARAM** indicates invalid parameters are specified.<br>**PREFERENCES_ERROR_STORAGE** indicates a storage exception.<br>**PREFERENCES_ERROR_MALLOC** indicates a failure in memory allocation.|

### OH_PreferencesValue_SetBool()

```c
int OH_PreferencesValue_SetBool(const OH_PreferencesValue *object, bool value)
```

**Description**

Sets a boolean value for an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | Pointer to the target [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| bool value | Boolean value to be set.|

**Returns**

| Type| Description|
| -- | -- |
| int | Returns an error code.<br>**PREFERENCES_OK** indicates the operation is successful.<br>**PREFERENCES_ERROR_INVALID_PARAM** indicates invalid parameters are specified.<br>**PREFERENCES_ERROR_STORAGE** indicates a storage exception.<br>**PREFERENCES_ERROR_MALLOC** indicates a failure in memory allocation.|

### OH_PreferencesValue_SetString()

```c
int OH_PreferencesValue_SetString(const OH_PreferencesValue *object, const char *value)
```

**Description**

Sets a string value for an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | Pointer to the target [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| const char *value | String value to be set.|

**Returns**

| Type| Description|
| -- | -- |
| int | Returns an error code.<br>**PREFERENCES_OK** indicates the operation is successful.<br>**PREFERENCES_ERROR_INVALID_PARAM** indicates invalid parameters are specified.<br>**PREFERENCES_ERROR_STORAGE** indicates a storage exception.<br>**PREFERENCES_ERROR_MALLOC** indicates a failure in memory allocation.|

### OH_PreferencesValue_SetInt64()

```c
int OH_PreferencesValue_SetInt64(const OH_PreferencesValue *object, int64_t value)
```

**Description**

Sets an int64 value for an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | Pointer to the target [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| int64_t value | Int64 value to be set.|

**Returns**

| Type| Description|
| -- | -- |
| int | Returns an error code.<br>**PREFERENCES_OK** indicates the operation is successful.<br>**PREFERENCES_ERROR_INVALID_PARAM** indicates invalid parameters are specified.<br>**PREFERENCES_ERROR_STORAGE** indicates a storage exception.<br>**PREFERENCES_ERROR_MALLOC** indicates a failure in memory allocation.|

### OH_PreferencesValue_GetInt64()

```c
int OH_PreferencesValue_GetInt64(const OH_PreferencesValue *object, int64_t *value)
```

**Description**

Obtains an int64 value from an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | Pointer to the target [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| int64_t *value | Pointer to the obtained int64 value.|

**Returns**

| Type| Description|
| -- | -- |
| int | Returns an error code.<br>**PREFERENCES_OK** indicates the operation is successful.<br>**PREFERENCES_ERROR_INVALID_PARAM** indicates invalid parameters are specified.<br>**PREFERENCES_ERROR_STORAGE** indicates a storage exception.<br>**PREFERENCES_ERROR_MALLOC** indicates a failure in memory allocation.|

### OH_PreferencesValue_SetDouble()

```c
int OH_PreferencesValue_SetDouble(const OH_PreferencesValue *object, double value)
```

**Description**

Sets a double value for an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | Pointer to the target [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| double value | Double value to be set.|

**Returns**

| Type| Description|
| -- | -- |
| int | Returns an error code.<br>**PREFERENCES_OK** indicates the operation is successful.<br>**PREFERENCES_ERROR_INVALID_PARAM** indicates invalid parameters are specified.<br>**PREFERENCES_ERROR_STORAGE** indicates a storage exception.<br>**PREFERENCES_ERROR_MALLOC** indicates a failure in memory allocation.|

### OH_PreferencesValue_GetDouble()

```c
int OH_PreferencesValue_GetDouble(const OH_PreferencesValue *object, double *value)
```

**Description**

Obtains a double value from an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | Pointer to the target [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| double *value | Pointer to the obtained double value.|

**Returns**

| Type| Description|
| -- | -- |
| int | Returns an error code.<br>**PREFERENCES_OK** indicates the operation is successful.<br>**PREFERENCES_ERROR_INVALID_PARAM** indicates invalid parameters are specified.<br>**PREFERENCES_ERROR_STORAGE** indicates a storage exception.<br>**PREFERENCES_ERROR_MALLOC** indicates a failure in memory allocation.|

### OH_PreferencesValue_SetIntArray()

```c
int OH_PreferencesValue_SetIntArray(const OH_PreferencesValue *object, const int *value, uint32_t count)
```

**Description**

Sets an integer array for an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | Pointer to the target [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| const int *value | Integer array to be set.|
| uint32_t count | Pointer to the size of the array to be set.|

**Returns**

| Type| Description|
| -- | -- |
| int | Returns an error code.<br>**PREFERENCES_OK** indicates the operation is successful.<br>**PREFERENCES_ERROR_INVALID_PARAM** indicates invalid parameters are specified.<br>**PREFERENCES_ERROR_STORAGE** indicates a storage exception.<br>**PREFERENCES_ERROR_MALLOC** indicates a failure in memory allocation.|

### OH_PreferencesValue_GetIntArray()

```c
int OH_PreferencesValue_GetIntArray(const OH_PreferencesValue *object, int **value, uint32_t *count)
```

**Description**

Obtains an integer array from an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | Pointer to the target [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| int **value | Double pointer to the obtained integer array.|
| uint32_t *count | Pointer to the size of the array obtained.|

**Returns**

| Type| Description|
| -- | -- |
| int | Returns an error code.<br>**PREFERENCES_OK** indicates the operation is successful.<br>**PREFERENCES_ERROR_INVALID_PARAM** indicates invalid parameters are specified.<br>**PREFERENCES_ERROR_STORAGE** indicates a storage exception.<br>**PREFERENCES_ERROR_MALLOC** indicates a failure in memory allocation.|

### OH_PreferencesValue_SetBoolArray()

```c
int OH_PreferencesValue_SetBoolArray(const OH_PreferencesValue *object, const bool *value, uint32_t count)
```

**Description**

Sets a boolean array for an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | Pointer to the target [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| const bool *value | Boolean array to be set.|
| uint32_t count | Pointer to the size of the array to be set.|

**Returns**

| Type| Description|
| -- | -- |
| int | Returns an error code.<br>**PREFERENCES_OK** indicates the operation is successful.<br>**PREFERENCES_ERROR_INVALID_PARAM** indicates invalid parameters are specified.<br>**PREFERENCES_ERROR_STORAGE** indicates a storage exception.<br>**PREFERENCES_ERROR_MALLOC** indicates a failure in memory allocation.|

### OH_PreferencesValue_GetBoolArray()

```c
int OH_PreferencesValue_GetBoolArray(const OH_PreferencesValue *object, bool **value, uint32_t *count)
```

**Description**

Obtains a boolean array from an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | Pointer to the target [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| bool **value | Double pointer to the obtained boolean array.|
| uint32_t *count | Pointer to the size of the array obtained.|

**Returns**

| Type| Description|
| -- | -- |
| int | Returns an error code.<br>**PREFERENCES_OK** indicates the operation is successful.<br>**PREFERENCES_ERROR_INVALID_PARAM** indicates invalid parameters are specified.<br>**PREFERENCES_ERROR_STORAGE** indicates a storage exception.<br>**PREFERENCES_ERROR_MALLOC** indicates a failure in memory allocation.|

### OH_PreferencesValue_SetStringArray()

```c
int OH_PreferencesValue_SetStringArray(const OH_PreferencesValue *object, const char **value, uint32_t count)
```

**Description**

Sets a string array for an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | Pointer to the target [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| const char **value | String array to be set.|
| uint32_t count | Pointer to the size of the array to be set.|

**Returns**

| Type| Description|
| -- | -- |
| int | Returns an error code.<br>**PREFERENCES_OK** indicates the operation is successful.<br>**PREFERENCES_ERROR_INVALID_PARAM** indicates invalid parameters are specified.<br>**PREFERENCES_ERROR_STORAGE** indicates a storage exception.<br>**PREFERENCES_ERROR_MALLOC** indicates a failure in memory allocation.|

### OH_PreferencesValue_GetStringArray()

```c
int OH_PreferencesValue_GetStringArray(const OH_PreferencesValue *object, char ***value, uint32_t *count)
```

**Description**

Obtains a string array of an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | Pointer to the target [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| char ***value | Double pointer to the obtained string array.|
| uint32_t *count | Pointer to the size of the array obtained.|

**Returns**

| Type| Description|
| -- | -- |
| int | Returns an error code.<br>**PREFERENCES_OK** indicates the operation is successful.<br>**PREFERENCES_ERROR_INVALID_PARAM** indicates invalid parameters are specified.<br>**PREFERENCES_ERROR_STORAGE** indicates a storage exception.<br>**PREFERENCES_ERROR_MALLOC** indicates a failure in memory allocation.|

### OH_PreferencesValue_SetInt64Array()

```c
int OH_PreferencesValue_SetInt64Array(const OH_PreferencesValue *object, const int64_t *value, uint32_t count)
```

**Description**

Sets an int64 array for an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | Pointer to the target [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| const int64_t *value | Int64 array to be set.|
| uint32_t count | Pointer to the size of the array to be set.|

**Returns**

| Type| Description|
| -- | -- |
| int | Returns an error code.<br>**PREFERENCES_OK** indicates the operation is successful.<br>**PREFERENCES_ERROR_INVALID_PARAM** indicates invalid parameters are specified.<br>**PREFERENCES_ERROR_STORAGE** indicates a storage exception.<br>**PREFERENCES_ERROR_MALLOC** indicates a failure in memory allocation.|

### OH_PreferencesValue_GetInt64Array()

```c
int OH_PreferencesValue_GetInt64Array(const OH_PreferencesValue *object, int64_t **value, uint32_t *count)
```

**Description**

Obtains an int64 array from an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | Pointer to the target [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| int64_t **value | Double pointer to the obtained int64 array.|
| uint32_t *count | Pointer to the size of the array obtained.|

**Returns**

| Type| Description|
| -- | -- |
| int | Returns an error code.<br>**PREFERENCES_OK** indicates the operation is successful.<br>**PREFERENCES_ERROR_INVALID_PARAM** indicates invalid parameters are specified.<br>**PREFERENCES_ERROR_STORAGE** indicates a storage exception.<br>**PREFERENCES_ERROR_MALLOC** indicates a failure in memory allocation.|

### OH_PreferencesValue_SetDoubleArray()

```c
int OH_PreferencesValue_SetDoubleArray(const OH_PreferencesValue *object, const double *value, uint32_t count)
```

**Description**

Sets a double array for an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | Pointer to the target [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| const double *value | Double array to be set.|
| uint32_t count | Pointer to the size of the array to be set.|

**Returns**

| Type| Description|
| -- | -- |
| int | Returns an error code.<br>**PREFERENCES_OK** indicates the operation is successful.<br>**PREFERENCES_ERROR_INVALID_PARAM** indicates invalid parameters are specified.<br>**PREFERENCES_ERROR_STORAGE** indicates a storage exception.<br>**PREFERENCES_ERROR_MALLOC** indicates a failure in memory allocation.|

### OH_PreferencesValue_GetDoubleArray()

```c
int OH_PreferencesValue_GetDoubleArray(const OH_PreferencesValue *object, double **value, uint32_t *count)
```

**Description**

Obtains a double array of an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | Pointer to the target [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| double **value | Double pointer to the obtained double array.|
| uint32_t *count | Pointer to the size of the array obtained.|

**Returns**

| Type| Description|
| -- | -- |
| int | Returns an error code.<br>**PREFERENCES_OK** indicates the operation is successful.<br>**PREFERENCES_ERROR_INVALID_PARAM** indicates invalid parameters are specified.<br>**PREFERENCES_ERROR_STORAGE** indicates a storage exception.<br>**PREFERENCES_ERROR_MALLOC** indicates a failure in memory allocation.|

### OH_PreferencesValue_SetBlob()

```c
int OH_PreferencesValue_SetBlob(const OH_PreferencesValue *object, const uint8_t *value, uint32_t count)
```

**Description**

Sets a blob value for an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | Pointer to the target [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| const uint8_t *value | Blob value to be set.|
| uint32_t count | Pointer to the size of the blob value to be set.|

**Returns**

| Type| Description|
| -- | -- |
| int | Returns an error code.<br>**PREFERENCES_OK** indicates the operation is successful.<br>**PREFERENCES_ERROR_INVALID_PARAM** indicates invalid parameters are specified.<br>**PREFERENCES_ERROR_STORAGE** indicates a storage exception.<br>**PREFERENCES_ERROR_MALLOC** indicates a failure in memory allocation.|

### OH_PreferencesValue_GetBlob()

```c
int OH_PreferencesValue_GetBlob(const OH_PreferencesValue *object, uint8_t **value, uint32_t *count)
```

**Description**

Obtains a blob value from an [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | Pointer to the target [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) instance.|
| uint8_t **value | Double pointer to the obtained blob value.|
| uint32_t *count | Pointer to the size of the blob value obtained.|

**Returns**

| Type| Description|
| -- | -- |
| int | Returns an error code.<br>**PREFERENCES_OK** indicates the operation is successful.<br>**PREFERENCES_ERROR_INVALID_PARAM** indicates invalid parameters are specified.<br>**PREFERENCES_ERROR_STORAGE** indicates a storage exception.<br>**PREFERENCES_ERROR_MALLOC** indicates a failure in memory allocation.|
