# ability_resource_info.h

## Overview

The file declares the APIs for obtaining the following ability resource information: bundle name, module name, ability name, icon, clone index, and whether the application is a default application.

**Library**: libbundle_ndk.z.so

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**Since**: 21

**Related module**: [Native_Bundle](capi-native-bundle.md)

## Summary

### Struct

| Name | Description |
| -- | -- |
| [OH_NativeBundle_AbilityResourceInfo](capi-native-bundle-oh-nativebundle-abilityresourceinfo.md) | Represents the ability resource information, which is used to store and pass the basic configuration information of an ability, including attributes such as name and type. It is applicable to scenarios where the native layer queries and manages ability resources. |

### Function

| Name | Description |
| -- | -- |
| [BundleManager_ErrorCode OH_NativeBundle_GetBundleName(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, char** bundleName)](#oh_nativebundle_getbundlename) | Obtains the bundle name of the ability. After using this function, you must manually release the pointer returned to prevent memory leakage. |
| [BundleManager_ErrorCode OH_NativeBundle_GetModuleName(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, char** moduleName)](#oh_nativebundle_getmodulename) | Obtains the module name of the ability. After using this function, you must manually release the pointer returned to prevent memory leakage. |
| [BundleManager_ErrorCode OH_NativeBundle_GetAbilityName(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, char** abilityName)](#oh_nativebundle_getabilityname) | Obtains the ability name. After using this function, you must manually release the pointer returned to prevent memory leakage. |
| [BundleManager_ErrorCode OH_NativeBundle_GetLabel(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, char** label)](#oh_nativebundle_getlabel) | Obtains the application name of the ability. After using this function, you must manually release the pointerreturned to prevent memory leakage. |
| [BundleManager_ErrorCode OH_NativeBundle_GetAppIndex(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, int* appIndex)](#oh_nativebundle_getappindex) | Obtains the clone index of the ability. |
| [BundleManager_ErrorCode OH_NativeBundle_CheckDefaultApp(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, bool* isDefault)](#oh_nativebundle_checkdefaultapp) | Checks whether the application to which the ability belongs is a default application. |
| [BundleManager_ErrorCode OH_AbilityResourceInfo_Destroy(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, size_t count)](#oh_abilityresourceinfo_destroy) | Releases memory allocated for ability resource information. |
| [int OH_NativeBundle_GetSize()](#oh_nativebundle_getsize) | Obtains the size of a single [OH_NativeBundle_AbilityResourceInfo](capi-native-bundle-oh-nativebundle-abilityresourceinfo.md) struct. |
| [BundleManager_ErrorCode OH_NativeBundle_GetDrawableDescriptor(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, ArkUI_DrawableDescriptor** drawableIcon)
} // extern "C"](#oh_nativebundle_getdrawabledescriptor) | Obtains the DrawableDescriptor object of the ability icon resource. After using this function, you must manually release the pointer returned to prevent memory leakage. |

## Function description

### OH_NativeBundle_GetBundleName()

```c
BundleManager_ErrorCode OH_NativeBundle_GetBundleName(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, char** bundleName)
```

**Description**

Obtains the bundle name of the ability. After using this function, you must manually release the pointer returned to prevent memory leakage.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeBundle_AbilityResourceInfo](capi-native-bundle-oh-nativebundle-abilityresourceinfo.md)* abilityResourceInfo | [in] Pointer to the ability resource information. |
| char** bundleName | [in] Double pointer to the bundle name. |

**Returns**:

| Type | Description |
| -- | -- |
| [BundleManager_ErrorCode](capi-bundle-manager-common-h.md#bundlemanager_errorcode) | One of the following operation results: <ul><li>[BUNDLE_MANAGER_ERROR_CODE_NO_ERROR](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval is successful. </li><li>[BUNDLE_MANAGER_ERROR_CODE_PARAM_INVALID](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval fails because the **abilityResourceInfo** parameter is nullptr.</li></ul> |

### OH_NativeBundle_GetModuleName()

```c
BundleManager_ErrorCode OH_NativeBundle_GetModuleName(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, char** moduleName)
```

**Description**

Obtains the module name of the ability. After using this function, you must manually release the pointer returned to prevent memory leakage.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeBundle_AbilityResourceInfo](capi-native-bundle-oh-nativebundle-abilityresourceinfo.md)* abilityResourceInfo | [in] Pointer to the ability resource information. |
| char** moduleName | [in] Double pointer to the module name. |

**Returns**:

| Type | Description |
| -- | -- |
| [BundleManager_ErrorCode](capi-bundle-manager-common-h.md#bundlemanager_errorcode) | One of the following operation results: <ul><li>[BUNDLE_MANAGER_ERROR_CODE_NO_ERROR](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval is successful. </li><li>[BUNDLE_MANAGER_ERROR_CODE_PARAM_INVALID](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval fails because the **abilityResourceInfo** parameter is nullptr.</li></ul> |

### OH_NativeBundle_GetAbilityName()

```c
BundleManager_ErrorCode OH_NativeBundle_GetAbilityName(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, char** abilityName)
```

**Description**

Obtains the ability name. After using this function, you must manually release the pointer returned to prevent memory leakage.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeBundle_AbilityResourceInfo](capi-native-bundle-oh-nativebundle-abilityresourceinfo.md)* abilityResourceInfo | [in] Pointer to the ability resource information. |
| char** abilityName | [in] Double pointer to the ability name. |

**Returns**:

| Type | Description |
| -- | -- |
| [BundleManager_ErrorCode](capi-bundle-manager-common-h.md#bundlemanager_errorcode) | One of the following operation results: <ul><li>[BUNDLE_MANAGER_ERROR_CODE_NO_ERROR](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval is successful. </li><li>[BUNDLE_MANAGER_ERROR_CODE_PARAM_INVALID](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval fails because the **abilityResourceInfo** parameter is nullptr.</li></ul> |

### OH_NativeBundle_GetLabel()

```c
BundleManager_ErrorCode OH_NativeBundle_GetLabel(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, char** label)
```

**Description**

Obtains the application name of the ability. After using this function, you must manually release the pointerreturned to prevent memory leakage.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeBundle_AbilityResourceInfo](capi-native-bundle-oh-nativebundle-abilityresourceinfo.md)* abilityResourceInfo | [in] Pointer to the ability resource information. |
| char** label | [in] Double pointer to the application name. |

**Returns**:

| Type | Description |
| -- | -- |
| [BundleManager_ErrorCode](capi-bundle-manager-common-h.md#bundlemanager_errorcode) | One of the following operation results: <ul><li>[BUNDLE_MANAGER_ERROR_CODE_NO_ERROR](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval is successful. </li><li>[BUNDLE_MANAGER_ERROR_CODE_PARAM_INVALID](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval fails because the **abilityResourceInfo** parameter is nullptr.</li></ul> |

### OH_NativeBundle_GetAppIndex()

```c
BundleManager_ErrorCode OH_NativeBundle_GetAppIndex(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, int* appIndex)
```

**Description**

Obtains the clone index of the ability.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeBundle_AbilityResourceInfo](capi-native-bundle-oh-nativebundle-abilityresourceinfo.md)* abilityResourceInfo | [in] Pointer to the ability resource information. |
| int* appIndex | [in] Pointer to the clone index. |

**Returns**:

| Type | Description |
| -- | -- |
| [BundleManager_ErrorCode](capi-bundle-manager-common-h.md#bundlemanager_errorcode) | One of the following operation results: <ul><li>[BUNDLE_MANAGER_ERROR_CODE_NO_ERROR](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval is successful. </li><li>[BUNDLE_MANAGER_ERROR_CODE_PARAM_INVALID](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval fails because the ** abilityResourceInfo** parameter is nullptr.</li></ul> |

### OH_NativeBundle_CheckDefaultApp()

```c
BundleManager_ErrorCode OH_NativeBundle_CheckDefaultApp(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, bool* isDefault)
```

**Description**

Checks whether the application to which the ability belongs is a default application.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeBundle_AbilityResourceInfo](capi-native-bundle-oh-nativebundle-abilityresourceinfo.md)* abilityResourceInfo | [in] Pointer to the ability resource information. |
| bool* isDefault | [in] Pointer to the check result for whether the application is a default application. A default application is the preferred application set by the user for a specific file type or operation. **true** if the application is a default application, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| [BundleManager_ErrorCode](capi-bundle-manager-common-h.md#bundlemanager_errorcode) | One of the following operation results: <ul><li>[BUNDLE_MANAGER_ERROR_CODE_NO_ERROR](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The query is successful. </li><li>[BUNDLE_MANAGER_ERROR_CODE_PARAM_INVALID](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The query fails because the abilityResourceInfo parameter is nullptr.</li></ul> |

### OH_AbilityResourceInfo_Destroy()

```c
BundleManager_ErrorCode OH_AbilityResourceInfo_Destroy(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, size_t count)
```

**Description**

Releases memory allocated for ability resource information.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeBundle_AbilityResourceInfo](capi-native-bundle-oh-nativebundle-abilityresourceinfo.md)* abilityResourceInfo | [in] Pointer to the ability resource information. |
| size_t count | [in] Size of the ability resource information array. |

**Returns**:

| Type | Description |
| -- | -- |
| [BundleManager_ErrorCode](capi-bundle-manager-common-h.md#bundlemanager_errorcode) | One of the following operation results: <ul><li>[BUNDLE_MANAGER_ERROR_CODE_NO_ERROR](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The release is successful. </li><li>[BUNDLE_MANAGER_ERROR_CODE_PARAM_INVALID](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The release fails because the **abilityResourceInfo** parameter is nullptr.</li></ul> |

### OH_NativeBundle_GetSize()

```c
int OH_NativeBundle_GetSize()
```

**Description**

Obtains the size of a single [OH_NativeBundle_AbilityResourceInfo](capi-native-bundle-oh-nativebundle-abilityresourceinfo.md) struct.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**Since**: 21

**Returns**:

| Type | Description |
| -- | -- |
| int | Size of a single [OH_NativeBundle_AbilityResourceInfo](capi-native-bundle-oh-nativebundle-abilityresourceinfo.md) struct. |

### OH_NativeBundle_GetDrawableDescriptor()

```c
BundleManager_ErrorCode OH_NativeBundle_GetDrawableDescriptor(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, ArkUI_DrawableDescriptor** drawableIcon)
} // extern "C"
```

**Description**

Obtains the DrawableDescriptor object of the ability icon resource. After using this function, you must manually release the pointer returned to prevent memory leakage.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeBundle_AbilityResourceInfo](capi-native-bundle-oh-nativebundle-abilityresourceinfo.md)* abilityResourceInfo | [in] Pointer to the ability resource information. |
| drawableIcon | [in] Double pointer to the DrawableDescriptor object. |

**Returns**:

| Type | Description |
| -- | -- |
| [BundleManager_ErrorCode](capi-bundle-manager-common-h.md#bundlemanager_errorcode) | One of the following operation results: <ul><li>[BUNDLE_MANAGER_ERROR_CODE_NO_ERROR](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval is successful. </li><li>[BUNDLE_MANAGER_ERROR_CODE_PARAM_INVALID](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval fails because the **abilityResourceInfo** parameter is nullptr.</li></ul> |


