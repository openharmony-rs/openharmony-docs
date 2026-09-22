# oh_preferences_option.h

## Overview

Provides APIs and structs for accessing the **PreferencesOption** object.

**Library**: libohpreferences.so

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Since**: 13

**Related module**: [Preferences](capi-preferences.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_PreferencesOption](capi-preferences-oh-preferencesoption.md) | OH_PreferencesOption | Defines a struct for **Preferences** configuration. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Preferences_StorageType](#preferences_storagetype) | Preferences_StorageType | Enumerates the preferences storage types. |

### Function

| Name | Description |
| -- | -- |
| [OH_PreferencesOption *OH_PreferencesOption_Create(void)](#oh_preferencesoption_create) | Creates a [OH_PreferencesOption](capi-preferences-oh-preferencesoption.md) instance and a pointer to it. If this pointer is no longer required, use [OH_PreferencesOption_Destroy](capi-oh-preferences-option-h.md#oh_preferencesoption_destroy) to destroy it. Otherwise, memory leaks may occur. |
| [int OH_PreferencesOption_SetFileName(OH_PreferencesOption *option, const char *fileName)](#oh_preferencesoption_setfilename) | Sets the file name for an [OH_PreferencesOption](capi-preferences-oh-preferencesoption.md) instance. |
| [int OH_PreferencesOption_SetBundleName(OH_PreferencesOption *option, const char *bundleName)](#oh_preferencesoption_setbundlename) | Sets the bundle name for an [OH_PreferencesOption](capi-preferences-oh-preferencesoption.md) instance. |
| [int OH_PreferencesOption_SetDataGroupId(OH_PreferencesOption *option, const char *dataGroupId)](#oh_preferencesoption_setdatagroupid) | Sets the application group ID for an [OH_PreferencesOption](capi-preferences-oh-preferencesoption.md) instance. After the application group ID is set, the **Preferences** instance will be created in the sandbox directory of the application group ID. The application group ID must be obtained from AppGallery. This parameter is not supported currently. If the application group ID is an empty string, the **Preferences** instance will be created in the sandbox directory of the current application. |
| [int OH_PreferencesOption_SetStorageType(OH_PreferencesOption *option, Preferences_StorageType type)](#oh_preferencesoption_setstoragetype) | Sets the storage type for a **Preferences** instance. |
| [int OH_PreferencesOption_Destroy(OH_PreferencesOption *option)](#oh_preferencesoption_destroy) | Destroys an [OH_PreferencesOption](capi-preferences-oh-preferencesoption.md) instance. |

## Enum type description

### Preferences_StorageType

```c
enum Preferences_StorageType
```

**Description**

Enumerates the preferences storage types.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Since**: 18

| Enum item | Description |
| -- | -- |
| PREFERENCES_STORAGE_XML = 0 | XML. In this type is used, data operations are performed in the memory and data is persisted after {@link OH_Preferences_Close} is called. This type does not multi-processes operations. |
| PREFERENCES_STORAGE_GSKV | CLKV. If this type is used, data operations are flushed on a real-time basis. This type supports multi-process operations. |


## Function description

### OH_PreferencesOption_Create()

```c
OH_PreferencesOption *OH_PreferencesOption_Create(void)
```

**Description**

Creates a [OH_PreferencesOption](capi-preferences-oh-preferencesoption.md) instance and a pointer to it. If this pointer is no longer required, use [OH_PreferencesOption_Destroy](capi-oh-preferences-option-h.md#oh_preferencesoption_destroy) to destroy it. Otherwise, memory leaks may occur.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Since**: 13

**Returns**:

| Type | Description |
| -- | -- |
| [OH_PreferencesOption *](capi-preferences-oh-preferencesoption.md) | Returns a pointer to the [OH_PreferencesOption](capi-preferences-oh-preferencesoption.md) instance created if the operation is successful;  returns a null pointer otherwise. |

**Reference**:

OH_PreferencesOption


### OH_PreferencesOption_SetFileName()

```c
int OH_PreferencesOption_SetFileName(OH_PreferencesOption *option, const char *fileName)
```

**Description**

Sets the file name for an [OH_PreferencesOption](capi-preferences-oh-preferencesoption.md) instance.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PreferencesOption](capi-preferences-oh-preferencesoption.md) *option | Pointer to the [OH_PreferencesOption](capi-preferences-oh-preferencesoption.md) instance. |
| const char *fileName | Pointer to the file name to set. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Error code.  PREFERENCES_OK indicates the operation is successful.  PREFERENCES_ERROR_INVALID_PARAM indicates invalid parameters are specified. |

**Reference**:

OH_PreferencesOption


### OH_PreferencesOption_SetBundleName()

```c
int OH_PreferencesOption_SetBundleName(OH_PreferencesOption *option, const char *bundleName)
```

**Description**

Sets the bundle name for an [OH_PreferencesOption](capi-preferences-oh-preferencesoption.md) instance.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PreferencesOption](capi-preferences-oh-preferencesoption.md) *option | Pointer to the [OH_PreferencesOption](capi-preferences-oh-preferencesoption.md) instance. |
| const char *bundleName | Pointer to the bundle name to set. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Error code.  PREFERENCES_OK indicates the operation is successful.  PREFERENCES_ERROR_INVALID_PARAM indicates invalid parameters are specified. |

**Reference**:

OH_PreferencesOption


### OH_PreferencesOption_SetDataGroupId()

```c
int OH_PreferencesOption_SetDataGroupId(OH_PreferencesOption *option, const char *dataGroupId)
```

**Description**

Sets the application group ID for an [OH_PreferencesOption](capi-preferences-oh-preferencesoption.md) instance. After the application group ID is set, the **Preferences** instance will be created in the sandbox directory of the application group ID. The application group ID must be obtained from AppGallery. This parameter is not supported currently. If the application group ID is an empty string, the **Preferences** instance will be created in the sandbox directory of the current application.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PreferencesOption](capi-preferences-oh-preferencesoption.md) *option | Pointer to the [OH_PreferencesOption](capi-preferences-oh-preferencesoption.md) instance. |
| const char *dataGroupId | Pointer to the application group ID to set. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Error code.  PREFERENCES_OK indicates the operation is successful.  PREFERENCES_ERROR_INVALID_PARAM indicates invalid parameters are specified. |

**Reference**:

OH_PreferencesOption


### OH_PreferencesOption_SetStorageType()

```c
int OH_PreferencesOption_SetStorageType(OH_PreferencesOption *option, Preferences_StorageType type)
```

**Description**

Sets the storage type for a **Preferences** instance.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PreferencesOption](capi-preferences-oh-preferencesoption.md) *option | Pointer to the configuration whose storage type is to set. |
| [Preferences_StorageType](capi-oh-preferences-option-h.md#preferences_storagetype) type | Storage type to set. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Error code.  PREFERENCES_OK indicates the operation is successful.  PREFERENCES_ERROR_INVALID_PARAM indicates invalid parameters are specified. |

**Reference**:

OH_PreferencesOption


### OH_PreferencesOption_Destroy()

```c
int OH_PreferencesOption_Destroy(OH_PreferencesOption *option)
```

**Description**

Destroys an [OH_PreferencesOption](capi-preferences-oh-preferencesoption.md) instance.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PreferencesOption](capi-preferences-oh-preferencesoption.md) *option | Pointer to the [OH_PreferencesOption](capi-preferences-oh-preferencesoption.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Operation status code.  PREFERENCES_OK indicates the operation is successful.  PREFERENCES_ERROR_INVALID_PARAM indicates invalid parameters are specified. |

**Reference**:

OH_PreferencesOption



