# native_interface_bundle.h

## Overview

The file declares the APIs for obtaining the application information, including the bundle name, fingerprint information, and appId.

**Library**: libbundle_ndk.z.so

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**Since**: 9

**Related module**: [Native_Bundle](capi-native-bundle.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_NativeBundle_ApplicationInfo](capi-native-bundle-oh-nativebundle-applicationinfo.md) | OH_NativeBundle_ApplicationInfo | The struct describes the application information, including the bundle name and fingerprint information. |
| [OH_NativeBundle_ElementName](capi-native-bundle-oh-nativebundle-elementname.md) | OH_NativeBundle_ElementName | The struct describes the elementName information. |
| [OH_NativeBundle_Metadata](capi-native-bundle-oh-nativebundle-metadata.md) | OH_NativeBundle_Metadata | The struct describes the metadata information. |
| [OH_NativeBundle_ModuleMetadata](capi-native-bundle-oh-nativebundle-modulemetadata.md) | OH_NativeBundle_ModuleMetadata | The struct describes the metadata of a module. |

### Macro

| Name | Description |
| -- | -- |
| FOUNDATION_APPEXECFWK_STANDARD_KITS_APPKIT_NATIVE_BUNDLE_INCLUDE_NATIVE_INTERFACE_BUNDLE_H | The file declares the APIs for obtaining the application information, including the bundle name, fingerprint information, and appId.<br>**Since**: 9<br>**System capability**: SystemCapability.BundleManager.BundleFramework.Core |

### Function

