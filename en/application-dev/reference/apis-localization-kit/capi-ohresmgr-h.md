# ohresmgr.h

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->

## Overview

Provides the capability of obtaining resources in the resource management native layer.

**File to include**: <resourcemanager/ohresmgr.h>

**Library**: libohresmgr.so

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 12

**Related module**: [resourcemanager](capi-resourcemanager.md)

## Summary

### Callback

| Name| Description|
| -- | -- |
| [ResourceManager_ErrorCode OH_ResourceManager_GetMediaBase64(const NativeResourceManager *mgr, uint32_t resId, char **resultValue, uint64_t *resultLen, uint32_t density = 0)](#oh_resourcemanager_getmediabase64) | Obtains the Base64-encoded string of the media resource by the specified resource ID and screen density.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetMediaBase64Data(const NativeResourceManager *mgr, uint32_t resId, char **resultValue, uint64_t *resultLen, uint32_t density)](#oh_resourcemanager_getmediabase64data) | Obtains the Base64-encoded string of the media resource by the specified resource ID and screen density.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetMediaBase64ByName(const NativeResourceManager *mgr, const char *resName, char **resultValue, uint64_t *resultLen, uint32_t density = 0)](#oh_resourcemanager_getmediabase64byname) | Obtains the Base64-encoded string of the media resource by the specified resource name and screen density.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetMediaBase64DataByName(const NativeResourceManager *mgr, const char *resName, char **resultValue, uint64_t *resultLen, uint32_t density)](#oh_resourcemanager_getmediabase64databyname) | Obtains the Base64-encoded string of the media resource by the specified resource name and screen density.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetMedia(const NativeResourceManager *mgr, uint32_t resId, uint8_t **resultValue, uint64_t *resultLen, uint32_t density = 0)](#oh_resourcemanager_getmedia) | Obtains the binary data of the media resource by the specified resource ID and screen density.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetMediaData(const NativeResourceManager *mgr, uint32_t resId, uint8_t **resultValue, uint64_t *resultLen, uint32_t density)](#oh_resourcemanager_getmediadata) | Obtains the binary data of the media resource by the specified resource ID and screen density.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetMediaByName(const NativeResourceManager *mgr, const char *resName, uint8_t **resultValue, uint64_t *resultLen, uint32_t density = 0)](#oh_resourcemanager_getmediabyname) | Obtains the binary data of the media resource by the specified resource name and screen density.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetMediaDataByName(const NativeResourceManager *mgr, const char *resName, uint8_t **resultValue, uint64_t *resultLen, uint32_t density)](#oh_resourcemanager_getmediadatabyname) | Obtains the binary data of the media resource by the specified resource name and screen density.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetDrawableDescriptor(const NativeResourceManager *mgr, uint32_t resId, ArkUI_DrawableDescriptor **drawableDescriptor, uint32_t density = 0, uint32_t type = 0)](#oh_resourcemanager_getdrawabledescriptor) | Obtains the DrawableDescriptor object of the icon resource by the specified resource ID, screen density, and icon type.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetDrawableDescriptorData(const NativeResourceManager *mgr, uint32_t resId, ArkUI_DrawableDescriptor **drawableDescriptor, uint32_t density, uint32_t type)](#oh_resourcemanager_getdrawabledescriptordata) | Obtains the DrawableDescriptor object of the icon resource by the specified resource ID, screen density, and icon type.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetDrawableDescriptorByName(const NativeResourceManager *mgr, const char *resName, ArkUI_DrawableDescriptor **drawableDescriptor, uint32_t density = 0, uint32_t type = 0)](#oh_resourcemanager_getdrawabledescriptorbyname) | Obtains the DrawableDescriptor object of the icon resource by the specified resource name, screen density, and icon type.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetDrawableDescriptorDataByName(const NativeResourceManager *mgr, const char *resName, ArkUI_DrawableDescriptor **drawableDescriptor, uint32_t density, uint32_t type)](#oh_resourcemanager_getdrawabledescriptordatabyname) | Obtains the DrawableDescriptor object of the icon resource by the specified resource name and screen density.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetSymbol(const NativeResourceManager *mgr, uint32_t resId, uint32_t *resultValue)](#oh_resourcemanager_getsymbol) | Obtains the Unicode encoding of the symbol icon corresponding to the specified resource ID.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetSymbolByName(const NativeResourceManager *mgr, const char *resName, uint32_t *resultValue)](#oh_resourcemanager_getsymbolbyname) | Obtains the Unicode encoding of the symbol icon corresponding to the specified resource name.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetLocales(const NativeResourceManager *mgr, char ***resultValue, uint32_t *resultLen, bool includeSystem = false)](#oh_resourcemanager_getlocales) | Obtains the list of languages supported by an application.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetLocalesData(const NativeResourceManager *mgr, char ***resultValue, uint32_t *resultLen, bool includeSystem)](#oh_resourcemanager_getlocalesdata) | Obtains the list of languages supported by an application.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetConfiguration(const NativeResourceManager *mgr, ResourceManager_Configuration *configuration)](#oh_resourcemanager_getconfiguration) | Obtains the configuration information of a device, such as the screen orientation, language and region, device type, screen density, and color mode. (It is deprecated in API version 20.)|
| [ResourceManager_ErrorCode OH_ResourceManager_GetResourceConfiguration(const NativeResourceManager *mgr, ResourceManager_Configuration *configuration)](#oh_resourcemanager_getresourceconfiguration) | Obtains the configuration information of a device, such as the screen orientation, language and region, device type, screen density, and color mode.|
| [ResourceManager_ErrorCode OH_ResourceManager_ReleaseConfiguration(ResourceManager_Configuration *configuration)](#oh_resourcemanager_releaseconfiguration) | Releases the memory requested through the [OH_ResourceManager_GetConfiguration](capi-ohresmgr-h.md#oh_resourcemanager_getconfiguration) or [OH_ResourceManager_GetResourceConfiguration](capi-ohresmgr-h.md#oh_resourcemanager_getresourceconfiguration) function.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetString(const NativeResourceManager *mgr, uint32_t resId, char **resultValue, ...)](#oh_resourcemanager_getstring) | Obtains a plain or formatted string based on the specified resource ID.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetStringByName(const NativeResourceManager *mgr, const char *resName, char **resultValue, ...)](#oh_resourcemanager_getstringbyname) | Obtains a plain or formatted string based on the specified resource name.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetStringArray(const NativeResourceManager *mgr, uint32_t resId, char ***resultValue, uint32_t *resultLen)](#oh_resourcemanager_getstringarray) | Obtains the string array based on the specified resource ID.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetStringArrayByName(const NativeResourceManager *mgr, const char *resName, char ***resultValue, uint32_t *resultLen)](#oh_resourcemanager_getstringarraybyname) | Obtains the string array based on the specified resource name.|
| [ResourceManager_ErrorCode OH_ResourceManager_ReleaseStringArray(char ***resValue, uint32_t len)](#oh_resourcemanager_releasestringarray) | Releases the memory of the string array.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetPluralString(const NativeResourceManager *mgr, uint32_t resId, uint32_t num, char **resultValue)](#oh_resourcemanager_getpluralstring) | Obtains the plural string based on the specified resource ID.<br> The Chinese language does not distinguish between singular and plural forms in strings, whereas other languages do. For details about the specific rules, see [language plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In languages such as English and German, plural categories include cardinal forms (for example, 1, 2, 3) and ordinal forms (for example, 1st, 2nd, 3rd). This function applies only to cardinal forms. (This API is deprecated since API version 16.)|
| [ResourceManager_ErrorCode OH_ResourceManager_GetPluralStringByName(const NativeResourceManager *mgr, const char *resName, uint32_t num, char **resultValue)](#oh_resourcemanager_getpluralstringbyname) | Obtains the plural string based on the specified resource name.<br> The Chinese language does not distinguish between singular and plural forms in strings, whereas other languages do. For details about the specific rules, see [language plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In languages such as English and German, plural categories include cardinal forms (for example, 1, 2, 3) and ordinal forms (for example, 1st, 2nd, 3rd). This function applies only to cardinal forms. (This API is deprecated since API version 16.)|
| [ResourceManager_ErrorCode OH_ResourceManager_GetIntPluralString(const NativeResourceManager *mgr, uint32_t resId, uint32_t num, char **resultValue, ...)](#oh_resourcemanager_getintpluralstring) | Obtains the corresponding plural string and formats it based on the specified resource ID, integer quantity, and variable parameters.<br> The Chinese language does not distinguish between singular and plural forms in strings, whereas other languages do. For details about the specific rules, see [language plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In languages such as English and German, plural categories include cardinal forms (for example, 1, 2, 3) and ordinal forms (for example, 1st, 2nd, 3rd). This function applies only to cardinal forms.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetIntPluralStringByName(const NativeResourceManager *mgr, const char *resName, uint32_t num, char **resultValue, ...)](#oh_resourcemanager_getintpluralstringbyname) | Obtains the corresponding plural string and formats it based on the specified resource name, integer quantity, and variable parameters.<br> The Chinese language does not distinguish between singular and plural forms in strings, whereas other languages do. For details about the specific rules, see [language plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In languages such as English and German, plural categories include cardinal forms (for example, 1, 2, 3) and ordinal forms (for example, 1st, 2nd, 3rd). This function applies only to cardinal forms.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetDoublePluralString(const NativeResourceManager *mgr, uint32_t resId, double num, char **resultValue, ...)](#oh_resourcemanager_getdoublepluralstring) | Obtains the corresponding plural string and formats it based on the specified resource ID, floating-point quantity, and variable parameters.<br> The Chinese language does not distinguish between singular and plural forms in strings, whereas other languages do. For details about the specific rules, see [language plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In languages such as English and German, plural categories include cardinal forms (for example, 1, 2, 3) and ordinal forms (for example, 1st, 2nd, 3rd). This function applies only to cardinal forms.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetDoublePluralStringByName(const NativeResourceManager *mgr, const char *resName, double num, char **resultValue, ...)](#oh_resourcemanager_getdoublepluralstringbyname) | Obtains the corresponding plural string and formats it based on the specified resource name, floating-point quantity, and variable parameters.<br> The Chinese language does not distinguish between singular and plural forms in strings, whereas other languages do. For details about the specific rules, see [language plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In languages such as English and German, plural categories include cardinal forms (for example, 1, 2, 3) and ordinal forms (for example, 1st, 2nd, 3rd). This function applies only to cardinal forms.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetColor(const NativeResourceManager *mgr, uint32_t resId, uint32_t *resultValue)](#oh_resourcemanager_getcolor) | Obtains the color resource value based on the specified resource ID.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetColorByName(const NativeResourceManager *mgr, const char *resName, uint32_t *resultValue)](#oh_resourcemanager_getcolorbyname) | Obtains the color resource value based on the specified resource name.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetInt(const NativeResourceManager *mgr, uint32_t resId, int *resultValue)](#oh_resourcemanager_getint) | Obtains the integer resource value based on the specified resource ID.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetIntByName(const NativeResourceManager *mgr, const char *resName, int *resultValue)](#oh_resourcemanager_getintbyname) | Obtains the integer resource value based on the specified resource name.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetFloat(const NativeResourceManager *mgr, uint32_t resId, float *resultValue)](#oh_resourcemanager_getfloat) | Obtains the floating-point resource value based on the specified resource ID.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetFloatByName(const NativeResourceManager *mgr, const char *resName, float *resultValue)](#oh_resourcemanager_getfloatbyname) | Obtains the floating-point resource value based on the specified resource name.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetBool(const NativeResourceManager *mgr, uint32_t resId, bool *resultValue)](#oh_resourcemanager_getbool) | Obtains the Boolean resource value based on the specified resource ID.|
| [ResourceManager_ErrorCode OH_ResourceManager_GetBoolByName(const NativeResourceManager *mgr, const char *resName, bool *resultValue)](#oh_resourcemanager_getboolbyname) | Obtains the Boolean resource value based on the specified resource name.|
| [ResourceManager_ErrorCode OH_ResourceManager_AddResource(const NativeResourceManager *mgr, const char *path)](#oh_resourcemanager_addresource) | Dynamically loads overlay resources during application runtime to implement theme switching or resource overriding.|
| [ResourceManager_ErrorCode OH_ResourceManager_RemoveResource(const NativeResourceManager *mgr, const char *path)](#oh_resourcemanager_removeresource) | Removes the specified overlay resource during application runtime and restores the original resource before the override.|

## Function Description

### OH_ResourceManager_GetMediaBase64()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetMediaBase64(const NativeResourceManager *mgr, uint32_t resId, char **resultValue, uint64_t *resultLen, uint32_t density = 0)
```

**Description**

Obtains the Base64-encoded string of the media resource by the specified resource ID and screen density.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| uint32_t resId | Input parameter. Resource ID.|
| char **resultValue | Output parameter. Pointer to the Base64-encoded string, which is allocated by **malloc()** and must be released via **free()** after use.|
| uint64_t *resultLen | Output parameter. Length of the Base64 string, in bytes.|
| density | Input parameter, which is optional. Screen density. For details about the value range, see [ScreenDensity](capi-resmgr-common-h.md#screendensity). The default value is **0**, indicating that the current system screen density is used.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_ID_NOT_FOUND**: Invalid resource ID.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_ID**: No matching resource is found based on the resource ID.<br>     **ERROR_CODE_OUT_OF_MEMORY**: Memory overflow occurs.|

### OH_ResourceManager_GetMediaBase64Data()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetMediaBase64Data(const NativeResourceManager *mgr, uint32_t resId, char **resultValue, uint64_t *resultLen, uint32_t density)
```

**Description**

Obtains the Base64-encoded string of the media resource by the specified resource ID and screen density.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| uint32_t resId | Input parameter. Resource ID.|
| char **resultValue | Output parameter. Pointer to the Base64-encoded string, which is allocated by **malloc()** and must be released via **free()** after use.|
| uint64_t *resultLen | Output parameter. Length of the Base64 string, in bytes.|
| uint32_t density | Input parameter. Screen density. For details about the value range, see [ScreenDensity](capi-resmgr-common-h.md#screendensity). The value **0** indicates that the current system screen density is used. If no specific density is required, set this parameter to **0**.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_ID_NOT_FOUND**: Invalid resource ID.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_ID**: No matching resource is found based on the resource ID.<br>     **ERROR_CODE_OUT_OF_MEMORY**: Memory overflow occurs.|

### OH_ResourceManager_GetMediaBase64ByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetMediaBase64ByName(const NativeResourceManager *mgr, const char *resName, char **resultValue, uint64_t *resultLen, uint32_t density = 0)
```

**Description**

Obtains the Base64-encoded string of the media resource by the specified resource name and screen density.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| const char *resName | Input parameter. Resource name.|
| char **resultValue | Output parameter. Pointer to the Base64-encoded string, which is allocated by **malloc()** and must be released via **free()** after use.|
| uint64_t *resultLen | Output parameter. Length of the Base64 string, in bytes.|
| density | Input parameter, which is optional. Screen density. For details about the value range, see [ScreenDensity](capi-resmgr-common-h.md#screendensity). The default value is **0**, indicating that the current system screen density is used.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_NAME_NOT_FOUND**: Invalid resource name.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_NAME**: No matching resource is found based on the resource name.<br>     **ERROR_CODE_OUT_OF_MEMORY**: Memory overflow occurs.|

### OH_ResourceManager_GetMediaBase64DataByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetMediaBase64DataByName(const NativeResourceManager *mgr, const char *resName, char **resultValue, uint64_t *resultLen, uint32_t density)
```

**Description**

Obtains the Base64-encoded string of the media resource by the specified resource name and screen density.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| const char *resName | Input parameter. Resource name.|
| char **resultValue | Output parameter. Pointer to the Base64-encoded string, which is allocated by **malloc()** and must be released via **free()** after use.|
| uint64_t *resultLen | Output parameter. Length of the Base64 string, in bytes.|
| uint32_t density | Input parameter. Screen density. For details about the value range, see [ScreenDensity](capi-resmgr-common-h.md#screendensity). The value **0** indicates that the current system screen density is used. If no specific density is required, set this parameter to **0**.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_NAME_NOT_FOUND**: Invalid resource name.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_NAME**: No matching resource is found based on the resource name.<br>     **ERROR_CODE_OUT_OF_MEMORY**: Memory overflow occurs.|

### OH_ResourceManager_GetMedia()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetMedia(const NativeResourceManager *mgr, uint32_t resId, uint8_t **resultValue, uint64_t *resultLen, uint32_t density = 0)
```

**Description**

Obtains the binary data of the media resource by the specified resource ID and screen density.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| uint32_t resId | Input parameter. Resource ID.|
| uint8_t **resultValue | Output parameter. Pointer to the media data, which is allocated by **malloc()** and must be released via **free()** after use.|
| uint64_t *resultLen | Output parameter. Data length, in bytes.|
| density | Input parameter, which is optional. Screen density. For details about the value range, see [ScreenDensity](capi-resmgr-common-h.md#screendensity). The default value is **0**, indicating that the current system screen density is used.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_ID_NOT_FOUND**: Invalid resource ID.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_ID**: No matching resource is found based on the resource ID.<br>     **ERROR_CODE_OUT_OF_MEMORY**: Memory overflow occurs.|

### OH_ResourceManager_GetMediaData()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetMediaData(const NativeResourceManager *mgr, uint32_t resId, uint8_t **resultValue, uint64_t *resultLen, uint32_t density)
```

**Description**

Obtains the binary data of the media resource by the specified resource ID and screen density.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| uint32_t resId | Input parameter. Resource ID.|
| uint8_t **resultValue | Output parameter. Pointer to the media data, which is allocated by **malloc()** and must be released via **free()** after use.|
| uint64_t *resultLen | Output parameter. Data length, in bytes.|
| uint32_t density | Input parameter. Screen density. For details about the value range, see [ScreenDensity](capi-resmgr-common-h.md#screendensity). The value **0** indicates that the current system screen density is used. If no specific density is required, set this parameter to **0**.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_ID_NOT_FOUND**: Invalid resource ID.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_ID**: No matching resource is found based on the resource ID.<br>     **ERROR_CODE_OUT_OF_MEMORY**: Memory overflow occurs.|

### OH_ResourceManager_GetMediaByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetMediaByName(const NativeResourceManager *mgr, const char *resName, uint8_t **resultValue, uint64_t *resultLen, uint32_t density = 0)
```

**Description**

Obtains the binary data of the media resource by the specified resource name and screen density.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| const char *resName | Input parameter. Resource name.|
| uint8_t **resultValue | Output parameter. Pointer to the media data, which is allocated by **malloc()** and must be released via **free()** after use.|
| uint64_t *resultLen | Output parameter. Data length, in bytes.|
| density | Input parameter, which is optional. Screen density. For details about the value range, see [ScreenDensity](capi-resmgr-common-h.md#screendensity). The default value is **0**, indicating that the current system screen density is used.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_NAME_NOT_FOUND**: Invalid resource name.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_NAME**: No matching resource is found based on the resource name.<br>     **ERROR_CODE_OUT_OF_MEMORY**: Memory overflow occurs.|

### OH_ResourceManager_GetMediaDataByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetMediaDataByName(const NativeResourceManager *mgr, const char *resName, uint8_t **resultValue, uint64_t *resultLen, uint32_t density)
```

**Description**

Obtains the binary data of the media resource by the specified resource name and screen density.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| const char *resName | Input parameter. Resource name.|
| uint8_t **resultValue | Output parameter. Pointer to the media data, which is allocated by **malloc()** and must be released via **free()** after use.|
| uint64_t *resultLen | Output parameter. Data length, in bytes.|
| uint32_t density | Input parameter. Screen density. For details about the value range, see [ScreenDensity](capi-resmgr-common-h.md#screendensity). The value **0** indicates that the current system screen density is used. If no specific density is required, set this parameter to **0**.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_NAME_NOT_FOUND**: Invalid resource name.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_NAME**: No matching resource is found based on the resource name.<br>     **ERROR_CODE_OUT_OF_MEMORY**: Memory overflow occurs.|

### OH_ResourceManager_GetDrawableDescriptor()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetDrawableDescriptor(const NativeResourceManager *mgr, uint32_t resId, ArkUI_DrawableDescriptor **drawableDescriptor, uint32_t density = 0, uint32_t type = 0)
```

**Description**

Obtains the DrawableDescriptor object of the icon resource by the specified resource ID, screen density, and icon type.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| uint32_t resId | Input parameter. Resource ID.|
| [ArkUI_DrawableDescriptor](../apis-arkui/capi-arkui-nativemodule-arkui-drawabledescriptor.md) **drawableDescriptor | Output parameter. Pointer to the DrawableDescriptor object.|
| density | Input parameter, which is optional. Screen density. For details about the value range, see [ScreenDensity](capi-resmgr-common-h.md#screendensity). The default value is **0**, indicating that the current system screen density is used.|
| type | Input parameter, which is optional. Icon type. The default value is **0**.<br>     **0**: application icon.<br>     **1**: application theme icon.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_ID_NOT_FOUND**: Invalid resource ID.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_ID**: No matching resource is found based on the resource ID.|

### OH_ResourceManager_GetDrawableDescriptorData()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetDrawableDescriptorData(const NativeResourceManager *mgr, uint32_t resId, ArkUI_DrawableDescriptor **drawableDescriptor, uint32_t density, uint32_t type)
```

**Description**

Obtains the DrawableDescriptor object of the icon resource by the specified resource ID, screen density, and icon type.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| uint32_t resId | Input parameter. Resource ID.|
| [ArkUI_DrawableDescriptor](../apis-arkui/capi-arkui-nativemodule-arkui-drawabledescriptor.md) **drawableDescriptor | Output parameter. Pointer to the DrawableDescriptor object.|
| uint32_t density | Input parameter. Screen density. For details about the value range, see [ScreenDensity](capi-resmgr-common-h.md#screendensity). The value **0** indicates that the current system screen density is used. If no specific density is required, set this parameter to **0**.|
| uint32_t type | Input parameter. Icon type. If no specific icon type is required, set this parameter to **0**.<br>     **0**: application icon.<br>     **1**: application theme icon.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_ID_NOT_FOUND**: Invalid resource ID.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_ID**: No matching resource is found based on the resource ID.|

### OH_ResourceManager_GetDrawableDescriptorByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetDrawableDescriptorByName(const NativeResourceManager *mgr, const char *resName, ArkUI_DrawableDescriptor **drawableDescriptor, uint32_t density = 0, uint32_t type = 0)
```

**Description**

Obtains the DrawableDescriptor object of the icon resource by the specified resource name, screen density, and icon type.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| const char *resName | Input parameter. Resource name.|
| [ArkUI_DrawableDescriptor](../apis-arkui/capi-arkui-nativemodule-arkui-drawabledescriptor.md) **drawableDescriptor | Output parameter. Pointer to the DrawableDescriptor object.|
| density | Input parameter, which is optional. Screen density. For details about the value range, see [ScreenDensity](capi-resmgr-common-h.md#screendensity). The default value is **0**, indicating that the current system screen density is used.|
| type | Input parameter, which is optional. Icon type. The default value is **0**.<br>     **0**: application icon.<br>     **1**: application theme icon.<br>     **2**: dynamic application icon.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_NAME_NOT_FOUND**: Invalid resource name.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_NAME**: No matching resource is found based on the resource name.|

### OH_ResourceManager_GetDrawableDescriptorDataByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetDrawableDescriptorDataByName(const NativeResourceManager *mgr, const char *resName, ArkUI_DrawableDescriptor **drawableDescriptor, uint32_t density, uint32_t type)
```

**Description**

Obtains the DrawableDescriptor object of the icon resource by the specified resource name and screen density.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| const char *resName | Input parameter. Resource name.|
| [ArkUI_DrawableDescriptor](../apis-arkui/capi-arkui-nativemodule-arkui-drawabledescriptor.md) **drawableDescriptor | Output parameter. Pointer to the DrawableDescriptor object.|
| uint32_t density | Input parameter. Screen density. For details about the value range, see [ScreenDensity](capi-resmgr-common-h.md#screendensity). The value **0** indicates that the current system screen density is used. If no specific density is required, set this parameter to **0**.|
| uint32_t type | Input parameter. Icon type. If no specific icon type is required, set this parameter to **0**.<br>**0**: application icon.<br>**1**: application theme icon.<br>**2**: dynamic icon.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_NAME_NOT_FOUND**: Invalid resource name.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_NAME**: No matching resource is found based on the resource name.|

### OH_ResourceManager_GetSymbol()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetSymbol(const NativeResourceManager *mgr, uint32_t resId, uint32_t *resultValue)
```

**Description**

Obtains the Unicode encoding of the symbol icon corresponding to the specified resource ID.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| uint32_t resId | Input parameter. Resource ID.|
| uint32_t *resultValue | Output parameter. Unicode encoding of the symbol icon.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_ID_NOT_FOUND**: Invalid resource ID.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_ID**: No matching resource is found based on the resource ID.<br>     **ERROR_CODE_RES_REF_TOO_MUCH**: The resource has a circular reference.|

### OH_ResourceManager_GetSymbolByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetSymbolByName(const NativeResourceManager *mgr, const char *resName, uint32_t *resultValue)
```

**Description**

Obtains the Unicode encoding of the symbol icon corresponding to the specified resource name.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| const char *resName | Input parameter. Resource name.|
| uint32_t *resultValue | Output parameter. Unicode encoding of the symbol icon.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_NAME_NOT_FOUND**: Invalid resource name.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_NAME**: No matching resource is found based on the resource name.<br>     **ERROR_CODE_RES_REF_TOO_MUCH**: The resource has a circular reference.|

### OH_ResourceManager_GetLocales()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetLocales(const NativeResourceManager *mgr, char ***resultValue, uint32_t *resultLen, bool includeSystem = false)
```

**Description**

Obtains the list of languages supported by an application.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| char ***resultValue | Output parameter. Pointer to the language list array. The memory is allocated by this function and must be released through [OH_ResourceManager_ReleaseStringArray](capi-ohresmgr-h.md#oh_resourcemanager_releasestringarray) after use.|
| uint32_t *resultLen | Output parameter. Length of the language list.|
| includeSystem | Input parameter, which is optional. This parameter indicates whether to include system resources. The value **true** indicates yes, and the value **false** indicates no. The default value is **false**.<br>     When the system resource manager object is used to obtain the language list, the system resource language list is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_OUT_OF_MEMORY**: Memory overflow occurs.|

### OH_ResourceManager_GetLocalesData()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetLocalesData(const NativeResourceManager *mgr, char ***resultValue, uint32_t *resultLen, bool includeSystem)
```

**Description**

Obtains the list of languages supported by an application.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| char ***resultValue | Output parameter. Pointer to the language list array. The memory is allocated by this function and must be released through [OH_ResourceManager_ReleaseStringArray](capi-ohresmgr-h.md#oh_resourcemanager_releasestringarray) after use.|
| uint32_t *resultLen | Output parameter. Length of the language list.|
| bool includeSystem | Input parameter. This parameter indicates whether to include system resources. The value **true** indicates yes, and the value **false** indicates no.<br>     When the system resource manager object is used to obtain the language list, the system resource language list is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_OUT_OF_MEMORY**: Memory overflow occurs.|

### OH_ResourceManager_GetConfiguration()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetConfiguration(const NativeResourceManager *mgr, ResourceManager_Configuration *configuration)
```

**Description**

Obtains the configuration information of a device, such as the screen orientation, language and region, device type, screen density, and color mode.

**Since**: 12

**Deprecated from**: 20

**Substitute: **[OH_ResourceManager_GetResourceConfiguration](capi-ohresmgr-h.md#oh_resourcemanager_getresourceconfiguration)

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| [ResourceManager_Configuration](capi-resourcemanager-resourcemanager-configuration.md) *configuration | Output parameter. Device configuration information, where **screenDensity** is the device screen density (in dpi) divided by 160 and rounded to an integer.<br>     The memory for the locale string in **configuration** is allocated by this function, and must be released through [OH_ResourceManager_ReleaseConfiguration](capi-ohresmgr-h.md#oh_resourcemanager_releaseconfiguration) after use. If the memory for **configuration** is allocated by **malloc()**, it must be released via **free()**.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_SYSTEM_RES_MANAGER_GET_FAILED**: Failed to access the system resource.<br>     **ERROR_CODE_OUT_OF_MEMORY**: Memory overflow occurs.|

### OH_ResourceManager_GetResourceConfiguration()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetResourceConfiguration(const NativeResourceManager *mgr, ResourceManager_Configuration *configuration)
```

**Description**

Obtains the configuration information of a device, such as the screen orientation, language and region, device type, screen density, and color mode.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| [ResourceManager_Configuration](capi-resourcemanager-resourcemanager-configuration.md) *configuration | Output parameter. Device configuration information, where **screenDensity** is the device screen density (in dpi).<br>     The memory for the locale string in **configuration** is allocated by this function, and must be released through [OH_ResourceManager_ReleaseConfiguration](capi-ohresmgr-h.md#oh_resourcemanager_releaseconfiguration) after use. If the memory for **configuration** is allocated by **malloc()**, it must be released via **free()**.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_SYSTEM_RES_MANAGER_GET_FAILED**: Failed to access the system resource.<br>     **ERROR_CODE_OUT_OF_MEMORY**: Memory overflow occurs.|

### OH_ResourceManager_ReleaseConfiguration()

```c
ResourceManager_ErrorCode OH_ResourceManager_ReleaseConfiguration(ResourceManager_Configuration *configuration)
```

**Description**

Releases the memory requested through the [OH_ResourceManager_GetConfiguration](capi-ohresmgr-h.md#oh_resourcemanager_getconfiguration) or [OH_ResourceManager_GetResourceConfiguration](capi-ohresmgr-h.md#oh_resourcemanager_getresourceconfiguration) function.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ResourceManager_Configuration](capi-resourcemanager-resourcemanager-configuration.md) *configuration | Input parameter. Pointer to the [ResourceManager_Configuration](capi-resourcemanager-resourcemanager-configuration.md) object whose memory needs to be deallocated.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.|

### OH_ResourceManager_GetString()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetString(const NativeResourceManager *mgr, uint32_t resId, char **resultValue, ...)
```

**Description**

Obtains a plain or formatted string based on the specified resource ID.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| uint32_t resId | Input parameter. Resource ID.|
| char **resultValue | Output parameter. Pointer to the string, which is allocated by **malloc()** and must be released via **free()** after use.|
| ... | Input parameter, which is optional. Variable parameter list, which is used for string formatting. The following types are supported: const char*, int, and float.<br>     You do not need to set this parameter when obtaining a plain string. This parameter is mandatory to obtain a formatted string. The variable parameters must be passed in the order corresponding to the placeholders in the string. The number and types of the parameters must match the placeholders in the string. For example, if the string contains three placeholders %d, %s, and %f, the API should be called as follows: **OH_ResourceManager_GetString(mgr, resId, resultValue, 10, "format", 10.10)**.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_ID_NOT_FOUND**: Invalid resource ID.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_ID**: No matching resource is found based on the resource ID.<br>     **ERROR_CODE_RES_REF_TOO_MUCH**: The resource has a circular reference.<br>     **ERROR_CODE_OUT_OF_MEMORY**: Memory overflow occurs.|

### OH_ResourceManager_GetStringByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetStringByName(const NativeResourceManager *mgr, const char *resName, char **resultValue, ...)
```

**Description**

Obtains a plain or formatted string based on the specified resource name.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| const char *resName | Input parameter. Resource name.|
| char **resultValue | Output parameter. Pointer to the string, which is allocated by **malloc()** and must be released via **free()** after use.|
| ... | Input parameter, which is optional. Variable parameter list, which is used for string formatting. The following types are supported: const char*, int, and float.<br>     You do not need to set this parameter when obtaining a plain string. This parameter is mandatory to obtain a formatted string. The variable parameters must be passed in the order corresponding to the placeholders in the string. The number and types of the parameters must match the placeholders in the string. For example, if the string contains three placeholders %d, %s, and %f, the API should be called as follows: **OH_ResourceManager_GetStringByName(mgr, resName, resultValue, 10, "format", 10.10)**.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_NAME_NOT_FOUND**: Invalid resource name.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_NAME**: No matching resource is found based on the resource name.<br>     **ERROR_CODE_RES_REF_TOO_MUCH**: The resource has a circular reference.<br>     **ERROR_CODE_OUT_OF_MEMORY**: Memory overflow occurs.|

### OH_ResourceManager_GetStringArray()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetStringArray(const NativeResourceManager *mgr, uint32_t resId, char ***resultValue, uint32_t *resultLen)
```

**Description**

Obtains the string array based on the specified resource ID.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| uint32_t resId | Input parameter. Resource ID.|
| char ***resultValue | Output parameter. Pointer to the string array. The memory is allocated by this function and must be released through [OH_ResourceManager_ReleaseStringArray](capi-ohresmgr-h.md#oh_resourcemanager_releasestringarray) after use.|
| uint32_t *resultLen | Output parameter. Length of the string array.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_ID_NOT_FOUND**: Invalid resource ID.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_ID**: No matching resource is found based on the resource ID.<br>     **ERROR_CODE_RES_REF_TOO_MUCH**: The resource has a circular reference.<br>     **ERROR_CODE_OUT_OF_MEMORY**: Memory overflow occurs.|

### OH_ResourceManager_GetStringArrayByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetStringArrayByName(const NativeResourceManager *mgr, const char *resName, char ***resultValue, uint32_t *resultLen)
```

**Description**

Obtains the string array based on the specified resource name.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| const char *resName | Input parameter. Resource name.|
| char ***resultValue | Output parameter. Pointer to the string array. The memory is allocated by this function and must be released through [OH_ResourceManager_ReleaseStringArray](capi-ohresmgr-h.md#oh_resourcemanager_releasestringarray) after use.|
| uint32_t *resultLen | Output parameter. Length of the string array.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_NAME_NOT_FOUND**: Invalid resource name.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_NAME**: No matching resource is found based on the resource name.<br>     **ERROR_CODE_RES_REF_TOO_MUCH**: The resource has a circular reference.<br>     **ERROR_CODE_OUT_OF_MEMORY**: Memory overflow occurs.|

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
| char ***resValue | Input parameter. Pointer to the string array to be released.|
| uint32_t len | Input parameter. Length of the string array.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.|

### OH_ResourceManager_GetPluralString()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetPluralString(const NativeResourceManager *mgr, uint32_t resId, uint32_t num, char **resultValue)
```

**Description**

Obtains the plural string based on the specified resource ID.<br> The Chinese language does not distinguish between singular and plural forms in strings, whereas other languages do. For details about the specific rules, see [language plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In languages such as English and German, plural categories include cardinal forms (for example, 1, 2, 3) and ordinal forms (for example, 1st, 2nd, 3rd). This function applies only to cardinal forms.

**Since**: 12

**Deprecated since**: 16

**Substitute**: [OH_ResourceManager_GetIntPluralString](capi-ohresmgr-h.md#oh_resourcemanager_getintpluralstring)

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| uint32_t resId | Input parameter. Resource ID.|
| uint32_t num | Input parameter. Quantity value, which is used to obtain the corresponding plural string based on the plural rules of the current language.|
| char **resultValue | Output parameter. Pointer to the string. The memory is allocated by **malloc()**, and must be released via **free()**.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_ID_NOT_FOUND**: Invalid resource ID.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_ID**: No matching resource is found based on the resource ID.<br>     **ERROR_CODE_RES_REF_TOO_MUCH**: The resource has a circular reference.<br>     **ERROR_CODE_OUT_OF_MEMORY**: Memory overflow occurs.|

### OH_ResourceManager_GetPluralStringByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetPluralStringByName(const NativeResourceManager *mgr, const char *resName, uint32_t num, char **resultValue)
```

**Description**

Obtains the plural string based on the specified resource name.<br> The Chinese language does not distinguish between singular and plural forms in strings, whereas other languages do. For details about the specific rules, see [language plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In languages such as English and German, plural categories include cardinal forms (for example, 1, 2, 3) and ordinal forms (for example, 1st, 2nd, 3rd). This function applies only to cardinal forms.

**Since**: 12

**Deprecated since**: 16

**Substitute**: [OH_ResourceManager_GetIntPluralStringByName](capi-ohresmgr-h.md#oh_resourcemanager_getintpluralstringbyname)

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| const char *resName | Input parameter. Resource name.|
| uint32_t num | Input parameter. Quantity value, which is used to obtain the corresponding plural string based on the plural rules of the current language.|
| char **resultValue | Output parameter. Pointer to the string. The memory is allocated by **malloc()**, and must be released via **free()**.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_NAME_NOT_FOUND**: Invalid resource name.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_NAME**: No matching resource is found based on the resource name.<br>     **ERROR_CODE_RES_REF_TOO_MUCH**: The resource has a circular reference.<br>     **ERROR_CODE_OUT_OF_MEMORY**: Memory overflow occurs.|

### OH_ResourceManager_GetIntPluralString()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetIntPluralString(const NativeResourceManager *mgr, uint32_t resId, uint32_t num, char **resultValue, ...)
```

**Description**

Obtains the corresponding plural string and formats it based on the specified resource ID, integer quantity, and variable parameters.<br> The Chinese language does not distinguish between singular and plural forms in strings, whereas other languages do. For details about the specific rules, see [language plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In languages such as English and German, plural categories include cardinal forms (for example, 1, 2, 3) and ordinal forms (for example, 1st, 2nd, 3rd). This function applies only to cardinal forms.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| uint32_t resId | Input parameter. Resource ID.|
| uint32_t num | Input parameter. Quantity value (integer), which is used to obtain the corresponding plural string based on the plural rules of the current language.|
| char **resultValue | Output parameter. Pointer to the string. The memory is allocated by **malloc()**, and must be released via **free()**.|
| ... | Input parameter, which is optional. Variable parameter list, which is used for string formatting. The following types are supported: const char*, int, and float.<br>     When obtaining a formatted string, pass the variable parameters in the order corresponding to the placeholders in the string. The number and types of the parameters must match the placeholders in the string. For example, if the string contains three placeholders %d, %s, and %f, the API should be called as follows: **OH_ResourceManager_GetIntPluralString(mgr, resId, 10, resultValue, 10, "format", 10.10)**.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_ID_NOT_FOUND**: Invalid resource ID.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_ID**: No matching resource is found based on the resource ID.<br>     **ERROR_CODE_RES_REF_TOO_MUCH**: The resource has a circular reference.<br>     **ERROR_CODE_OUT_OF_MEMORY**: Memory overflow occurs.|

### OH_ResourceManager_GetIntPluralStringByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetIntPluralStringByName(const NativeResourceManager *mgr, const char *resName, uint32_t num, char **resultValue, ...)
```

**Description**

Obtains the corresponding plural string and formats it based on the specified resource name, integer quantity, and variable parameters.<br> The Chinese language does not distinguish between singular and plural forms in strings, whereas other languages do. For details about the specific rules, see [language plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In languages such as English and German, plural categories include cardinal forms (for example, 1, 2, 3) and ordinal forms (for example, 1st, 2nd, 3rd). This function applies only to cardinal forms.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| const char *resName | Input parameter. Resource name.|
| uint32_t num | Input parameter. Quantity value (integer), which is used to obtain the corresponding plural string based on the plural rules of the current language.|
| char **resultValue | Output parameter. Pointer to the string. The memory is allocated by **malloc()**, and must be released via **free()**.|
| ... | Input parameter, which is optional. Variable parameter list, which is used for string formatting. The following types are supported: const char*, int, and float.<br>     When obtaining a formatted string, pass the variable parameters in the order corresponding to the placeholders in the string. The number and types of the parameters must match the placeholders in the string. For example, if the string contains three placeholders %d, %s, and %f, the API should be called as follows: **OH_ResourceManager_GetIntPluralStringByName(mgr, resName, 10, resultValue, 10, "format", 10.10)**.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_NAME_NOT_FOUND**: Invalid resource name.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_NAME**: No matching resource is found based on the resource name.<br>     **ERROR_CODE_RES_REF_TOO_MUCH**: The resource has a circular reference.<br>     **ERROR_CODE_OUT_OF_MEMORY**: Memory overflow occurs.|

### OH_ResourceManager_GetDoublePluralString()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetDoublePluralString(const NativeResourceManager *mgr, uint32_t resId, double num, char **resultValue, ...)
```

**Description**

Obtains the corresponding plural string and formats it based on the specified resource ID, floating-point quantity, and variable parameters.<br> The Chinese language does not distinguish between singular and plural forms in strings, whereas other languages do. For details about the specific rules, see [language plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In languages such as English and German, plural categories include cardinal forms (for example, 1, 2, 3) and ordinal forms (for example, 1st, 2nd, 3rd). This function applies only to cardinal forms.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| uint32_t resId | Input parameter. Resource ID.|
| double num | Input parameter. Quantity value (floating-point), which is used to obtain the corresponding plural string based on the plural rules of the current language.|
| char **resultValue | Output parameter. Pointer to the string. The memory is allocated by **malloc()**, and must be released via **free()**.|
| ... | Input parameter, which is optional. Variable parameter list, which is used for string formatting. The following types are supported: const char*, int, and float.<br>     When obtaining a formatted string, pass the variable parameters in the order corresponding to the placeholders in the string. The number and types of the parameters must match the placeholders in the string. For example, if the string contains three placeholders %d, %s, and %f, the API should be called as follows: **OH_ResourceManager_GetDoublePluralString(mgr, resId, 1.1, resultValue, 10, "format", 10.10)**.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_ID_NOT_FOUND**: Invalid resource ID.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_ID**: No matching resource is found based on the resource ID.<br>     **ERROR_CODE_RES_REF_TOO_MUCH**: The resource has a circular reference.<br>     **ERROR_CODE_OUT_OF_MEMORY**: Memory overflow occurs.|

### OH_ResourceManager_GetDoublePluralStringByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetDoublePluralStringByName(const NativeResourceManager *mgr, const char *resName, double num, char **resultValue, ...)
```

**Description**

Obtains the corresponding plural string and formats it based on the specified resource name, floating-point quantity, and variable parameters.<br> The Chinese language does not distinguish between singular and plural forms in strings, whereas other languages do. For details about the specific rules, see [language plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).<br> In languages such as English and German, plural categories include cardinal forms (for example, 1, 2, 3) and ordinal forms (for example, 1st, 2nd, 3rd). This function applies only to cardinal forms.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| const char *resName | Input parameter. Resource name.|
| double num | Input parameter. Quantity value (floating-point), which is used to obtain the corresponding plural string based on the plural rules of the current language.|
| char **resultValue | Output parameter. Pointer to the string. The memory is allocated by **malloc()**, and must be released via **free()**.|
| ... | Input parameter, which is optional. Variable parameter list, which is used for string formatting. The following types are supported: const char*, int, and float.<br>     When obtaining a formatted string, pass the variable parameters in the order corresponding to the placeholders in the string. The number and types of the parameters must match the placeholders in the string. For example, if the string contains three placeholders %d, %s, and %f, the API should be called as follows: **OH_ResourceManager_GetDoublePluralStringByName(mgr, resName, 1.1, resultValue, 10, "format", 10.10)**.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_NAME_NOT_FOUND**: Invalid resource name.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_NAME**: No matching resource is found based on the resource name.<br>     **ERROR_CODE_RES_REF_TOO_MUCH**: The resource has a circular reference.<br>     **ERROR_CODE_OUT_OF_MEMORY**: Memory overflow occurs.|

### OH_ResourceManager_GetColor()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetColor(const NativeResourceManager *mgr, uint32_t resId, uint32_t *resultValue)
```

**Description**

Obtains the color resource value based on the specified resource ID.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| uint32_t resId | Input parameter. Resource ID.|
| uint32_t *resultValue | Output parameter. Color resource value.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_ID_NOT_FOUND**: Invalid resource ID.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_ID**: No matching resource is found based on the resource ID.<br>     **ERROR_CODE_RES_REF_TOO_MUCH**: The resource has a circular reference.|

### OH_ResourceManager_GetColorByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetColorByName(const NativeResourceManager *mgr, const char *resName, uint32_t *resultValue)
```

**Description**

Obtains the color resource value based on the specified resource name.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| const char *resName | Input parameter. Resource name.|
| uint32_t *resultValue | Output parameter. Color resource value.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_NAME_NOT_FOUND**: Invalid resource name.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_NAME**: No matching resource is found based on the resource name.<br>     **ERROR_CODE_RES_REF_TOO_MUCH**: The resource has a circular reference.|

### OH_ResourceManager_GetInt()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetInt(const NativeResourceManager *mgr, uint32_t resId, int *resultValue)
```

**Description**

Obtains the integer resource value based on the specified resource ID.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| uint32_t resId | Input parameter. Resource ID.|
| int *resultValue | Output parameter. Integer resource value.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_ID_NOT_FOUND**: Invalid resource ID.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_ID**: No matching resource is found based on the resource ID.<br>     **ERROR_CODE_RES_REF_TOO_MUCH**: The resource has a circular reference.|

### OH_ResourceManager_GetIntByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetIntByName(const NativeResourceManager *mgr, const char *resName, int *resultValue)
```

**Description**

Obtains the integer resource value based on the specified resource name.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| const char *resName | Input parameter. Resource name.|
| int *resultValue | Output parameter. Integer resource value.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_NAME_NOT_FOUND**: Invalid resource name.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_NAME**: No matching resource is found based on the resource name.<br>     **ERROR_CODE_RES_REF_TOO_MUCH**: The resource has a circular reference.|

### OH_ResourceManager_GetFloat()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetFloat(const NativeResourceManager *mgr, uint32_t resId, float *resultValue)
```

**Description**

Obtains the floating-point resource value based on the specified resource ID.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| uint32_t resId | Input parameter. Resource ID.|
| float *resultValue | Output parameter. Floating-point resource value.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_ID_NOT_FOUND**: Invalid resource ID.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_ID**: No matching resource is found based on the resource ID.<br>     **ERROR_CODE_RES_REF_TOO_MUCH**: The resource has a circular reference.|

### OH_ResourceManager_GetFloatByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetFloatByName(const NativeResourceManager *mgr, const char *resName, float *resultValue)
```

**Description**

Obtains the floating-point resource value based on the specified resource name.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| const char *resName | Input parameter. Resource name.|
| float *resultValue | Output parameter. Floating-point resource value.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_NAME_NOT_FOUND**: Invalid resource name.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_NAME**: No matching resource is found based on the resource name.<br>     **ERROR_CODE_RES_REF_TOO_MUCH**: The resource has a circular reference.|

### OH_ResourceManager_GetBool()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetBool(const NativeResourceManager *mgr, uint32_t resId, bool *resultValue)
```

**Description**

Obtains the Boolean resource value based on the specified resource ID.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| uint32_t resId | Input parameter. Resource ID.|
| bool *resultValue | Output parameter. Boolean resource value.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_ID_NOT_FOUND**: Invalid resource ID.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_ID**: No matching resource is found based on the resource ID.<br>     **ERROR_CODE_RES_REF_TOO_MUCH**: The resource has a circular reference.|

### OH_ResourceManager_GetBoolByName()

```c
ResourceManager_ErrorCode OH_ResourceManager_GetBoolByName(const NativeResourceManager *mgr, const char *resName, bool *resultValue)
```

**Description**

Obtains the Boolean resource value based on the specified resource name.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| const char *resName | Input parameter. Resource name.|
| bool *resultValue | Output parameter. Boolean resource value.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_RES_NAME_NOT_FOUND**: Invalid resource name.<br>     **ERROR_CODE_RES_NOT_FOUND_BY_NAME**: No matching resource is found based on the resource name.<br>     **ERROR_CODE_RES_REF_TOO_MUCH**: The resource has a circular reference.|

### OH_ResourceManager_AddResource()

```c
ResourceManager_ErrorCode OH_ResourceManager_AddResource(const NativeResourceManager *mgr, const char *path)
```

**Description**

Dynamically loads overlay resources during application runtime to implement theme switching or resource overriding.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| const char *path | Input parameter. Absolute path of the HSP or HAP resource package to be loaded.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_OVERLAY_RES_PATH_INVALID**: Invalid overlay path.|

### OH_ResourceManager_RemoveResource()

```c
ResourceManager_ErrorCode OH_ResourceManager_RemoveResource(const NativeResourceManager *mgr, const char *path)
```

**Description**

Removes the specified overlay resource during application runtime and restores the original resource before the override.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const NativeResourceManager](capi-rawfile-nativeresourcemanager.md) *mgr | Input parameter. Pointer to the NativeResourceManager object. The pointer is obtained through [OH_ResourceManager_InitNativeResourceManager](capi-raw-file-manager-h.md#oh_resourcemanager_initnativeresourcemanager).|
| const char *path | Input parameter. Absolute path of the HSP or HAP resource package to be removed.|

**Returns**

| Type| Description|
| -- | -- |
| [ResourceManager_ErrorCode](capi-resmgr-common-h.md#resourcemanager_errorcode) | Result code.<br>     **SUCCESS**: Success.<br>     **ERROR_CODE_INVALID_INPUT_PARAMETER**: Invalid input parameter. Possible causes: 1. The parameter type is incorrect. 2. Parameter verification failed.<br>     **ERROR_CODE_OVERLAY_RES_PATH_INVALID**: Invalid overlay path.|
