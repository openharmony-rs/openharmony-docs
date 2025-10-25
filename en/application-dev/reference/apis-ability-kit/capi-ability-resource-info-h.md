# ability_resource_info.h
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

The file declares the APIs for obtaining the following ability resource information: bundle name, module name, ability name, icon, clone index, and whether the application is a default application.

**File to include**: <bundle/ability_resource_info.h>

**Library**: libbundle_ndk.z.so

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**Since**: 21

**Related module**: [Native_Bundle](capi-native-bundle.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_NativeBundle_AbilityResourceInfo](capi-native-bundle-oh-nativebundle-abilityresourceinfo.md) | OH_NativeBundle_AbilityResourceInfo | Describes the ability resource information.|

### Functions

| Name| Description|
| -- | -- |
| [BundleManager_ErrorCode OH_NativeBundle_GetBundleName(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, char** bundleName)](#oh_nativebundle_getbundlename) | Obtains the bundle name of the ability. After using this function, you must manually release the pointer returned to prevent memory leakage.|
| [BundleManager_ErrorCode OH_NativeBundle_GetModuleName(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, char** moduleName)](#oh_nativebundle_getmodulename) | Obtains the module name of the ability. After using this function, you must manually release the pointer returned to prevent memory leakage.|
| [BundleManager_ErrorCode OH_NativeBundle_GetAbilityName(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, char** abilityName)](#oh_nativebundle_getabilityname) | Obtains the ability name. After using this function, you must manually release the pointer returned to prevent memory leakage.|
| [BundleManager_ErrorCode OH_NativeBundle_GetDrawableDescriptor(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, ArkUI_DrawableDescriptor** drawableIcon)](#oh_nativebundle_getdrawabledescriptor) | Obtains the [DrawableDescriptor](../apis-arkui/capi-arkui-nativemodule-arkui-drawabledescriptor.md) object of the ability icon resource. After using this function, you must manually call [OH_AbilityResourceInfo_Destroy](#oh_abilityresourceinfo_destroy) to release the pointer returned to prevent memory leakage.|
| [BundleManager_ErrorCode OH_NativeBundle_GetLabel(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, char** label)](#oh_nativebundle_getlabel) | Obtains the application name of the ability. After using this function, you must manually release the pointer returned to prevent memory leakage.|
| [BundleManager_ErrorCode OH_NativeBundle_GetAppIndex(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, int* appIndex)](#oh_nativebundle_getappindex) | Obtains the clone index of the ability.|
| [BundleManager_ErrorCode OH_NativeBundle_CheckDefaultApp(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, bool* isDefault)](#oh_nativebundle_checkdefaultapp) | Checks whether the application to which the ability belongs is a default application.|
| [BundleManager_ErrorCode OH_AbilityResourceInfo_Destroy(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, size_t count)](#oh_abilityresourceinfo_destroy) | Releases memory allocated for ability resource information.|
| [int OH_NativeBundle_GetSize()](#oh_nativebundle_getsize) | Obtains the size of a single [OH_NativeBundle_AbilityResourceInfo](capi-native-bundle-oh-nativebundle-abilityresourceinfo.md) struct.|

## Function Description

### OH_NativeBundle_GetBundleName()

```
BundleManager_ErrorCode OH_NativeBundle_GetBundleName(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, char** bundleName)
```

**Description**

Obtains the bundle name of the ability. After using this function, you must manually release the pointer returned to prevent memory leakage.

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo | Pointer to the ability resource information.|
| char** bundleName | Double pointer to the bundle name.|

**Returns**

| Type| Description|
| -- | -- |
| [BundleManager_ErrorCode](capi-bundle-manager-common-h.md#bundlemanager_errorcode) | One of the following operation results:<br>         [BUNDLE_MANAGER_ERROR_CODE_NO_ERROR](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval is successful.<br>         [BUNDLE_MANAGER_ERROR_CODE_PARAM_INVALID](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval fails because the **abilityResourceInfo** parameter is nullptr.|

### OH_NativeBundle_GetModuleName()

```
BundleManager_ErrorCode OH_NativeBundle_GetModuleName(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, char** moduleName)
```

**Description**

Obtains the module name of the ability. After using this function, you must manually release the pointer returned to prevent memory leakage.

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo | Pointer to the ability resource information.|
| char** moduleName | Double pointer to the module name.|

**Returns**

| Type| Description|
| -- | -- |
| [BundleManager_ErrorCode](capi-bundle-manager-common-h.md#bundlemanager_errorcode) | One of the following operation results:<br>         [BUNDLE_MANAGER_ERROR_CODE_NO_ERROR](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval is successful.<br>         [BUNDLE_MANAGER_ERROR_CODE_PARAM_INVALID](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval fails because the **abilityResourceInfo** parameter is nullptr.|

### OH_NativeBundle_GetAbilityName()

```
BundleManager_ErrorCode OH_NativeBundle_GetAbilityName(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, char** abilityName)
```

**Description**

Obtains the ability name. After using this function, you must manually release the pointer returned to prevent memory leakage.

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo | Pointer to the ability resource information.|
| char** abilityName | Double pointer to the ability name.|

**Returns**

| Type| Description|
| -- | -- |
| [BundleManager_ErrorCode](capi-bundle-manager-common-h.md#bundlemanager_errorcode) | One of the following operation results:<br>         [BUNDLE_MANAGER_ERROR_CODE_NO_ERROR](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval is successful.<br>         [BUNDLE_MANAGER_ERROR_CODE_PARAM_INVALID](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval fails because the **abilityResourceInfo** parameter is nullptr.|

### OH_NativeBundle_GetDrawableDescriptor()

```
BundleManager_ErrorCode OH_NativeBundle_GetDrawableDescriptor(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, ArkUI_DrawableDescriptor** drawableIcon)
```

**Description**

Obtains the [DrawableDescriptor](../apis-arkui/capi-arkui-nativemodule-arkui-drawabledescriptor.md) object of the ability icon resource. After using this function, you must manually call [OH_AbilityResourceInfo_Destroy](#oh_abilityresourceinfo_destroy) to release the pointer returned to prevent memory leakage.

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo | Pointer to the ability resource information.|
| ArkUI_DrawableDescriptor** drawableIcon | Double pointer to the [DrawableDescriptor](../apis-arkui/capi-arkui-nativemodule-arkui-drawabledescriptor.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| [BundleManager_ErrorCode](capi-bundle-manager-common-h.md#bundlemanager_errorcode) | One of the following operation results:<br>         [BUNDLE_MANAGER_ERROR_CODE_NO_ERROR](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval is successful.<br>         [BUNDLE_MANAGER_ERROR_CODE_PARAM_INVALID](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval fails because the **abilityResourceInfo** parameter is nullptr.|

### OH_NativeBundle_GetLabel()

```
BundleManager_ErrorCode OH_NativeBundle_GetLabel(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, char** label)
```

**Description**

Obtains the application name of the ability. After using this function, you must manually release the pointer returned to prevent memory leakage.

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo |  Pointer to the ability resource information.|
| char** label | Double pointer to the application name.|

**Returns**

| Type| Description|
| -- | -- |
| [BundleManager_ErrorCode](capi-bundle-manager-common-h.md#bundlemanager_errorcode) | One of the following operation results:<br>         [BUNDLE_MANAGER_ERROR_CODE_NO_ERROR](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval is successful.<br>         [BUNDLE_MANAGER_ERROR_CODE_PARAM_INVALID](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval fails because the **abilityResourceInfo** parameter is nullptr.|

### OH_NativeBundle_GetAppIndex()

```
BundleManager_ErrorCode OH_NativeBundle_GetAppIndex(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, int* appIndex)
```

**Description**

Obtains the clone index of the ability.

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo | Pointer to the ability resource information.|
| int* appIndex | Double pointer to the clone index.|

**Returns**

| Type| Description|
| -- | -- |
| [BundleManager_ErrorCode](capi-bundle-manager-common-h.md#bundlemanager_errorcode) | One of the following operation results:<br>         [BUNDLE_MANAGER_ERROR_CODE_NO_ERROR](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval is successful.<br>         [BUNDLE_MANAGER_ERROR_CODE_PARAM_INVALID](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The retrieval fails because the **abilityResourceInfo** parameter is nullptr.|

### OH_NativeBundle_CheckDefaultApp()

```
BundleManager_ErrorCode OH_NativeBundle_CheckDefaultApp(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, bool* isDefault)
```

**Description**

Checks whether the application to which the ability belongs is a default application.

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo | Pointer to the ability resource information.|
| bool* isDefault | Pointer to the check result for whether the application is a default application. A default application is the preferred application set by the user for a specific file type or operation. **true** if the application is a default application, **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| [BundleManager_ErrorCode](capi-bundle-manager-common-h.md#bundlemanager_errorcode) | One of the following operation results:<br>         [BUNDLE_MANAGER_ERROR_CODE_NO_ERROR](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The query is successful.<br>         [BUNDLE_MANAGER_ERROR_CODE_PARAM_INVALID](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The query fails because the **abilityResourceInfo** parameter is nullptr.|

### OH_AbilityResourceInfo_Destroy()

```
BundleManager_ErrorCode OH_AbilityResourceInfo_Destroy(OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo, size_t count)
```

**Description**

Releases memory allocated for ability resource information.

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| OH_NativeBundle_AbilityResourceInfo* abilityResourceInfo | Pointer to the ability resource information.|
| size_t count | Size of the ability resource information array.|

**Returns**

| Type| Description|
| -- | -- |
| [BundleManager_ErrorCode](capi-bundle-manager-common-h.md#bundlemanager_errorcode) | One of the following operation results:<br>         [BUNDLE_MANAGER_ERROR_CODE_NO_ERROR](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The release is successful.<br>         [BUNDLE_MANAGER_ERROR_CODE_PARAM_INVALID](capi-bundle-manager-common-h.md#bundlemanager_errorcode): The release fails because the **abilityResourceInfo** parameter is nullptr.|

### OH_NativeBundle_GetSize()

```
int OH_NativeBundle_GetSize()
```

**Description**

Obtains the size of a single [OH_NativeBundle_AbilityResourceInfo](capi-native-bundle-oh-nativebundle-abilityresourceinfo.md) struct.

**Since**: 21

**Returns**

| Type| Description|
| -- | -- |
| int | Size of a single [OH_NativeBundle_AbilityResourceInfo](capi-native-bundle-oh-nativebundle-abilityresourceinfo.md) struct.|
