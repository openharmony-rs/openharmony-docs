# oh_preferences.h

## Overview

Provides APIs and structs for accessing the **Preferences** object.

**Library**: libohpreferences.so

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Since**: 13

**Related module**: [Preferences](capi-preferences.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Preferences](capi-preferences-oh-preferences.md) | OH_Preferences | Represents a **Preferences** object. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_PreferencesDataObserver)(void *context, const OH_PreferencesPair *pairs, uint32_t count)](#oh_preferencesdataobserver) | OH_PreferencesDataObserver | Defines a struct for the callback for data changes. |
| [OH_Preferences *OH_Preferences_Open(OH_PreferencesOption *option, int *errCode)](#oh_preferences_open) | - | Opens a **Preferences** instance and creates a pointer to it. If this pointer is no longer required, use [OH_Preferences_Close](capi-oh-preferences-h.md#oh_preferences_close) to close the instance. |
| [int OH_Preferences_Close(OH_Preferences *preference)](#oh_preferences_close) | - | Closes a **Preferences** instance. |
| [int OH_Preferences_DeletePreferences(OH_PreferencesOption *option)](#oh_preferences_deletepreferences) | - | Deletes the specified **Preferences** object. |
| [int OH_Preferences_GetInt(OH_Preferences *preference, const char *key, int *value)](#oh_preferences_getint) | - | Obtains an integer corresponding to the specified key in a **Preferences** instance. |
| [int OH_Preferences_GetBool(OH_Preferences *preference, const char *key, bool *value)](#oh_preferences_getbool) | - | Obtains a Boolean value corresponding to the specified key in a **Preferences** instance. |
| [int OH_Preferences_GetString(OH_Preferences *preference, const char *key, char **value, uint32_t *valueLen)](#oh_preferences_getstring) | - | Obtains a string corresponding to the specified key in a **Preferences** instance. |
| [void OH_Preferences_FreeString(char *string)](#oh_preferences_freestring) | - | Releases a string obtained from a **Preferences** instance. |
| [int OH_Preferences_SetInt(OH_Preferences *preference, const char *key, int value)](#oh_preferences_setint) | - | Sets an integer based on the specified key in a **Preferences** instance. |
| [int OH_Preferences_SetBool(OH_Preferences *preference, const char *key, bool value)](#oh_preferences_setbool) | - | Sets a Boolean value based on the specified key in a **Preferences** instance. |
| [int OH_Preferences_SetString(OH_Preferences *preference, const char *key, const char *value)](#oh_preferences_setstring) | - | Sets a string based on the specified key in a **Preferences** instance. |
| [int OH_Preferences_Delete(OH_Preferences *preference, const char *key)](#oh_preferences_delete) | - | Deletes the KV data corresponding to the specified key from a **Preferences** instance. |
| [int OH_Preferences_RegisterDataObserver(OH_Preferences *preference, void *context, OH_PreferencesDataObserver observer, const char *keys[], uint32_t keyCount)](#oh_preferences_registerdataobserver) | - | Subscribes to data changes of the specified keys. If the value of the specified key changes, a callback will be invoked after **OH_Preferences_Close()** is called. |
| [int OH_Preferences_UnregisterDataObserver(OH_Preferences *preference, void *context, OH_PreferencesDataObserver observer, const char *keys[], uint32_t keyCount)](#oh_preferences_unregisterdataobserver) | - | Unsubscribes from data changes of the specified keys. |
| [int OH_Preferences_IsStorageTypeSupported(Preferences_StorageType type, bool *isSupported)](#oh_preferences_isstoragetypesupported) | - | Check if a type is supported or not. |
| [int OH_Preferences_SetValue(OH_Preferences *preference, const char *key, OH_PreferencesValue *value)](#oh_preferences_setvalue) | - | Sets {@link OH_PreferencesValue} in the **Preferences** object. |
| [int OH_Preferences_GetValue(OH_Preferences *preference, const char *key, OH_PreferencesValue **value)](#oh_preferences_getvalue) | - | Obtains the value from the **Preferences** object based on the given key. |
| [int OH_Preferences_GetAll(OH_Preferences *preference, OH_PreferencesPair **pairs, uint32_t *count)](#oh_preferences_getall) | - | Obtains all the values from the **Preferences** object. |
| [bool OH_Preferences_HasKey(OH_Preferences *preference, const char *key)](#oh_preferences_haskey) | - | Checks whether the **Preferences** object contains KV data matching the specified key. Returns **true** if present, and **false** otherwise. |
| [int OH_Preferences_Flush(OH_Preferences *preference)](#oh_preferences_flush) | - | Saves the cache of the [OH_Preferences](capi-preferences-oh-preferences.md) object to an XML file. |
| [int OH_Preferences_ClearCache(OH_Preferences *preference)](#oh_preferences_clearcache) | - | Clears all values in the cache of the [OH_Preferences](capi-preferences-oh-preferences.md) object. |
| [int OH_Preferences_RegisterMultiProcessDataObserver(OH_Preferences *preference, void *context, OH_PreferencesDataObserver observer)](#oh_preferences_registermultiprocessdataobserver) | - | Registers a multi-process data observer for the **Preferences** object. |
| [int OH_Preferences_UnregisterMultiProcessDataObserver(OH_Preferences *preference, void *context, OH_PreferencesDataObserver observer)](#oh_preferences_unregistermultiprocessdataobserver) | - | Unregisters the multi-process data observer of the **Preferences** object. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_PreferencesDataObserver)(void *context, const OH_PreferencesPair *pairs, uint32_t count) | Defines a struct for the callback for data changes.<br>**Since**: 13 |

## Function description

### OH_PreferencesDataObserver()

```c
typedef void (*OH_PreferencesDataObserver)(void *context, const OH_PreferencesPair *pairs, uint32_t count)
```

**Description**

Defines a struct for the callback for data changes.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| void \*context | Pointer to the application context. |
| const OH_PreferencesPair \*pairs | Pointer to the changed KV data. |
| uint32_t count | Number of KV pairs changed. |

**Reference**:

OH_PreferencesPair


### OH_Preferences_Open()

```c
OH_Preferences *OH_Preferences_Open(OH_PreferencesOption *option, int *errCode)
```

**Description**

Opens a **Preferences** instance and creates a pointer to it. If this pointer is no longer required, use [OH_Preferences_Close](capi-oh-preferences-h.md#oh_preferences_close) to close the instance.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_PreferencesOption *option | Pointer to the {@link OH_PreferencesOption} instance. |
| int *errCode | Pointer to the error code returned. For details, see {@link OH_Preferences_ErrCode}. **PREFERENCES_OK** indicates the operation is successful. **PREFERENCES_ERROR_INVALID_PARAM** indicates invalid parameters are specified. **PREFERENCES_ERROR_NOT_SUPPORTED** indicates the system capability is not supported. **PREFERENCES_ERROR_DELETE_FILE** indicates the file fails to be deleted. **PREFERENCES_ERROR_STORAGE** indicates the storage is abnormal. **PREFERENCES_ERROR_MALLOC** indicates a failure in memory allocation. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Preferences *](capi-preferences-oh-preferences.md) | Returns a pointer to the [OH_Preferences](capi-preferences-oh-preferences.md) instance opened if the operation is successful; returns a  null pointer otherwise. |

**Reference**:

OH_Preferences OH_PreferencesOption


### OH_Preferences_Close()

```c
int OH_Preferences_Close(OH_Preferences *preference)
```

**Description**

Closes a **Preferences** instance.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Preferences](capi-preferences-oh-preferences.md) *preference | Pointer to the [OH_Preferences](capi-preferences-oh-preferences.md) instance to close. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code. For details, see {@link OH_Preferences_ErrCode}.  PREFERENCES_OK indicates the operation is successful.  PREFERENCES_ERROR_INVALID_PARAM indicates invalid parameters are specified.  PREFERENCES_ERROR_STORAGE indicates the storage is abnormal.  PREFERENCES_ERROR_MALLOC indicates a failure in memory allocation. |

**Reference**:

OH_Preferences


### OH_Preferences_DeletePreferences()

```c
int OH_Preferences_DeletePreferences(OH_PreferencesOption *option)
```

**Description**

Deletes the specified **Preferences** object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_PreferencesOption *option | Pointer to the {@link OH_PreferencesOption} instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code.  PREFERENCES_OK indicates the operation is successful.  PREFERENCES_ERROR_INVALID_PARAM indicates invalid parameters are specified.  PREFERENCES_ERROR_NOT_SUPPORTED indicates the system capability is not supported.  PREFERENCES_ERROR_DELETE_FILE indicates the file fails to be deleted. |

**Reference**:

OH_Preferences


### OH_Preferences_GetInt()

```c
int OH_Preferences_GetInt(OH_Preferences *preference, const char *key, int *value)
```

**Description**

Obtains an integer corresponding to the specified key in a **Preferences** instance.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Preferences](capi-preferences-oh-preferences.md) *preference | Pointer to the [OH_Preferences](capi-preferences-oh-preferences.md) instance. |
| const char *key | Pointer to the key of the value to obtain. |
| int *value | Pointer to the integer value obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code.  PREFERENCES_OK indicates the operation is successful.  PREFERENCES_ERROR_INVALID_PARAM indicates invalid parameters are specified.  PREFERENCES_ERROR_STORAGE indicates the storage is abnormal.  PREFERENCES_ERROR_MALLOC indicates a failure in memory allocation.  PREFERENCES_ERROR_KEY_NOT_FOUND indicates the specified key does not exist. |

**Reference**:

OH_Preferences


### OH_Preferences_GetBool()

```c
int OH_Preferences_GetBool(OH_Preferences *preference, const char *key, bool *value)
```

**Description**

Obtains a Boolean value corresponding to the specified key in a **Preferences** instance.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Preferences](capi-preferences-oh-preferences.md) *preference | Pointer to the [OH_Preferences](capi-preferences-oh-preferences.md) instance. |
| const char *key | Pointer to the key of the value to obtain. |
| bool *value | Pointer to the Boolean value obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code.  PREFERENCES_OK indicates the operation is successful.  PREFERENCES_ERROR_INVALID_PARAM indicates invalid parameters are specified.  PREFERENCES_ERROR_STORAGE indicates the storage is abnormal.  PREFERENCES_ERROR_MALLOC indicates a failure in memory allocation.  PREFERENCES_ERROR_KEY_NOT_FOUND indicates the specified key does not exist. |

**Reference**:

OH_Preferences


### OH_Preferences_GetString()

```c
int OH_Preferences_GetString(OH_Preferences *preference, const char *key, char **value, uint32_t *valueLen)
```

**Description**

Obtains a string corresponding to the specified key in a **Preferences** instance.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Preferences](capi-preferences-oh-preferences.md) *preference | Pointer to the [OH_Preferences](capi-preferences-oh-preferences.md) instance. |
| const char *key | Pointer to the key of the value to obtain. |
| char **value | Double pointer to the string obtained. If the string is not required, you can use [OH_Preferences_FreeString](capi-oh-preferences-h.md#oh_preferences_freestring) to free the string (release the memory occupied by the string). |
| uint32_t *valueLen | Pointer to the length of the string obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code.  PREFERENCES_OK indicates the operation is successful.  PREFERENCES_ERROR_INVALID_PARAM indicates invalid parameters are specified.  PREFERENCES_ERROR_STORAGE indicates the storage is abnormal.  PREFERENCES_ERROR_MALLOC indicates a failure in memory allocation.  PREFERENCES_ERROR_KEY_NOT_FOUND indicates the specified key does not exist. |

**Reference**:

OH_Preferences


### OH_Preferences_FreeString()

```c
void OH_Preferences_FreeString(char *string)
```

**Description**

Releases a string obtained from a **Preferences** instance.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| char *string | Pointer to the string to release. |

**Reference**:

OH_Preferences


### OH_Preferences_SetInt()

```c
int OH_Preferences_SetInt(OH_Preferences *preference, const char *key, int value)
```

**Description**

Sets an integer based on the specified key in a **Preferences** instance.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Preferences](capi-preferences-oh-preferences.md) *preference | Pointer to the [OH_Preferences](capi-preferences-oh-preferences.md) instance. |
| const char *key | Pointer to the key of the value to set. |
| int value | Integer value to be set. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code.  PREFERENCES_OK indicates the operation is successful.  PREFERENCES_ERROR_INVALID_PARAM indicates invalid parameters are specified.  PREFERENCES_ERROR_STORAGE indicates the storage is abnormal.  PREFERENCES_ERROR_MALLOC indicates a failure in memory allocation. |

**Reference**:

OH_Preferences


### OH_Preferences_SetBool()

```c
int OH_Preferences_SetBool(OH_Preferences *preference, const char *key, bool value)
```

**Description**

Sets a Boolean value based on the specified key in a **Preferences** instance.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Preferences](capi-preferences-oh-preferences.md) *preference | Pointer to the [OH_Preferences](capi-preferences-oh-preferences.md) instance. |
| const char *key | Pointer to the key of the value to set. |
| bool value | Boolean value to be set. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code.  PREFERENCES_OK indicates the operation is successful.  PREFERENCES_ERROR_INVALID_PARAM indicates invalid parameters are specified.  PREFERENCES_ERROR_STORAGE indicates the storage is abnormal.  PREFERENCES_ERROR_MALLOC indicates a failure in memory allocation. |

**Reference**:

OH_Preferences


### OH_Preferences_SetString()

```c
int OH_Preferences_SetString(OH_Preferences *preference, const char *key, const char *value)
```

**Description**

Sets a string based on the specified key in a **Preferences** instance.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Preferences](capi-preferences-oh-preferences.md) *preference | Pointer to the [OH_Preferences](capi-preferences-oh-preferences.md) instance. |
| const char *key | Pointer to the key of the value to set. |
| const char *value | Pointer to the string to set. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code.  PREFERENCES_OK indicates the operation is successful.  PREFERENCES_ERROR_INVALID_PARAM indicates invalid parameters are specified.  PREFERENCES_ERROR_STORAGE indicates the storage is abnormal.  PREFERENCES_ERROR_MALLOC indicates a failure in memory allocation. |

**Reference**:

OH_Preferences


### OH_Preferences_Delete()

```c
int OH_Preferences_Delete(OH_Preferences *preference, const char *key)
```

**Description**

Deletes the KV data corresponding to the specified key from a **Preferences** instance.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Preferences](capi-preferences-oh-preferences.md) *preference | Pointer to the [OH_Preferences](capi-preferences-oh-preferences.md) instance. |
| const char *key | Pointer to the key of the KV pair to delete. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code.  PREFERENCES_OK indicates the operation is successful.  PREFERENCES_ERROR_INVALID_PARAM indicates invalid parameters are specified.  PREFERENCES_ERROR_STORAGE indicates the storage is abnormal.  PREFERENCES_ERROR_MALLOC indicates a failure in memory allocation. |

**Reference**:

OH_Preferences


### OH_Preferences_RegisterDataObserver()

```c
int OH_Preferences_RegisterDataObserver(OH_Preferences *preference, void *context, OH_PreferencesDataObserver observer, const char *keys[], uint32_t keyCount)
```

**Description**

Subscribes to data changes of the specified keys. If the value of the specified key changes, a callback will be invoked after **OH_Preferences_Close()** is called.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Preferences](capi-preferences-oh-preferences.md) *preference | Pointer to the [OH_Preferences](capi-preferences-oh-preferences.md) instance. |
| void *context | Pointer to the application context. |
| [OH_PreferencesDataObserver](capi-oh-preferences-h.md#oh_preferencesdataobserver) observer | [OH_PreferencesDataObserver](capi-oh-preferences-h.md#oh_preferencesdataobserver) callback to be invoked when data changes. |
| const char *keys[] | Pointer to the keys to observe. |
| uint32_t keyCount | Number of keys. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code.  PREFERENCES_OK indicates the operation is successful.  PREFERENCES_ERROR_INVALID_PARAM indicates invalid parameters are specified.  PREFERENCES_ERROR_STORAGE indicates the storage is abnormal.  PREFERENCES_ERROR_MALLOC indicates a failure in memory allocation.  PREFERENCES_ERROR_GET_DATAOBSMGRCLIENT indicates a failure in obtaining the data change subscription service. |

**Reference**:

OH_Preferences OH_PreferencesDataObserver


### OH_Preferences_UnregisterDataObserver()

```c
int OH_Preferences_UnregisterDataObserver(OH_Preferences *preference, void *context, OH_PreferencesDataObserver observer, const char *keys[], uint32_t keyCount)
```

**Description**

Unsubscribes from data changes of the specified keys.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Preferences](capi-preferences-oh-preferences.md) *preference | Pointer to the [OH_Preferences](capi-preferences-oh-preferences.md) instance. |
| void *context | Pointer to the application context. |
| [OH_PreferencesDataObserver](capi-oh-preferences-h.md#oh_preferencesdataobserver) observer | [OH_PreferencesDataObserver](capi-oh-preferences-h.md#oh_preferencesdataobserver) callback to be invoked when data changes. |
| const char *keys[] | Pointer to the keys observed. If this parameter is null, this API unregisters the listening for all keys. |
| uint32_t keyCount | Number of keys. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code.  PREFERENCES_OK indicates the operation is successful.  PREFERENCES_ERROR_INVALID_PARAM indicates invalid parameters are specified.  PREFERENCES_ERROR_STORAGE indicates the storage is abnormal.  PREFERENCES_ERROR_MALLOC indicates a failure in memory allocation. |

**Reference**:

OH_Preferences OH_PreferencesDataObserver


### OH_Preferences_IsStorageTypeSupported()

```c
int OH_Preferences_IsStorageTypeSupported(Preferences_StorageType type, bool *isSupported)
```

**Description**

Check if a type is supported or not.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| Preferences_StorageType type | the storage type of {@Link Preferences_StorageType}. |
| bool *isSupported | Pointer to the Boolean value obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          {@link PREFERENCES_OK} indicates the operation is successful.<br>        {@link PREFERENCES_ERROR_INVALID_PARAM} indicates invalid args are passed in. |

### OH_Preferences_SetValue()

```c
int OH_Preferences_SetValue(OH_Preferences *preference, const char *key, OH_PreferencesValue *value)
```

**Description**

Sets {@link OH_PreferencesValue} in the **Preferences** object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Preferences](capi-preferences-oh-preferences.md) *preference | Pointer to the target [OH_Preferences](capi-preferences-oh-preferences.md) instance. |
| const char *key | Pointer to the key of the value to set. |
| OH_PreferencesValue *value | Pointer to the {@link OH_PreferencesValue} value to set. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code.  PREFERENCES_OK indicates the operation is successful.  PREFERENCES_ERROR_INVALID_PARAM indicates invalid parameters are specified.  PREFERENCES_ERROR_STORAGE indicates a storage exception.  PREFERENCES_ERROR_MALLOC indicates a failure in memory allocation. |

**Reference**:

OH_Preferences


### OH_Preferences_GetValue()

```c
int OH_Preferences_GetValue(OH_Preferences *preference, const char *key, OH_PreferencesValue **value)
```

**Description**

Obtains the value from the **Preferences** object based on the given key.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Preferences](capi-preferences-oh-preferences.md) *preference | Pointer to the target [OH_Preferences](capi-preferences-oh-preferences.md) instance. |
| const char *key | Pointer to the key of the value to obtain. |
| OH_PreferencesValue **value | Double pointer to {@link OH_PreferencesValue}. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code.  PREFERENCES_OK indicates the operation is successful.  PREFERENCES_ERROR_INVALID_PARAM indicates invalid parameters are specified.  PREFERENCES_ERROR_STORAGE indicates a storage exception.  PREFERENCES_ERROR_MALLOC indicates a failure in memory allocation.  PREFERENCES_ERROR_KEY_NOT_FOUND indicates the specified key does not exist. |

**Reference**:

OH_Preferences


### OH_Preferences_GetAll()

```c
int OH_Preferences_GetAll(OH_Preferences *preference, OH_PreferencesPair **pairs, uint32_t *count)
```

**Description**

Obtains all the values from the **Preferences** object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Preferences](capi-preferences-oh-preferences.md) *preference | Pointer to the target [OH_Preferences](capi-preferences-oh-preferences.md) instance. |
| OH_PreferencesPair **pairs | Pointer to the KV data to obtain. When the KV data is no longer needed, call [OH_Preferences_FreeString](capi-oh-preferences-h.md#oh_preferences_freestring) to free the memory. |
| uint32_t *count | Pointer to the count of all obtained values. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code.  PREFERENCES_OK indicates the operation is successful.  PREFERENCES_ERROR_INVALID_PARAM indicates invalid parameters are specified.  PREFERENCES_ERROR_STORAGE indicates a storage exception.  PREFERENCES_ERROR_MALLOC indicates a failure in memory allocation.  PREFERENCES_ERROR_KEY_NOT_FOUND indicates the specified key does not exist. |

**Reference**:

OH_Preferences


### OH_Preferences_HasKey()

```c
bool OH_Preferences_HasKey(OH_Preferences *preference, const char *key)
```

**Description**

Checks whether the **Preferences** object contains KV data matching the specified key. Returns **true** if present, and **false** otherwise.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Preferences](capi-preferences-oh-preferences.md) *preference | Pointer to the target [OH_Preferences](capi-preferences-oh-preferences.md) instance. |
| const char *key | Pointer to the key to check. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the Preferences object contains KV data that matches the specified key; returns   false otherwise. |

**Reference**:

OH_Preferences


### OH_Preferences_Flush()

```c
int OH_Preferences_Flush(OH_Preferences *preference)
```

**Description**

Saves the cache of the [OH_Preferences](capi-preferences-oh-preferences.md) object to an XML file.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Preferences](capi-preferences-oh-preferences.md) *preference | Pointer to the target [OH_Preferences](capi-preferences-oh-preferences.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code.  PREFERENCES_OK indicates the operation is successful.  PREFERENCES_ERROR_INVALID_PARAM indicates invalid parameters are specified.  PREFERENCES_ERROR_NOT_SUPPORTED indicates the system capability is not supported. |

**Reference**:

OH_Preferences


### OH_Preferences_ClearCache()

```c
int OH_Preferences_ClearCache(OH_Preferences *preference)
```

**Description**

Clears all values in the cache of the [OH_Preferences](capi-preferences-oh-preferences.md) object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Preferences](capi-preferences-oh-preferences.md) *preference | Pointer to the target [OH_Preferences](capi-preferences-oh-preferences.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code.  PREFERENCES_OK indicates the operation is successful.  PREFERENCES_ERROR_INVALID_PARAM indicates invalid parameters are specified.  PREFERENCES_ERROR_NOT_SUPPORTED indicates the system capability is not supported. |

**Reference**:

OH_Preferences


### OH_Preferences_RegisterMultiProcessDataObserver()

```c
int OH_Preferences_RegisterMultiProcessDataObserver(OH_Preferences *preference, void *context, OH_PreferencesDataObserver observer)
```

**Description**

Registers a multi-process data observer for the **Preferences** object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Preferences](capi-preferences-oh-preferences.md) *preference | Pointer to the target [OH_Preferences](capi-preferences-oh-preferences.md) instance. |
| void *context | Pointer to the data observer context. |
| [OH_PreferencesDataObserver](capi-oh-preferences-h.md#oh_preferencesdataobserver) observer | The [OH_PreferencesDataObserver](capi-oh-preferences-h.md#oh_preferencesdataobserver) callback function to register. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code.  PREFERENCES_OK indicates the operation is successful.  PREFERENCES_ERROR_INVALID_PARAM indicates invalid parameters are specified.  PREFERENCES_ERROR_STORAGE indicates a storage exception.  PREFERENCES_ERROR_MALLOC indicates a failure in memory allocation.  PREFERENCES_ERROR_GET_DATAOBSMGRCLIENT indicates a failure in obtaining the data change subscription service. |

**Reference**:

OH_Preferences OH_PreferencesDataObserver


### OH_Preferences_UnregisterMultiProcessDataObserver()

```c
int OH_Preferences_UnregisterMultiProcessDataObserver(OH_Preferences *preference, void *context, OH_PreferencesDataObserver observer)
```

**Description**

Unregisters the multi-process data observer of the **Preferences** object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Preferences](capi-preferences-oh-preferences.md) *preference | Pointer to the target [OH_Preferences](capi-preferences-oh-preferences.md) instance. |
| void *context | Pointer to the data observer context. |
| [OH_PreferencesDataObserver](capi-oh-preferences-h.md#oh_preferencesdataobserver) observer | The [OH_PreferencesDataObserver](capi-oh-preferences-h.md#oh_preferencesdataobserver) callback function to unregister. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns an error code.  PREFERENCES_OK indicates the operation is successful.  PREFERENCES_ERROR_INVALID_PARAM indicates invalid parameters are specified.  PREFERENCES_ERROR_STORAGE indicates a storage exception.  PREFERENCES_ERROR_MALLOC indicates a failure in memory allocation. |

**Reference**:

OH_Preferences OH_PreferencesDataObserver



