# ohresmgr.h

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=d1ed4ce8d034cfba750330bf06dcd3a9995f70ce translatedAt=2026-11-04T04:03:55.964Z pushedAt=2026-11-04T10:13:14.914Z nl=1 -->

## Overview

Provides the capability of obtaining resources at the native layer of resource management.

**File to include**: <resourcemanager/ohresmgr.h>

**Library**: libohresmgr.so

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 12

**Related module**: [resourcemanager](capi-resourcemanager.md)

## Summary

### Callback

| Name| Description|
| -- | -- |
| [ResourceManager_ErrorCode OH_ResourceManager_GetMediaBase64(const NativeResourceManager *mgr, uint32_t resId, char **resultValue, uint64_t *resultLen, uint32_t density = 0)](#oh_resourcemanager_getmediabase64) | Obtains the Base64-encoded string of the corresponding media resource by specifying the resource ID and screen density. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetMediaBase64Data(const NativeResourceManager *mgr, uint32_t resId, char **resultValue, uint64_t *resultLen, uint32_t density)](#oh_resourcemanager_getmediabase64data) | Obtains the Base64-encoded string of the corresponding media resource by specifying the resource ID and screen density. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetMediaBase64ByName(const NativeResourceManager *mgr, const char *resName, char **resultValue, uint64_t *resultLen, uint32_t density = 0)](#oh_resourcemanager_getmediabase64byname) | Obtains the Base64-encoded string of the corresponding media resource by specifying the resource name and screen density. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetMediaBase64DataByName(const NativeResourceManager *mgr, const char *resName, char **resultValue, uint64_t *resultLen, uint32_t density)](#oh_resourcemanager_getmediabase64databyname) | Obtains the Base64-encoded string of the corresponding media resource by specifying the resource name and screen density. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetMedia(const NativeResourceManager *mgr, uint32_t resId, uint8_t **resultValue, uint64_t *resultLen, uint32_t density = 0)](#oh_resourcemanager_getmedia) | Obtains the binary data of the corresponding media resource by specifying the resource ID and screen density. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetMediaData(const NativeResourceManager *mgr, uint32_t resId, uint8_t **resultValue, uint64_t *resultLen, uint32_t density)](#oh_resourcemanager_getmediadata) | Obtains the binary data of the corresponding media resource by specifying the resource ID and screen density. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetMediaByName(const NativeResourceManager *mgr, const char *resName, uint8_t **resultValue, uint64_t *resultLen, uint32_t density = 0)](#oh_resourcemanager_getmediabyname) | Obtains the binary data of the corresponding media resource by specifying the resource name and screen density. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetMediaDataByName(const NativeResourceManager *mgr, const char *resName, uint8_t **resultValue, uint64_t *resultLen, uint32_t density)](#oh_resourcemanager_getmediadatabyname) | Obtains the binary data of the corresponding media resource by specifying the resource name and screen density. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetDrawableDescriptor(const NativeResourceManager *mgr, uint32_t resId, ArkUI_DrawableDescriptor **drawableDescriptor, uint32_t density = 0, uint32_t type = 0)](#oh_resourcemanager_getdrawabledescriptor) | Obtains the DrawableDescriptor object corresponding to the icon resource by specifying the resource ID, screen density, and icon type. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetDrawableDescriptorData(const NativeResourceManager *mgr, uint32_t resId, ArkUI_DrawableDescriptor **drawableDescriptor, uint32_t density, uint32_t type)](#oh_resourcemanager_getdrawabledescriptordata) | Obtains the DrawableDescriptor object corresponding to the icon resource by specifying the resource ID, screen density, and icon type. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetDrawableDescriptorByName(const NativeResourceManager *mgr, const char *resName, ArkUI_DrawableDescriptor **drawableDescriptor, uint32_t density = 0, uint32_t type = 0)](#oh_resourcemanager_getdrawabledescriptorbyname) | Obtains the DrawableDescriptor object corresponding to the icon resource by specifying the resource name, screen density, and icon type. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetDrawableDescriptorDataByName(const NativeResourceManager *mgr, const char *resName, ArkUI_DrawableDescriptor **drawableDescriptor, uint32_t density, uint32_t type)](#oh_resourcemanager_getdrawabledescriptordatabyname) | Obtains the DrawableDescriptor object corresponding to the icon resource by specifying the resource name and screen density. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetSymbol(const NativeResourceManager *mgr, uint32_t resId, uint32_t *resultValue)](#oh_resourcemanager_getsymbol) | Obtains the Unicode encoding of the Symbol icon corresponding to the specified resource ID. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetSymbolByName(const NativeResourceManager *mgr, const char *resName, uint32_t *resultValue)](#oh_resourcemanager_getsymbolbyname) | Obtains the Unicode encoding of the Symbol icon corresponding to the specified resource name. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetLocales(const NativeResourceManager *mgr, char ***resultValue, uint32_t *resultLen, bool includeSystem = false)](#oh_resourcemanager_getlocales) | Obtains the list of languages supported by the application. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetLocalesData(const NativeResourceManager *mgr, char ***resultValue, uint32_t *resultLen, bool includeSystem)](#oh_resourcemanager_getlocalesdata) | Obtains the list of languages supported by the application. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetConfiguration(const NativeResourceManager *mgr, ResourceManager_Configuration *configuration)](#oh_resourcemanager_getconfiguration) | Obtains the configuration information of the device, such as screen orientation, language region, device type, screen density, and color mode. (Deprecated since API 20) |
| [ResourceManager_ErrorCode OH_ResourceManager_GetResourceConfiguration(const NativeResourceManager *mgr, ResourceManager_Configuration *configuration)](#oh_resourcemanager_getresourceconfiguration) | Obtains the configuration information of the device, such as screen orientation, language region, device type, screen density, and color mode. |
| [ResourceManager_ErrorCode OH_ResourceManager_ReleaseConfiguration(ResourceManager_Configuration *configuration)](#oh_resourcemanager_releaseconfiguration) | Releases the memory allocated by [OH_ResourceManager_GetConfiguration](capi-ohresmgr-h.md#oh_resourcemanager_getconfiguration) or [OH_ResourceManager_GetResourceConfiguration](capi-ohresmgr-h.md#oh_resourcemanager_getresourceconfiguration). |
| [ResourceManager_ErrorCode OH_ResourceManager_GetString(const NativeResourceManager *mgr, uint32_t resId, char **resultValue, ...)](#oh_resourcemanager_getstring) | Obtains the plain string or format string corresponding to the specified resource ID. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetStringByName(const NativeResourceManager *mgr, const char *resName, char **resultValue, ...)](#oh_resourcemanager_getstringbyname) | Obtains the plain string or format string corresponding to the specified resource name. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetStringArray(const NativeResourceManager *mgr, uint32_t resId, char ***resultValue, uint32_t *resultLen)](#oh_resourcemanager_getstringarray) | Obtains the string array corresponding to the specified resource ID. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetStringArrayByName(const NativeResourceManager *mgr, const char *resName, char ***resultValue, uint32_t *resultLen)](#oh_resourcemanager_getstringarraybyname) | Obtains the string array corresponding to the specified resource name. |
| [ResourceManager_ErrorCode OH_ResourceManager_ReleaseStringArray(char ***resValue, uint32_t len)](#oh_resourcemanager_releasestringarray) | Releases the memory of the string array.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetPluralString(const NativeResourceManager *mgr, uint32_t resId, uint32_t num, char **resultValue)](#oh_resourcemanager_getpluralstring) | Obtains the plural string corresponding to the specified resource ID.<br> In the Chinese environment, the string does not distinguish singular and plural; in other languages, the string distinguishes singular and plural. For specific rules, see [language plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In English, German and other languages, plural types include cardinal (such as 1, 2, 3) and ordinal (such as 1st, 2nd, 3rd). This function only supports cardinal numeral types. (Deprecated since API 16) |
| [ResourceManager_ErrorCode OH_ResourceManager_GetPluralStringByName(const NativeResourceManager *mgr, const char *resName, uint32_t num, char **resultValue)](#oh_resourcemanager_getpluralstringbyname) | Obtains the plural string corresponding to the specified resource name.<br> In the Chinese environment, the string does not distinguish singular and plural; in other languages, the string distinguishes singular and plural. For specific rules, see [language plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In English, German and other languages, plural types include cardinal (such as 1, 2, 3) and ordinal (such as 1st, 2nd, 3rd). This function only supports cardinal numeral types. (Deprecated since API 16) |
| [ResourceManager_ErrorCode OH_ResourceManager_GetIntPluralString(const NativeResourceManager *mgr, uint32_t resId, uint32_t num, char **resultValue, ...)](#oh_resourcemanager_getintpluralstring) | Obtains the corresponding plural string and formats it by specifying the resource ID, integer quantity value, and variable arguments.<br> In the Chinese environment, the string does not distinguish singular and plural; in other languages, the string distinguishes singular and plural. For specific rules, see [language plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In English, German and other languages, plural types include cardinal (such as 1, 2, 3) and ordinal (such as 1st, 2nd, 3rd). This function only supports cardinal numeral types. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetIntPluralStringByName(const NativeResourceManager *mgr, const char *resName, uint32_t num, char **resultValue, ...)](#oh_resourcemanager_getintpluralstringbyname) | Obtains the corresponding plural string and formats it by specifying the resource name, integer quantity value, and variable arguments.<br> In the Chinese environment, the string does not distinguish singular and plural; in other languages, the string distinguishes singular and plural. For specific rules, see [language plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In English, German and other languages, plural types include cardinal (such as 1, 2, 3) and ordinal (such as 1st, 2nd, 3rd). This function only supports cardinal numeral types. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetDoublePluralString(const NativeResourceManager *mgr, uint32_t resId, double num, char **resultValue, ...)](#oh_resourcemanager_getdoublepluralstring) | Obtains the corresponding plural string and formats it by specifying the resource ID, floating-point number quantity value, and variable arguments.<br> In the Chinese environment, the string does not distinguish singular and plural; in other languages, the string distinguishes singular and plural. For specific rules, see [language plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In English, German and other languages, plural types include cardinal (such as 1, 2, 3) and ordinal (such as 1st, 2nd, 3rd). This function only supports cardinal numeral types. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetDoublePluralStringByName(const NativeResourceManager *mgr, const char *resName, double num, char **resultValue, ...)](#oh_resourcemanager_getdoublepluralstringbyname) | Obtains the corresponding plural string and formats it by specifying the resource name, floating-point number quantity value, and variable arguments.<br> In the Chinese environment, the string does not distinguish singular and plural; in other languages, the string distinguishes singular and plural. For specific rules, see [language plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In English, German and other languages, plural types include cardinal (such as 1, 2, 3) and ordinal (such as 1st, 2nd, 3rd). This function only supports cardinal numeral types. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetColor(const NativeResourceManager *mgr, uint32_t resId, uint32_t *resultValue)](#oh_resourcemanager_getcolor) | Obtains the color resource value corresponding to the specified resource ID. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetColorByName(const NativeResourceManager *mgr, const char *resName, uint32_t *resultValue)](#oh_resourcemanager_getcolorbyname) | Obtains the color resource value corresponding to the specified resource name. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetInt(const NativeResourceManager *mgr, uint32_t resId, int *resultValue)](#oh_resourcemanager_getint) | Obtains the integer resource value corresponding to the specified resource ID. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetIntByName(const NativeResourceManager *mgr, const char *resName, int *resultValue)](#oh_resourcemanager_getintbyname) | Obtains the integer resource value corresponding to the specified resource name. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetFloat(const NativeResourceManager *mgr, uint32_t resId, float *resultValue)](#oh_resourcemanager_getfloat) | Obtains the floating-point resource value corresponding to the specified resource ID. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetFloatByName(const NativeResourceManager *mgr, const char *resName, float *resultValue)](#oh_resourcemanager_getfloatbyname) | Obtains the floating-point resource value corresponding to the specified resource name. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetBool(const NativeResourceManager *mgr, uint32_t resId, bool *resultValue)](#oh_resourcemanager_getbool) | Obtains the boolean resource value corresponding to the specified resource ID. |
| [ResourceManager_ErrorCode OH_ResourceManager_GetBoolByName(const NativeResourceManager *mgr, const char *resName, bool *resultValue)](#oh_resourcemanager_getboolbyname) | Obtains the boolean resource value corresponding to the specified resource name. |
| [ResourceManager_ErrorCode OH_ResourceManager_AddResource(const NativeResourceManager *mgr, const char *path)](#oh_resourcemanager_addresource) | Dynamically loads overlay resources at application runtime to implement theme switching or resource overriding. |
| [ResourceManager_ErrorCode OH_ResourceManager_RemoveResource(const NativeResourceManager *mgr, const char *path)](#oh_resourcemanager_removeresource) | Removes the specified overlay resources at application runtime and restores the resources before being overridden. |

## Function Description

### OH_ResourceManager_GetMediaBase64()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetMediaBase64(const NativeResourceManager *mgr, uint32_t resId, char **resultValue, uint64_t *resultLen, uint32_t density = 0)
```

**Description**

Gets the Base64-encoded string of the corresponding media resource by specifying the resource ID and screen density.

**Since**: 12

**Parameters**

| Name| Description|
| -- |--|
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| uint32_t resId | Input parameter. Resource ID. |
| char **resultValue | Output parameter. Pointer to the Base64-encoded string, which is allocated by malloc() and must be released by free() after use. |
| uint64_t *resultLen | Output parameter. Length of the Base64 string, in bytes. |
| density | Input parameter, optional. Screen density. For the value range, see [ScreenDensity](capi-resmgr-common-h.md#resourcemanager_devicetype). The default value is 0, which indicates the current system screen density. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_RES_ID_NOT_FOUND if the resource ID is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_ID if no matching resource is found by the resource ID.<br>     Returns ERROR_CODE_OUT_OF_MEMORY if memory overflow occurs. |

### OH_ResourceManager_GetMediaBase64Data()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetMediaBase64Data(const NativeResourceManager *mgr, uint32_t resId, char **resultValue, uint64_t *resultLen, uint32_t density)
```

**Description**

Gets the Base64-encoded string of the corresponding media resource by specifying the resource ID and screen density.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| uint32_t resId | Input parameter. Resource ID. |
| char **resultValue | Output parameter. Pointer to the Base64-encoded string, which is allocated by malloc() and must be released by free() after use. |
| uint64_t *resultLen | Output parameter. Length of the Base64 string, in bytes. |
| uint32_t density | Input parameter. Screen density. For the value range, see [ScreenDensity](capi-resmgr-common-h.md#resourcemanager_devicetype). The value 0 indicates the current system screen density. If no specific density is required, set this parameter to 0. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_RES_ID_NOT_FOUND if the resource ID is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_ID if no matching resource is found based on the resource ID.<br>     Returns ERROR_CODE_OUT_OF_MEMORY if memory overflow occurs. |

### OH_ResourceManager_GetMediaBase64ByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetMediaBase64ByName(const NativeResourceManager *mgr, const char *resName, char **resultValue, uint64_t *resultLen, uint32_t density = 0)
```

**Description**

Gets the Base64-encoded string of the corresponding media resource by specifying the resource name and screen density.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| const char *resName | Input parameter. Resource name. |
| char **resultValue | Output parameter. Pointer to the Base64-encoded string, allocated by malloc() and must be released by free() after use. |
| uint64_t *resultLen | Output parameter. Length of the Base64 string, in bytes. |
| density | Input parameter, optional. Screen density. For the value range, see [ScreenDensity](capi-resmgr-common-h.md#screendensity). The default value is **0**, which indicates the current system screen density. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_RES_NAME_NOT_FOUND if the resource name is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_NAME if no matching resource is found by the resource name.<br>     Returns ERROR_CODE_OUT_OF_MEMORY if memory overflow occurs. |

### OH_ResourceManager_GetMediaBase64DataByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetMediaBase64DataByName(const NativeResourceManager *mgr, const char *resName, char **resultValue, uint64_t *resultLen, uint32_t density)
```

**Description**

Gets the Base64-encoded string of the corresponding media resource by specifying the resource name and screen density.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| const char *resName | Input parameter. Resource name. |
| char **resultValue | Output parameter. Pointer to the Base64-encoded string, which is allocated by malloc() and must be released by free() after use. |
| uint64_t *resultLen | Output parameter. Length of the Base64 string, in bytes. |
| uint32_t density | Input parameter. Screen density. For the value range, see [ScreenDensity](capi-resmgr-common-h.md#resourcemanager_devicetype). The value 0 indicates that the current system screen density is used. If a specific density is not required, set this parameter to 0. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification failed.<br>     Returns ERROR_CODE_RES_NAME_NOT_FOUND if the resource name is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_NAME if no matching resource is found by the resource name.<br>     Returns ERROR_CODE_OUT_OF_MEMORY if the memory is insufficient. |

### OH_ResourceManager_GetMedia()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetMedia(const NativeResourceManager *mgr, uint32_t resId, uint8_t **resultValue, uint64_t *resultLen, uint32_t density = 0)
```

**Description**

Gets the binary data of the corresponding media resource by specifying the resource ID and screen density.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| uint32_t resId | Input parameter. Resource ID. |
| uint8_t **resultValue | Output parameter. Pointer to the media data. The memory is allocated by malloc() and must be released by free() after use. |
| uint64_t *resultLen | Output parameter. Length of the returned data, in bytes. |
| density | Input parameter, optional. Screen density. For the value range, see [ScreenDensity](capi-resmgr-common-h.md#screendensity). The default value is 0, which indicates the current system screen density. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. Incorrect parameter type; 2. Parameter verification failed.<br>     Returns ERROR_CODE_RES_ID_NOT_FOUND if the resource ID is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_ID if no matching resource is found by the resource ID.<br>     Returns ERROR_CODE_OUT_OF_MEMORY if the memory is exhausted. |

### OH_ResourceManager_GetMediaData()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetMediaData(const NativeResourceManager *mgr, uint32_t resId, uint8_t **resultValue, uint64_t *resultLen, uint32_t density)
```

**Description**

Gets the binary data of the corresponding media resource by specifying the resource ID and screen density.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| uint32_t resId | Input parameter. Resource ID. |
| uint8_t **resultValue | Output parameter. Pointer to the returned media data. The memory is allocated by malloc() and must be released by free() after use. |
| uint64_t *resultLen | Output parameter. Length of the returned data, in bytes. |
| uint32_t density | Input parameter. Screen density. For the value range, see [ScreenDensity](capi-resmgr-common-h.md#screendensity). The value 0 indicates the current system screen density. If no specific density is required, set this parameter to 0. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter validation fails.<br>     Returns ERROR_CODE_RES_ID_NOT_FOUND if the resource ID is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_ID if no matching resource is found by the resource ID.<br>     Returns ERROR_CODE_OUT_OF_MEMORY if the memory is insufficient. |

### OH_ResourceManager_GetMediaByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetMediaByName(const NativeResourceManager *mgr, const char *resName, uint8_t **resultValue, uint64_t *resultLen, uint32_t density = 0)
```

**Description**

Gets the binary data of the corresponding media resource by specifying the resource name and screen density.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| const char *resName | Input parameter. Resource name. |
| uint8_t **resultValue | Output parameter. Pointer to the returned media data. The memory is allocated by malloc() and must be released by free() after use. |
| uint64_t *resultLen | Output parameter. Length of the returned data, in bytes. |
| density | Input parameter, optional. Screen density. For the value range, see [ScreenDensity](capi-resmgr-common-h.md#screendensity). The default value is 0, which indicates the current system screen density. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. incorrect parameter type; 2. parameter verification failed.<br>     Returns ERROR_CODE_RES_NAME_NOT_FOUND if the resource name is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_NAME if no matching resource is found by the resource name.<br>     Returns ERROR_CODE_OUT_OF_MEMORY if memory overflow occurs. |

### OH_ResourceManager_GetMediaDataByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetMediaDataByName(const NativeResourceManager *mgr, const char *resName, uint8_t **resultValue, uint64_t *resultLen, uint32_t density)
```

**Description**

Gets the binary data of the corresponding media resource by specifying the resource name and screen density.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| const char *resName | Input parameter. Resource name. |
| uint8_t **resultValue | Output parameter. Pointer to the returned media data. The memory is allocated by malloc() and must be released by free() after use. |
| uint64_t *resultLen | Output parameter. Length of the returned data, in bytes. |
| uint32_t density | Input parameter. Screen density. For the value range, see ScreenDensity](capi-resmgr-common-h.md#screendensity. The value **0** indicates the current system screen density. If no specific density is required, set this parameter to 0. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_RES_NAME_NOT_FOUND if the resource name is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_NAME if no matching resource is found by the resource name.<br>     Returns ERROR_CODE_OUT_OF_MEMORY if memory overflow occurs. |

### OH_ResourceManager_GetDrawableDescriptor()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetDrawableDescriptor(const NativeResourceManager *mgr, uint32_t resId, ArkUI_DrawableDescriptor **drawableDescriptor, uint32_t density = 0, uint32_t type = 0)
```

**Description**

Gets the DrawableDescriptor object corresponding to the icon resource by specifying the resource ID, screen density, and icon type.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| uint32_t resId | Input parameter. Resource ID. |
| [ArkUI_DrawableDescriptor](../apis-arkui/capi-arkui-nativemodule-arkui-drawabledescriptor.md) **drawableDescriptor | Output parameter. Pointer to the DrawableDescriptor object. |
| density | Input parameter, optional. Screen density. For the value range, see[ScreenDensity](capi-resmgr-common-h.md#screendensity). The default value is 0, which indicates the current system screen density. |
| type | Input parameter, optional. Icon type. The default value is 0.<br>     0: application icon.<br>     1: application theme icon. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_RES_ID_NOT_FOUND if the resource ID is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_ID if no matching resource is found by the resource ID. |

### OH_ResourceManager_GetDrawableDescriptorData()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetDrawableDescriptorData(const NativeResourceManager *mgr, uint32_t resId, ArkUI_DrawableDescriptor **drawableDescriptor, uint32_t density, uint32_t type)
```

**Description**

Gets the DrawableDescriptor object corresponding to the icon resource by specifying the resource ID, screen density, and icon type.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| uint32_t resId | Input parameter. Resource ID. |
| [ArkUI_DrawableDescriptor](../apis-arkui/capi-arkui-nativemodule-arkui-drawabledescriptor.md) **drawableDescriptor | Output parameter. Pointer to the DrawableDescriptor object. |
| uint32_t density | Input parameter. Screen density. For the value range, see [ScreenDensity](capi-resmgr-common-h.md#screendensity). The value 0 indicates the current system screen density. If no specific density is required, set this parameter to 0. |
| uint32_t type | Input parameter. Icon type. If no specific icon type is required, set this parameter to 0.<br>     0: the application's own icon.<br>     1: the application's theme icon. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. Incorrect parameter type; 2. Parameter verification failed.<br>     Returns ERROR_CODE_RES_ID_NOT_FOUND if the resource ID is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_ID if no matching resource is found based on the resource ID. |

### OH_ResourceManager_GetDrawableDescriptorByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetDrawableDescriptorByName(const NativeResourceManager *mgr, const char *resName, ArkUI_DrawableDescriptor **drawableDescriptor, uint32_t density = 0, uint32_t type = 0)
```

**Description**

Gets the DrawableDescriptor object corresponding to the icon resource by specifying the resource name, screen density, and icon type.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| const char *resName | Input parameter. Resource name. |
| [ArkUI_DrawableDescriptor](../apis-arkui/capi-arkui-nativemodule-arkui-drawabledescriptor.md) **drawableDescriptor | Output parameter. Pointer to the DrawableDescriptor object. |
| density | Input parameter, optional. Screen density. For the value range, see [ScreenDensity](capi-resmgr-common-h.md#screendensity). The default value is 0, which indicates the current system screen density. |
| type | Input parameter, optional. Icon type. The default value is 0.<br>     0: application icon.<br>     1: application theme icon.<br>     2: application dynamic icon. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. Incorrect parameter type; 2. Parameter verification failed.<br>     Returns ERROR_CODE_RES_NAME_NOT_FOUND if the resource name is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_NAME if no matching resource is found by the resource name. |

### OH_ResourceManager_GetDrawableDescriptorDataByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetDrawableDescriptorDataByName(const NativeResourceManager *mgr, const char *resName, ArkUI_DrawableDescriptor **drawableDescriptor, uint32_t density, uint32_t type)
```

**Description**

Gets the DrawableDescriptor object of the corresponding icon resource by specifying the resource name and screen density.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| const char *resName | Input parameter. Resource name. |
| [ArkUI_DrawableDescriptor](../apis-arkui/capi-arkui-nativemodule-arkui-drawabledescriptor.md) **drawableDescriptor | Output parameter. Pointer to the DrawableDescriptor object. |
| uint32_t density | Input parameter. Screen density. For the value range, see [ScreenDensity](capi-resmgr-common-h.md#screendensity). The value 0 indicates the current system screen density. If no specific density is required, set this parameter to 0. |
| uint32_t type | Input parameter. Icon type. If no specific icon type is required, set this parameter to 0.<br>0: application icon.<br>1: theme icon.<br>2: dynamic icon. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_RES_NAME_NOT_FOUND if the resource name is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_NAME if no matching resource is found by the resource name. |

### OH_ResourceManager_GetSymbol()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetSymbol(const NativeResourceManager *mgr, uint32_t resId, uint32_t *resultValue)
```

**Description**

Gets the Unicode encoding of the Symbol icon corresponding to the specified resource ID.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| uint32_t resId | Input parameter. Resource ID. |
| uint32_t *resultValue | Output parameter. Returns the Unicode encoding of the Symbol icon. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_RES_ID_NOT_FOUND if the resource ID is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_ID if no matching resource is found based on the resource ID.<br>     Returns ERROR_CODE_RES_REF_TOO_MUCH if the resource has a circular reference. |

### OH_ResourceManager_GetSymbolByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetSymbolByName(const NativeResourceManager *mgr, const char *resName, uint32_t *resultValue)
```

**Description**

Gets the Unicode encoding of the Symbol icon corresponding to the specified resource name.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| const char *resName | Input parameter. Resource name. |
| uint32_t *resultValue | Output parameter. Unicode encoding of the returned Symbol icon. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_RES_NAME_NOT_FOUND if the resource name is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_NAME if no matching resource is found by the resource name.<br>     Returns ERROR_CODE_RES_REF_TOO_MUCH if the resource has a circular reference. |

### OH_ResourceManager_GetLocales()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetLocales(const NativeResourceManager *mgr, char ***resultValue, uint32_t *resultLen, bool includeSystem = false)
```

**Description**

Gets the list of languages supported by the application.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| char ***resultValue | Output parameter. Pointer to the array of language lists. The memory is allocated by this function and must be released through [OH_ResourceManager_ReleaseStringArray](capi-ohresmgr-h.md#oh_resourcemanager_releasestringarray) after use. |
| uint32_t *resultLen | Output parameter. Pointer to the length of the language list. |
| includeSystem | Input parameter, optional. Whether to include system resources. The value true means to include system resources, and false means not to include system resources. The default value is false.<br>     When the system resource manager object is used to obtain the language list, the system resource language list is always returned. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_OUT_OF_MEMORY if memory overflow occurs. |

### OH_ResourceManager_GetLocalesData()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetLocalesData(const NativeResourceManager *mgr, char ***resultValue, uint32_t *resultLen, bool includeSystem)
```

**Description**

Gets the list of languages supported by the application.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| char ***resultValue | Output parameter. Returns a pointer to the array of the language list. The memory is allocated by this function and must be released through [OH_ResourceManager_ReleaseStringArray](capi-ohresmgr-h.md#oh_resourcemanager_releasestringarray) after use. |
| uint32_t *resultLen | Output parameter. Returns the length of the language list. |
| bool includeSystem | Input parameter. Whether to include system resources. The value true indicates that system resources are included, and false indicates that they are not included.<br>     When the system resource manager object is used to obtain the language list, the system resource language list is always returned. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. Incorrect parameter type; 2. Parameter verification failed.<br>     Returns ERROR_CODE_OUT_OF_MEMORY if memory overflow occurs. |

### OH_ResourceManager_GetConfiguration()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetConfiguration(const NativeResourceManager *mgr, ResourceManager_Configuration *configuration)
```

**Description**

Gets the device configuration information, including screen orientation, language region, device type, screen density, and color mode.

**Since**: 12

**Deprecated from**: 20

**Replacement API:** [OH_ResourceManager_GetResourceConfiguration](capi-ohresmgr-h.md#oh_resourcemanager_getresourceconfiguration)

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| [ResourceManager_Configuration](capi-resourcemanager-resourcemanager-configuration.md) *configuration | Output parameter. Returns the device configuration information, where screenDensity is the device screen density (dpi) divided by 160 and rounded down.<br>     The locale string in configuration is allocated by this function. After use, release locale through [OH_ResourceManager_ReleaseConfiguration](capi-ohresmgr-h.md#oh_resourcemanager_releaseconfiguration). If the configuration pointer is allocated by malloc(), release it through free() after use. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_SYSTEM_RES_MANAGER_GET_FAILED if accessing system resources fails.<br>     Returns ERROR_CODE_OUT_OF_MEMORY if memory overflow occurs. |

### OH_ResourceManager_GetResourceConfiguration()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetResourceConfiguration(const NativeResourceManager *mgr, ResourceManager_Configuration *configuration)
```

**Description**

Gets the device configuration information, including screen orientation, language region, device type, screen density, and color mode.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| [ResourceManager_Configuration](capi-resourcemanager-resourcemanager-configuration.md) *configuration | Output parameter. Returns the device configuration information, where the value of screenDensity is the device screen density (dpi).<br>     The locale string in configuration is allocated by this function. After use, release locale through [OH_ResourceManager_ReleaseConfiguration](capi-ohresmgr-h.md#oh_resourcemanager_releaseconfiguration). If the configuration pointer is allocated by malloc(), it must be released by free() after use. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_SYSTEM_RES_MANAGER_GET_FAILED if accessing system resources fails.<br>     Returns ERROR_CODE_OUT_OF_MEMORY if the memory is insufficient. |

### OH_ResourceManager_ReleaseConfiguration()

```c
ResourceManager_ErrorCode OH_ResourceManager_ReleaseConfiguration(ResourceManager_Configuration *configuration)
```

**Description**

Releases the memory allocated by [OH_ResourceManager_GetConfiguration](capi-ohresmgr-h.md#oh_resourcemanager_getconfiguration) or [OH_ResourceManager_GetResourceConfiguration](capi-ohresmgr-h.md#oh_resourcemanager_getresourceconfiguration).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ResourceManager_Configuration](capi-resourcemanager-resourcemanager-configuration.md) *configuration | Input parameter. Pointer to the [ResourceManager_Configuration](capi-resourcemanager-resourcemanager-configuration.md) object whose memory needs to be released. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification failed. |

### OH_ResourceManager_GetString()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetString(const NativeResourceManager *mgr, uint32_t resId, char **resultValue, ...)
```

**Description**

Gets the corresponding plain string or format string by specifying the resource ID.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| uint32_t resId | Input parameter. Resource ID. |
| char **resultValue | Output parameter. Returns a string pointer. The memory is allocated by malloc() and must be released by free() after use. |
| ... | Input parameter, optional. Indicates a variable argument list used to format the string. It supports three types: const char*, int, and float.<br>     When obtaining a plain string, this parameter is not required. When obtaining a format string, it is mandatory. The variable arguments of the corresponding types must be passed in sequence according to the placeholders in the string, and the number and types of arguments must be consistent with the placeholders in the string. For example, if the string contains three placeholders %d, %s, and %f, the call is OH_ResourceManager_GetString(mgr, resId, resultValue, 10, "format", 10.10). |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_RES_ID_NOT_FOUND if the resource ID is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_ID if no matching resource is found based on the resource ID.<br>     Returns ERROR_CODE_RES_REF_TOO_MUCH if the resource has a circular reference.<br>     Returns ERROR_CODE_OUT_OF_MEMORY if memory overflow occurs. |

### OH_ResourceManager_GetStringByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetStringByName(const NativeResourceManager *mgr, const char *resName, char **resultValue, ...)
```

**Description**

Gets the corresponding plain string or format string by specifying the resource name.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| const char *resName | Input parameter. Resource name. |
| char **resultValue | Output parameter. Pointer to the returned string, which is allocated by malloc() and must be released by free() after use. |
| ... | Input parameter, optional. Indicates a variable argument list used to format the string, supporting three types: const char*, int, and float.<br>     When obtaining a plain string, this parameter is not required. When obtaining a format string, it is mandatory, and variable arguments of the corresponding types must be passed in sequence according to the placeholders in the string. The number and types of arguments must be consistent with the placeholders in the string. For example, if the string contains three placeholders %d, %s, and %f, the call is OH_ResourceManager_GetStringByName(mgr, resName, resultValue, 10, "format", 10.10). |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_RES_NAME_NOT_FOUND if the resource name is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_NAME if no matching resource is found by the resource name.<br>     Returns ERROR_CODE_RES_REF_TOO_MUCH if the resource has circular references.<br>     Returns ERROR_CODE_OUT_OF_MEMORY if memory overflow occurs. |

### OH_ResourceManager_GetStringArray()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetStringArray(const NativeResourceManager *mgr, uint32_t resId, char ***resultValue, uint32_t *resultLen)
```

**Description**

Gets the corresponding string array by specifying the resource ID.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| uint32_t resId | Input parameter. Resource ID. |
| char ***resultValue | Output parameter. Pointer to the string array returned. The memory is allocated by this function and must be released through [OH_ResourceManager_ReleaseStringArray](capi-ohresmgr-h.md#oh_resourcemanager_releasestringarray) after use. |
| uint32_t *resultLen | Output parameter. Length of the string array returned. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_RES_ID_NOT_FOUND if the resource ID is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_ID if no matching resource is found based on the resource ID.<br>     Returns ERROR_CODE_RES_REF_TOO_MUCH if the resource has a circular reference.<br>     Returns ERROR_CODE_OUT_OF_MEMORY if memory overflow occurs. |

### OH_ResourceManager_GetStringArrayByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetStringArrayByName(const NativeResourceManager *mgr, const char *resName, char ***resultValue, uint32_t *resultLen)
```

**Description**

Gets the corresponding string array by specifying the resource name.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| const char *resName | Input parameter. Resource name. |
| char ***resultValue | Output parameter. Pointer to the returned string array. The memory is allocated by this function and must be released through [OH_ResourceManager_ReleaseStringArray](capi-ohresmgr-h.md#oh_resourcemanager_releasestringarray) after use. |
| uint32_t *resultLen | Output parameter. Length of the returned string array. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_RES_NAME_NOT_FOUND if the resource name is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_NAME if no matching resource is found by the resource name.<br>     Returns ERROR_CODE_RES_REF_TOO_MUCH if the resource has a circular reference.<br>     Returns ERROR_CODE_OUT_OF_MEMORY if the memory overflows. |

### OH_ResourceManager_ReleaseStringArray()

```c
ResourceManager_ErrorCode OH_ResourceManager_ReleaseStringArray(char ***resValue, uint32_t len)
```

**Description**

Releases the memory of the string array.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| char ***resValue | Input parameter. Pointer to the string array to be released. |
| uint32_t len | Input parameter. Length of the string array. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails. |

### OH_ResourceManager_GetPluralString()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetPluralString(const NativeResourceManager *mgr, uint32_t resId, uint32_t num, char **resultValue)
```

**Description**

Gets the corresponding plural numeric string by specifying the resource ID.<br> In the Chinese environment, the string does not distinguish singular and plural; in other languages, the string distinguishes singular and plural. For specific rules, see [language singular and plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In English, German and other languages, plural types include cardinal (such as 1, 2, 3) and ordinal (such as 1st, 2nd, 3rd). This function only supports cardinal numeral types.

**Since**: 12

**Deprecated version**: 16

**Substitute**: [OH_ResourceManager_GetIntPluralString](capi-ohresmgr-h.md#oh_resourcemanager_getintpluralstring)

**Parameters**

| Name| Description|
|--| -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| uint32_t resId | Input parameter. Resource ID. |
| uint32_t num | Input parameter. Quantity value, used to get the corresponding plural string based on the plural rules of the current language. |
| char **resultValue | Output parameter. Pointer to the returned string. The memory is allocated by malloc() and must be released by free() after use. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_RES_ID_NOT_FOUND if the resource ID is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_ID if no matching resource is found based on the resource ID.<br>     Returns ERROR_CODE_RES_REF_TOO_MUCH if the resource has a circular reference.<br>     Returns ERROR_CODE_OUT_OF_MEMORY if memory overflow occurs. |

### OH_ResourceManager_GetPluralStringByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetPluralStringByName(const NativeResourceManager *mgr, const char *resName, uint32_t num, char **resultValue)
```

**Description**

Gets the corresponding plural numeric string by specifying the resource name.<br> In the Chinese environment, the string does not distinguish singular and plural; in other languages, the string distinguishes singular and plural. For specific rules, see [language singular and plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In English, German and other languages, plural types include cardinal (such as 1, 2, 3) and ordinal (such as 1st, 2nd, 3rd). This function only supports cardinal numeral types.

**Since**: 12

**Deprecated version**: 16

**Substitute**: [OH_ResourceManager_GetIntPluralStringByName](capi-ohresmgr-h.md#oh_resourcemanager_getintpluralstringbyname)

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| const char *resName | Input parameter. Resource name. |
| uint32_t num | Input parameter. Quantity value, used to obtain the corresponding plural string based on the plural rules of the current language. |
| char **resultValue | Output parameter. Returns a string pointer. The memory is allocated by malloc() and must be released by free() after use. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_RES_NAME_NOT_FOUND if the resource name is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_NAME if no matching resource is found by the resource name.<br>     Returns ERROR_CODE_RES_REF_TOO_MUCH if the resource has a circular reference.<br>     Returns ERROR_CODE_OUT_OF_MEMORY if memory overflow occurs. |

### OH_ResourceManager_GetIntPluralString()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetIntPluralString(const NativeResourceManager *mgr, uint32_t resId, uint32_t num, char **resultValue, ...)
```

**Description**

Gets the corresponding plural string and format it by specifying the resource ID, an integer quantity value, and variable parameters.<br> In the Chinese environment, the string does not distinguish singular and plural; in other languages, the string distinguishes singular and plural. For specific rules, see [language singular and plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In English, German and other languages, plural types include cardinal (such as 1, 2, 3) and ordinal (such as 1st, 2nd, 3rd). This function only supports cardinal numeral types.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| uint32_t resId | Input parameter. Resource ID. |
| uint32_t num | Input parameter. Quantity value (integer), used to get the corresponding plural string based on the plural rules of the current language. |
| char **resultValue | Output parameter. Pointer to the returned string. The memory is allocated by malloc() and must be released by free() after use. |
| ... | Input parameter, optional. Variable argument list used to format the string, supporting three types: const char*, int, and float.<br>     When obtaining a formatted string, pass the variable arguments of the corresponding types in the order of the placeholders in the string. The number and types of the arguments must be consistent with the placeholders in the string. For example, if the string contains three placeholders %d, %s, and %f, call OH_ResourceManager_GetIntPluralString(mgr, resId, 10, resultValue, 10, "format", 10.10). |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. incorrect parameter type; 2. parameter validation failure.<br>     Returns ERROR_CODE_RES_ID_NOT_FOUND if the resource ID is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_ID if no matching resource is found by the resource ID.<br>     Returns ERROR_CODE_RES_REF_TOO_MUCH if the resource has a circular reference.<br>     Returns ERROR_CODE_OUT_OF_MEMORY if memory overflow occurs. |

### OH_ResourceManager_GetIntPluralStringByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetIntPluralStringByName(const NativeResourceManager *mgr, const char *resName, uint32_t num, char **resultValue, ...)
```

**Description**

Gets the corresponding plural string and formats it by specifying the resource name, integer quantity value, and variable parameters.<br> In the Chinese environment, the string does not distinguish singular and plural; in other languages, the string distinguishes singular and plural. For specific rules, see [language plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In English, German, and other languages, plural types include cardinal (for example, 1, 2, 3) and ordinal (for example, 1st, 2nd, 3rd). This function only supports cardinal numeral types.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| const char *resName | Input parameter. Resource name. |
| uint32_t num | Input parameter. Integer quantity used to get the corresponding plural string based on the plural rules of the current language. |
| char **resultValue | Output parameter. Pointer to the returned string. The memory is allocated by malloc() and must be released by free() after use. |
| ... | Input parameter, optional. Indicates a variable argument list used to format the string, supporting three types: const char*, int, and float.<br>     When obtaining a formatted string, pass the variable arguments of the corresponding types in the order of the placeholders in the string. The number and types of the arguments must be consistent with the placeholders in the string. For example, if the string contains three placeholders %d, %s, and %f, call OH_ResourceManager_GetIntPluralStringByName(mgr, resName, 10, resultValue, 10, "format", 10.10). |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_RES_NAME_NOT_FOUND if the resource name is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_NAME if no matching resource is found by the resource name.<br>     Returns ERROR_CODE_RES_REF_TOO_MUCH if the resource has circular references.<br>     Returns ERROR_CODE_OUT_OF_MEMORY if memory overflow occurs. |

### OH_ResourceManager_GetDoublePluralString()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetDoublePluralString(const NativeResourceManager *mgr, uint32_t resId, double num, char **resultValue, ...)
```

**Description**

Obtains the corresponding plural string and formats it by specifying the resource ID, a floating-point value for the quantity, and variable arguments.<br> In Chinese, strings do not distinguish between singular and plural; in other languages, strings distinguish between singular and plural. For details, see [Language Plural Rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In languages such as English and German, plural types include cardinal numbers (for example, 1, 2, 3) and ordinal numbers (for example, 1st, 2nd, 3rd). This function only supports use with cardinal number types.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| uint32_t resId | Input parameter. Resource ID. |
| double num | Input parameter. Quantity value (floating-point number), used to obtain the corresponding plural string based on the plural rules of the current language. |
| char **resultValue | Output parameter. Returns the string pointer. The memory is allocated by malloc() and must be released by free() after use. |
| ... | Input parameter, optional. Indicates a variable argument list used to format the string, supporting three types: const char*, int, and float.<br>     When obtaining a formatted string, pass the variable arguments of the corresponding types in the order of the placeholders in the string. The number and types of the arguments must be consistent with the placeholders in the string. For example, if the string contains three placeholders %d, %s, and %f, call it as OH_ResourceManager_GetDoublePluralString(mgr, resId, 1.1, resultValue, 10, "format", 10.10). |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_RES_ID_NOT_FOUND if the resource ID is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_ID if no matching resource is found based on the resource ID.<br>     Returns ERROR_CODE_RES_REF_TOO_MUCH if the resource has a circular reference.<br>     Returns ERROR_CODE_OUT_OF_MEMORY if the memory is insufficient. |

### OH_ResourceManager_GetDoublePluralStringByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetDoublePluralStringByName(const NativeResourceManager *mgr, const char *resName, double num, char **resultValue, ...)
```

**Description**

Gets the corresponding plural string by specifying the resource name, floating-point quantity value, and variable parameters, and formats the string.<br> In the Chinese environment, the string does not distinguish singular and plural; in other languages, the string distinguishes singular and plural. For specific rules, see [language plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In English, German, and other languages, plural types include cardinal (for example, 1, 2, 3) and ordinal (for example, 1st, 2nd, 3rd). This function only supports cardinal numeral types.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| const char *resName | Input parameter. Resource name. |
| double num | Input parameter. Quantity value (floating-point number), used to get the corresponding plural string based on the plural rules of the current language. |
| char **resultValue | Output parameter. Returns a string pointer. The memory is allocated by malloc() and must be released by free() after use. |
| ... | Input parameter, optional. Indicates a variable argument list used to format the string. It supports three types: const char*, int, and float.<br>     When obtaining a formatted string, pass the variable arguments of the corresponding types in the order of the placeholders in the string. The number and types of arguments must be consistent with the placeholders in the string. For example, if the string contains three placeholders %d, %s, and %f, call OH_ResourceManager_GetDoublePluralStringByName(mgr, resName, 1.1, resultValue, 10, "format", 10.10). |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_RES_NAME_NOT_FOUND if the resource name is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_NAME if no matching resource is found by the resource name.<br>     Returns ERROR_CODE_RES_REF_TOO_MUCH if the resource has a circular reference.<br>     Returns ERROR_CODE_OUT_OF_MEMORY if memory overflow occurs. |

### OH_ResourceManager_GetColor()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetColor(const NativeResourceManager *mgr, uint32_t resId, uint32_t *resultValue)
```

**Description**

Gets the color resource value corresponding to the specified resource ID.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| uint32_t resId | Input parameter. Resource ID. |
| uint32_t *resultValue | Output parameter. Pointer to the color resource value returned. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_RES_ID_NOT_FOUND if the resource ID is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_ID if no matching resource is found by the resource ID.<br>     Returns ERROR_CODE_RES_REF_TOO_MUCH if the resource has a circular reference. |

### OH_ResourceManager_GetColorByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetColorByName(const NativeResourceManager *mgr, const char *resName, uint32_t *resultValue)
```

**Description**

Gets the color resource value corresponding to the specified resource name.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| const char *resName | Input parameter. Resource name. |
| uint32_t *resultValue | Output parameter. Pointer to the color resource value returned. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_RES_NAME_NOT_FOUND if the resource name is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_NAME if no matching resource is found by the resource name.<br>     Returns ERROR_CODE_RES_REF_TOO_MUCH if the resource has a circular reference. |

### OH_ResourceManager_GetInt()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetInt(const NativeResourceManager *mgr, uint32_t resId, int *resultValue)
```

**Description**

Gets the integer resource value corresponding to the specified resource ID.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| uint32_t resId | Input parameter. Resource ID. |
| int *resultValue | Output parameter. Pointer to the integer resource value returned. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_RES_ID_NOT_FOUND if the resource ID is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_ID if no matching resource is found based on the resource ID.<br>     Returns ERROR_CODE_RES_REF_TOO_MUCH if the resource has a circular reference. |

### OH_ResourceManager_GetIntByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetIntByName(const NativeResourceManager *mgr, const char *resName, int *resultValue)
```

**Description**

Gets the integer resource value corresponding to the specified resource name.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| const char *resName | Input parameter. Resource name. |
| int *resultValue | Output parameter. Pointer to the integer resource value returned. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_RES_NAME_NOT_FOUND if the resource name is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_NAME if no matching resource is found by the resource name.<br>     Returns ERROR_CODE_RES_REF_TOO_MUCH if the resource has a circular reference. |

### OH_ResourceManager_GetFloat()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetFloat(const NativeResourceManager *mgr, uint32_t resId, float *resultValue)
```

**Description**

Gets the floating-point resource value corresponding to the specified resource ID.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| uint32_t resId | Input parameter. Resource ID. |
| float *resultValue | Output parameter. Floating-point resource value returned. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_RES_ID_NOT_FOUND if the resource ID is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_ID if no matching resource is found by the resource ID.<br>     Returns ERROR_CODE_RES_REF_TOO_MUCH if the resource has a circular reference. |

### OH_ResourceManager_GetFloatByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetFloatByName(const NativeResourceManager *mgr, const char *resName, float *resultValue)
```

**Description**

Gets the floating-point resource value corresponding to the specified resource name.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| const char *resName | Input parameter. Resource name. |
| float *resultValue | Output parameter. Pointer to the floating-point resource value. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_RES_NAME_NOT_FOUND if the resource name is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_NAME if no matching resource is found by the resource name.<br>     Returns ERROR_CODE_RES_REF_TOO_MUCH if the resource has a circular reference. |

### OH_ResourceManager_GetBool()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetBool(const NativeResourceManager *mgr, uint32_t resId, bool *resultValue)
```

**Description**

Gets the boolean resource value corresponding to the specified resource ID.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| uint32_t resId | Input parameter. Resource ID. |
| bool *resultValue | Output parameter. Returns the boolean resource value. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. incorrect parameter type; 2. parameter verification failed.<br>     Returns ERROR_CODE_RES_ID_NOT_FOUND if the resource ID is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_ID if no matching resource is found based on the resource ID.<br>     Returns ERROR_CODE_RES_REF_TOO_MUCH if the resource has a circular reference. |

### OH_ResourceManager_GetBoolByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetBoolByName(const NativeResourceManager *mgr, const char *resName, bool *resultValue)
```

**Description**

Gets the boolean resource value corresponding to the specified resource name.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager). |
| const char *resName | Input parameter. Resource name. |
| bool *resultValue | Output parameter. Pointer to the parameter used to return the boolean resource value. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. Incorrect parameter type; 2. Parameter verification failed.<br>     Returns ERROR_CODE_RES_NAME_NOT_FOUND if the resource name is invalid.<br>     Returns ERROR_CODE_RES_NOT_FOUND_BY_NAME if no matching resource is found by the resource name.<br>     Returns ERROR_CODE_RES_REF_TOO_MUCH if the resource has a circular reference. |

### OH_ResourceManager_AddResource()

```c
ResourceManager_ErrorCode OH_ResourceManager_AddResource(const NativeResourceManager *mgr, const char *path)
```

**Description**

Dynamically loads overlay resources at application runtime to implement theme switching or resource overriding.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| const char *path | Input parameter. Pointer to the absolute path of the HSP or HAP resource package to be loaded. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. The parameter type is incorrect; 2. Parameter verification fails.<br>     Returns ERROR_CODE_OVERLAY_RES_PATH_INVALID if the overlay path is invalid. |

### OH_ResourceManager_RemoveResource()

```c
ResourceManager_ErrorCode OH_ResourceManager_RemoveResource(const NativeResourceManager *mgr, const char *path)
```

**Description**

Removes the specified overlay resources at application runtime to restore the resources before being overridden.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object, which is obtained through the [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager) function. |
| const char *path | Input parameter. Absolute path of the HSP or HAP resource package to be removed. |

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     Returns SUCCESS if the operation is successful.<br>     Returns ERROR_CODE_INVALID_INPUT_PARAMETER if the input parameter is invalid. Possible causes: 1. Incorrect parameter type; 2. Parameter verification failed.<br>     Returns ERROR_CODE_OVERLAY_RES_PATH_INVALID if the overlay path is invalid. |