| Name | Description |
| -- | -- |
| [OH_NativeBundle_ApplicationInfo OH_NativeBundle_GetCurrentApplicationInfo()](#oh_nativebundle_getcurrentapplicationinfo) | Obtains the current application information, including the bundle name and fingerprint information. |
| [char* OH_NativeBundle_GetAppId()](#oh_nativebundle_getappid) | Obtains the appId of the current application. The appId is the unique identifier of an application and is determined by the bundle name and signature information of the application. After using this function, you must manually release the pointer returned to prevent memory leakage. |
| [char* OH_NativeBundle_GetAppIdentifier()](#oh_nativebundle_getappidentifier) | Obtains the appIdentifier of the current application. The appIdentifier does not change throughout the application lifecycle, including version updates, certificate changes, public and private key changes, and application migration. After using this function, you must manually release the pointer returned to prevent memory leakage. |
| [OH_NativeBundle_ElementName OH_NativeBundle_GetMainElementName()](#oh_nativebundle_getmainelementname) | Obtains the mainElement information of the current application, including the bundle name, module name, and ability name. After using this function, you must manually release the pointer returned to prevent memory leakage. |
| [char* OH_NativeBundle_GetCompatibleDeviceType()](#oh_nativebundle_getcompatibledevicetype) | Obtains the compatible device type of the current application. It helps you optimize the layout and font size when distributing mobile applications to tablets or 2-in-1 devices. After using this function, you must manually release the pointer returned to prevent memory leakage. |
| [bool OH_NativeBundle_IsDebugMode(bool* isDebugMode)](#oh_nativebundle_isdebugmode) | Checks whether the current application is in debug mode. |
| [OH_NativeBundle_ModuleMetadata* OH_NativeBundle_GetModuleMetadata(size_t* size)](#oh_nativebundle_getmodulemetadata) | Obtains the module metadata array of the current application. After using this function, you must manually release the pointer returned to prevent memory leakage. |
| [BundleManager_ErrorCode OH_NativeBundle_GetAbilityResourceInfo(char* fileType, OH_NativeBundle_AbilityResourceInfo** abilityResourceInfo, size_t* size)](#oh_nativebundle_getabilityresourceinfo) | Obtain a list of ability that support opening files in a certain format. |

## Function description

### OH_NativeBundle_GetCurrentApplicationInfo()

```c
OH_NativeBundle_ApplicationInfo OH_NativeBundle_GetCurrentApplicationInfo()
```

**Description**

Obtains the current application information, including the bundle name and fingerprint information.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**Since**: 9

**Returns**:

| Type | Description |
| -- | -- |
| [OH_NativeBundle_ApplicationInfo](capi-native-bundle-oh-nativebundle-applicationinfo.md) | Pointer to the OH_NativeBundle_ApplicationInfo object. If the attribute of the returned object is NULL,      the creation fails. The possible cause is that the application address space is full, causing space      allocation to fail. |

### OH_NativeBundle_GetAppId()

```c
char* OH_NativeBundle_GetAppId()
```

**Description**

Obtains the appId of the current application. The appId is the unique identifier of an application and is determined by the bundle name and signature information of the application. After using this function, you must manually release the pointer returned to prevent memory leakage.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**Since**: 11

**Returns**:

| Type | Description |
| -- | -- |
| char* | Pointer to a new string that indicates the appID. If the returned object is NULL, the creation fails.      <br> The possible cause is that the application address space is full, causing space allocation to fail. |

### OH_NativeBundle_GetAppIdentifier()

```c
char* OH_NativeBundle_GetAppIdentifier()
```

**Description**

Obtains the appIdentifier of the current application. The appIdentifier does not change throughout the application lifecycle, including version updates, certificate changes, public and private key changes, and application migration. After using this function, you must manually release the pointer returned to prevent memory leakage.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**Since**: 11

**Returns**:

| Type | Description |
| -- | -- |
| char* | Pointer to a new string that indicates the appIdentifier. If the returned object is NULL, the creation      fails. The possible cause is that the application address space is full, causing space allocation to fail. |

### OH_NativeBundle_GetMainElementName()

```c
OH_NativeBundle_ElementName OH_NativeBundle_GetMainElementName()
```

**Description**

Obtains the mainElement information of the current application, including the bundle name, module name, and ability name. After using this function, you must manually release the pointer returned to prevent memory leakage.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**Since**: 13

**Returns**:

| Type | Description |
| -- | -- |
| [OH_NativeBundle_ElementName](capi-native-bundle-oh-nativebundle-elementname.md) | Pointer to the OH_NativeBundle_ElementName object. If the attribute of the returned object is NULL,      the creation fails. The possible cause is that the application address space is full, causing space      allocation to fail. |

### OH_NativeBundle_GetCompatibleDeviceType()

```c
char* OH_NativeBundle_GetCompatibleDeviceType()
```

**Description**

Obtains the compatible device type of the current application. It helps you optimize the layout and font size when distributing mobile applications to tablets or 2-in-1 devices. After using this function, you must manually release the pointer returned to prevent memory leakage.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**Since**: 14

**Returns**:

| Type | Description |
| -- | -- |
| char* | Pointer to a new string that indicates the compatible device type. If the returned object is NULL, the      creation fails.      <br> The possible cause is that the application address space is full, causing space allocation to fail. |

### OH_NativeBundle_IsDebugMode()

```c
bool OH_NativeBundle_IsDebugMode(bool* isDebugMode)
```

**Description**

Checks whether the current application is in debug mode.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| bool* isDebugMode | Pointer to the check result indicating whether the application is in debug mode. **true** if in debug mode, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Operation result. true if the call is successful, false otherwise. |

### OH_NativeBundle_GetModuleMetadata()

```c
OH_NativeBundle_ModuleMetadata* OH_NativeBundle_GetModuleMetadata(size_t* size)
```

**Description**

Obtains the module metadata array of the current application. After using this function, you must manually release the pointer returned to prevent memory leakage.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| size_t* size | Pointer to the size of the module metadata array. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_NativeBundle_ModuleMetadata*](capi-native-bundle-oh-nativebundle-modulemetadata.md) | An array of module metadata. If the returned object is NULL, the retrieval fails.      <br> The possible cause is that the application address space is full, causing space allocation to fail. |

### OH_NativeBundle_GetAbilityResourceInfo()

```c
BundleManager_ErrorCode OH_NativeBundle_GetAbilityResourceInfo(char* fileType, OH_NativeBundle_AbilityResourceInfo** abilityResourceInfo, size_t* size)
```

**Description**

Obtain a list of ability that support opening files in a certain format.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**Required permission**: ohos.permission.GET_ABILITY_INFO

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| char* fileType | Indicates the file type. |
| OH_NativeBundle_AbilityResourceInfo** abilityResourceInfo | Indicates the ability resource array. |
| size_t* size | Indicates the ability resource array size. |

**Returns**:

| Type | Description |
| -- | -- |
| BundleManager_ErrorCode | <ul><li>Returns [BUNDLE_MANAGER_ERROR_CODE_NO_ERROR](capi-bundle-manager-common-h.md#bundlemanager_errorcode) if the call is successful.</li><li>      Returns [BUNDLE_MANAGER_ERROR_CODE_PERMISSION_DENIED](capi-bundle-manager-common-h.md#bundlemanager_errorcode) if the caller has no correct permission.</li></ul> |


