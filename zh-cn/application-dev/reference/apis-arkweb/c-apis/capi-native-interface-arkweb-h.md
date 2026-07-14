# native_interface_arkweb.h

## 概述

Declares the APIs to use javascript proxy and run javascript code.

**库：** libohweb.so

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 11

**相关模块：** [Web](capi-web.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkWeb_BlanklessInfo](capi-web-arkweb-blanklessinfo.md) | ArkWeb_BlanklessInfo | Describes prediction information about blankless loading, including the first screen similarity, first screenloading duration, and error codes. The application determines whether to enable the blankless loading solution basedon the prediction information. |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkWebEngineVersion](#arkwebengineversion) | ArkWebEngineVersion | ArkWeb内核版本，请参考[M114内核在OpenHarmony 6.0系统上的适配指导](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/web/ReleaseNote/CompatibleWithLegacyWebEngine_6.0.md)，[M132内核在OpenHarmony 7.0系统上的适配指导](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/web/ReleaseNote/CompatibleWithLegacyWebEngine_7.0.md)。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*NativeArkWeb_OnJavaScriptCallback)(const char*)](#nativearkweb_onjavascriptcallback) | NativeArkWeb_OnJavaScriptCallback | Defines the javascript callback of the web component. |
| [typedef char* (\*NativeArkWeb_OnJavaScriptProxyCallback)(const char** argv, int32_t argc)](#nativearkweb_onjavascriptproxycallback) | NativeArkWeb_OnJavaScriptProxyCallback | Defines the javascript proxy callback of the web component. |
| [typedef void (\*NativeArkWeb_OnValidCallback)(const char*)](#nativearkweb_onvalidcallback) | NativeArkWeb_OnValidCallback | Defines the valid callback of the web component. |
| [typedef void (\*NativeArkWeb_OnDestroyCallback)(const char*)](#nativearkweb_ondestroycallback) | NativeArkWeb_OnDestroyCallback | Defines the destroy callback of the web component. |
| [typedef void (\*OH_ArkWeb_OnCookieSaveCallback)(ArkWeb_ErrorCode errorCode)](#oh_arkweb_oncookiesavecallback) | OH_ArkWeb_OnCookieSaveCallback | Defines the callback of save cookie. |
| [void OH_NativeArkWeb_RunJavaScript(const char* webTag, const char* jsCode, NativeArkWeb_OnJavaScriptCallback callback)](#oh_nativearkweb_runjavascript) | - | Loads a piece of code and execute JS code in the context of the currently displayed page. |
| [void OH_NativeArkWeb_RegisterJavaScriptProxy(const char* webTag, const char* objName, const char** methodList, NativeArkWeb_OnJavaScriptProxyCallback* callback, int32_t size, bool needRefresh)](#oh_nativearkweb_registerjavascriptproxy) | - | Registers the JavaScript object and method list. |
| [void OH_NativeArkWeb_UnregisterJavaScriptProxy(const char* webTag, const char* objName)](#oh_nativearkweb_unregisterjavascriptproxy) | - | Deletes the registered object which th given name. |
| [void OH_NativeArkWeb_SetJavaScriptProxyValidCallback(const char* webTag, NativeArkWeb_OnValidCallback callback)](#oh_nativearkweb_setjavascriptproxyvalidcallback) | - | Registers the valid callback. |
| [NativeArkWeb_OnValidCallback OH_NativeArkWeb_GetJavaScriptProxyValidCallback(const char* webTag)](#oh_nativearkweb_getjavascriptproxyvalidcallback) | - | Get the valid callback. |
| [void OH_NativeArkWeb_SetDestroyCallback(const char* webTag, NativeArkWeb_OnDestroyCallback callback)](#oh_nativearkweb_setdestroycallback) | - | Registers the destroy callback. |
| [NativeArkWeb_OnDestroyCallback OH_NativeArkWeb_GetDestroyCallback(const char* webTag)](#oh_nativearkweb_getdestroycallback) | - | Get the destroy callback. |
| [ArkWeb_ErrorCode OH_NativeArkWeb_LoadData(const char* webTag, const char* data, const char* mimeType, const char* encoding, const char* baseUrl, const char* historyUrl)](#oh_nativearkweb_loaddata) | - | Loads the data or URL.This function should be called on main thread. |
| [void OH_NativeArkWeb_RegisterAsyncThreadJavaScriptProxy(const char* webTag, const ArkWeb_ProxyObjectWithResult* proxyObject, const char* permission)](#oh_nativearkweb_registerasyncthreadjavascriptproxy) | - | Registers a JavaScript object with callback methods, which may return values. This object will be injectedinto all frames of the current page, including all iframes, and will be accessible using the specifiedname in ArkWeb_ProxyObjectWithResult. The object will only be available in JavaScript after the nextload or reload.These methods will be executed in the ArkWeb worker thread. |
| [ArkWeb_BlanklessErrorCode OH_NativeArkWeb_SetBlanklessLoadingWithKey(const char* webTag, const char* key, bool isStarted)](#oh_nativearkweb_setblanklessloadingwithkey) | - | Sets whether to enable blankless loading. This API must be used together with the [OH_NativeArkWeb_GetBlanklessInfoWithKey](capi-native-interface-arkweb-h.md#oh_nativearkweb_getblanklessinfowithkey)API. |
| [void OH_NativeArkWeb_ClearBlanklessLoadingCache(const char* key[], uint32_t size)](#oh_nativearkweb_clearblanklessloadingcache) | - | Clears the blankless loading cache of the page with a specified key value. |
| [ArkWeb_BlanklessInfo OH_NativeArkWeb_GetBlanklessInfoWithKey(const char* webTag, const char* key)](#oh_nativearkweb_getblanklessinfowithkey) | - | Obtains the first screen loading prediction information, and starts to generate the loading transition frame.The application determines whether to enable blankless loading based on the information. For details, see [ArkWeb_BlanklessInfo](capi-web-arkweb-blanklessinfo.md). This API must be used together with the [OH_NativeArkWeb_SetBlanklessLoadingWithKey](capi-native-interface-arkweb-h.md#oh_nativearkweb_setblanklessloadingwithkey) API and must be calledbefore the page loading API is triggered and after **WebViewController** is bound to the **Web** component. |
| [uint32_t OH_NativeArkWeb_SetBlanklessLoadingCacheCapacity(uint32_t capacity)](#oh_nativearkweb_setblanklessloadingcachecapacity) | - | Sets the persistent cache capacity of the blankless loading solution and returns the value that takes effect.The default cache capacity is 30 MB, and the maximum cache capacity is 100 MB. When this limit is exceeded,transition frames that are not frequently used are eliminated. |
| [ArkWeb_ErrorCode OH_ArkWebCookieManager_SaveCookieSync()](#oh_arkwebcookiemanager_savecookiesync) | - | Ensure that all cookies currently accessible via the CookieManager API have been persisted to disk.If you want to use this interface in a non-UI thread, you need to initialize the CookieManager interfaceusing OH_ArkWeb_GetNativeAPI first. |
| [void OH_ArkWebCookieManager_SaveCookieAsync(OH_ArkWeb_OnCookieSaveCallback callback)](#oh_arkwebcookiemanager_savecookieasync) | - | Ensure that all cookies currently accessible via the CookieManager API have been persisted to disk.Without initializing the CookieManager interface, this call will automatically be executed on the UI thread. |
| [void OH_NativeArkWeb_SetActiveWebEngineVersion(ArkWebEngineVersion webEngineVersion)](#oh_nativearkweb_setactivewebengineversion) | - |  |
| [ArkWebEngineVersion OH_NativeArkWeb_GetActiveWebEngineVersion()](#oh_nativearkweb_getactivewebengineversion) | - |  |
| [void OH_NativeArkWeb_LazyInitializeWebEngineInCookieManager(bool lazy)](#oh_nativearkweb_lazyinitializewebengineincookiemanager) | - |  |
| [bool OH_NativeArkWeb_IsActiveWebEngineEvergreen()](#oh_nativearkweb_isactivewebengineevergreen) | - |  |

## 枚举类型说明

### ArkWebEngineVersion

```c
enum ArkWebEngineVersion
```

**描述**

ArkWeb内核版本，请参考[M114内核在OpenHarmony 6.0系统上的适配指导](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/web/ReleaseNote/CompatibleWithLegacyWebEngine_6.0.md)，[M132内核在OpenHarmony 7.0系统上的适配指导](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/web/ReleaseNote/CompatibleWithLegacyWebEngine_7.0.md)。

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| SYSTEM_DEFAULT = 0 | 系统默认内核，OpenHarmony 6.0版本默认为M132，OpenHarmony 7.0版本默认为M144。<br>**起始版本：** 20 |
| ARKWEB_M114 = 1 | OpenHarmony 6.0版本的遗留内核。开发者可选择此遗留内核，若系统版本上不存在此内核则设置无效。<br>**起始版本：** 20 |
| ARKWEB_M132 = 2 | OpenHarmony 6.0版本的常青内核（OpenHarmony 7.0版本的遗留内核），M132为OpenHarmony 6.0版本的默认内核。若系统版本上不存在此内核则设置无效。<br>**起始版本：** 20 |
| ARKWEB_M144 = 3 | OpenHarmony 7.0版本的[常青内核]，M144为此版本的默认内核。若系统版本上不存在此内核则设置无效。<br>**起始版本：** 26.0.0 |
| ARKWEB_EVERGREEN = 99999 | 常青内核，系统的最新内核。开发者可选择在每个系统版本上都使用最新的内核，OpenHarmony 6.1及之后所有系统版本都生效。<br>**起始版本：** 23 |


## 函数说明

### NativeArkWeb_OnJavaScriptCallback()

```c
typedef void (*NativeArkWeb_OnJavaScriptCallback)(const char*)
```

**描述**

Defines the javascript callback of the web component.

**起始版本：** 11

### NativeArkWeb_OnJavaScriptProxyCallback()

```c
typedef char* (*NativeArkWeb_OnJavaScriptProxyCallback)(const char** argv, int32_t argc)
```

**描述**

Defines the javascript proxy callback of the web component.

**起始版本：** 11

### NativeArkWeb_OnValidCallback()

```c
typedef void (*NativeArkWeb_OnValidCallback)(const char*)
```

**描述**

Defines the valid callback of the web component.

**起始版本：** 11

### NativeArkWeb_OnDestroyCallback()

```c
typedef void (*NativeArkWeb_OnDestroyCallback)(const char*)
```

**描述**

Defines the destroy callback of the web component.

**起始版本：** 11

### OH_ArkWeb_OnCookieSaveCallback()

```c
typedef void (*OH_ArkWeb_OnCookieSaveCallback)(ArkWeb_ErrorCode errorCode)
```

**描述**

Defines the callback of save cookie.

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (ArkWeb_ErrorCode errorCode | {@link ARKWEB_SUCCESS} Save cookie success.{@link ARKWEB_COOKIE_MANAGER_INITIALIZE_FAILED} Cookie manager initialize failed.{@link ARKWEB_COOKIE_SAVE_FAILED} Save cookie failed. |

### OH_NativeArkWeb_RunJavaScript()

```c
void OH_NativeArkWeb_RunJavaScript(const char* webTag, const char* jsCode, NativeArkWeb_OnJavaScriptCallback callback)
```

**描述**

Loads a piece of code and execute JS code in the context of the currently displayed page.

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | The name of the web component. |
| const char* jsCode | a piece of javascript code. |
| [NativeArkWeb_OnJavaScriptCallback](capi-native-interface-arkweb-h.md#nativearkweb_onjavascriptcallback) callback | Callbacks execute JavaScript script results. |

### OH_NativeArkWeb_RegisterJavaScriptProxy()

```c
void OH_NativeArkWeb_RegisterJavaScriptProxy(const char* webTag, const char* objName, const char** methodList, NativeArkWeb_OnJavaScriptProxyCallback* callback, int32_t size, bool needRefresh)
```

**描述**

Registers the JavaScript object and method list.

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | The name of the web component. |
| const char* objName | The name of the registered object. |
| const char** methodList | The method of the application side JavaScript object participating in the registration. |
| [NativeArkWeb_OnJavaScriptProxyCallback](capi-native-interface-arkweb-h.md#nativearkweb_onjavascriptproxycallback)* callback | The callback function registered by developer is called back when HTML side uses. |
| int32_t size | The size of the callback. |
| bool needRefresh | if web need refresh. |

### OH_NativeArkWeb_UnregisterJavaScriptProxy()

```c
void OH_NativeArkWeb_UnregisterJavaScriptProxy(const char* webTag, const char* objName)
```

**描述**

Deletes the registered object which th given name.

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | The name of the web component. |
| const char* objName | The name of the registered object. |

### OH_NativeArkWeb_SetJavaScriptProxyValidCallback()

```c
void OH_NativeArkWeb_SetJavaScriptProxyValidCallback(const char* webTag, NativeArkWeb_OnValidCallback callback)
```

**描述**

Registers the valid callback.

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | The name of the web component. |
| [NativeArkWeb_OnValidCallback](capi-native-interface-arkweb-h.md#nativearkweb_onvalidcallback) callback | The callback in which we can register object. |

### OH_NativeArkWeb_GetJavaScriptProxyValidCallback()

```c
NativeArkWeb_OnValidCallback OH_NativeArkWeb_GetJavaScriptProxyValidCallback(const char* webTag)
```

**描述**

Get the valid callback.

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | The name of the web component. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeArkWeb_OnValidCallback](capi-native-interface-arkweb-h.md#nativearkweb_onvalidcallback) | Return the valid callback function registered. If the valid callback function<br>         specified by the parameter webTag is not set, a null pointer is returned. |

### OH_NativeArkWeb_SetDestroyCallback()

```c
void OH_NativeArkWeb_SetDestroyCallback(const char* webTag, NativeArkWeb_OnDestroyCallback callback)
```

**描述**

Registers the destroy callback.

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | The name of the web component. |
| [NativeArkWeb_OnDestroyCallback](capi-native-interface-arkweb-h.md#nativearkweb_ondestroycallback) callback | the destroy callback. |

### OH_NativeArkWeb_GetDestroyCallback()

```c
NativeArkWeb_OnDestroyCallback OH_NativeArkWeb_GetDestroyCallback(const char* webTag)
```

**描述**

Get the destroy callback.

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | The name of the web component. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeArkWeb_OnDestroyCallback](capi-native-interface-arkweb-h.md#nativearkweb_ondestroycallback) | Return the destroy callback function registered. If the destroy callback<br>         function specified by the parameter webTag is not set,<br>         a null pointer is returned. |

### OH_NativeArkWeb_LoadData()

```c
ArkWeb_ErrorCode OH_NativeArkWeb_LoadData(const char* webTag, const char* data, const char* mimeType, const char* encoding, const char* baseUrl, const char* historyUrl)
```

**描述**

Loads the data or URL.This function should be called on main thread.

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | The name of the web component. |
| const char* data | A string encoded according to "Base64" or "URL", should not be NULL. |
| const char* mimeType | Media type. For example: "text/html", should not be NULL. |
| const char* encoding | Encoding type. For example: "UTF-8", should not be NULL. |
| const char* baseUrl | A specified URL path ("http"/"https"/"data" protocol),which is assigned to window.origin by the Web component. |
| const char* historyUrl | History URL. When it is not empty, it can be managed byhistory records to realize the back and forth function. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkWeb_ErrorCode | LoadData result code.<br>         {@link ARKWEB_SUCCESS} load data success.<br>         {@link ARKWEB_INVALID_PARAM} Mandatory parameters are left unspecified or<br>                                      Incorrect parameter types or Parameter verification failed.<br>         {@link ARKWEB_INIT_ERROR} Initialization error, can't get a valid Web for the webTag.<br>         {@link ARKWEB_LIBRARY_OPEN_FAILURE} Failed to open the library.<br>         {@link ARKWEB_LIBRARY_SYMBOL_NOT_FOUND} The required symbol was not found in the library. |

### OH_NativeArkWeb_RegisterAsyncThreadJavaScriptProxy()

```c
void OH_NativeArkWeb_RegisterAsyncThreadJavaScriptProxy(const char* webTag, const ArkWeb_ProxyObjectWithResult* proxyObject, const char* permission)
```

**描述**

Registers a JavaScript object with callback methods, which may return values. This object will be injectedinto all frames of the current page, including all iframes, and will be accessible using the specifiedname in ArkWeb_ProxyObjectWithResult. The object will only be available in JavaScript after the nextload or reload.These methods will be executed in the ArkWeb worker thread.

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | Name of the web component. |
| const ArkWeb_ProxyObjectWithResult* proxyObject | JavaScript object to register, the object has callback functions with return value. |
| const char* permission | Optional JSON string(default is null) for JSBridge permission control,allowing URL whitelist configuration at object-level and method-level. |

### OH_NativeArkWeb_SetBlanklessLoadingWithKey()

```c
ArkWeb_BlanklessErrorCode OH_NativeArkWeb_SetBlanklessLoadingWithKey(const char* webTag, const char* key, bool isStarted)
```

**描述**

Sets whether to enable blankless loading. This API must be used together with the [OH_NativeArkWeb_GetBlanklessInfoWithKey](capi-native-interface-arkweb-h.md#oh_nativearkweb_getblanklessinfowithkey)API.

**需要权限：** ohos.permission.INTERNET and ohos.permission.GET_NETWORK_INFO

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | Name of the **Web** component. |
| const char* key | Key value that uniquely identifies the page. The value must be the same as the key value of the [OH_NativeArkWeb_GetBlanklessInfoWithKey](capi-native-interface-arkweb-h.md#oh_nativearkweb_getblanklessinfowithkey)API.The value cannot be empty and can contain a maximum of 2048 characters.When an invalid value is set, the error code {@link ArkWeb_BlanklessErrorCode} is returned and the frame insertiondoes not take effect. |
| bool isStarted | Whether to enable frame insertion. The value **true** indicates to enable frame insertion, and false** indicates the opposite.The default value is **false**. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkWeb_BlanklessErrorCode | Whether the API is successfully called. For details, see {@link ArkWeb_BlanklessErrorCode}. |

### OH_NativeArkWeb_ClearBlanklessLoadingCache()

```c
void OH_NativeArkWeb_ClearBlanklessLoadingCache(const char* key[], uint32_t size)
```

**描述**

Clears the blankless loading cache of the page with a specified key value.

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* key[] | The list of key values of pages cached in the blankless loading solution. These key values arespecified in OH_NativeArkWeb_GetBlanklessInfoWithKey.The default value is the list of key values of all pages cached in the blankless loading solution.The key length cannot exceed 2048 characters, and the number of keys must be less than or equal to 100. TheURL is the same as that input to the Web component during page loading.When the key length exceeds 2048 characters, the key does not take effect. When the number of keys exceeds100, the first 100 keys are used. If this parameter is set to NULL, the default value is used. |
| uint32_t size | Size of the key array.The default value is **0**.The value ranges from 0 to 100. If the size exceeds 100, the first 100 keys are used.When an invalid value is set, the value **0** is used. |

### OH_NativeArkWeb_GetBlanklessInfoWithKey()

```c
ArkWeb_BlanklessInfo OH_NativeArkWeb_GetBlanklessInfoWithKey(const char* webTag, const char* key)
```

**描述**

Obtains the first screen loading prediction information, and starts to generate the loading transition frame.The application determines whether to enable blankless loading based on the information. For details, see [ArkWeb_BlanklessInfo](capi-web-arkweb-blanklessinfo.md). This API must be used together with the [OH_NativeArkWeb_SetBlanklessLoadingWithKey](capi-native-interface-arkweb-h.md#oh_nativearkweb_setblanklessloadingwithkey) API and must be calledbefore the page loading API is triggered and after **WebViewController** is bound to the **Web** component.

**需要权限：** ohos.permission.INTERNET and ohos.permission.GET_NETWORK_INFO

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | Name of the **Web** component. |
| const char* key | Key value that uniquely identifies the page.The value cannot be empty and can contain a maximum of 2048 characters.Invalid values do not take effect. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkWeb_BlanklessInfo](capi-web-arkweb-blanklessinfo.md) | Prediction information about blankless loading, including the first screen similarity and first screen<br> loading duration. The application determines whether to enable blankless loading based on the prediction information. |

### OH_NativeArkWeb_SetBlanklessLoadingCacheCapacity()

```c
uint32_t OH_NativeArkWeb_SetBlanklessLoadingCacheCapacity(uint32_t capacity)
```

**描述**

Sets the persistent cache capacity of the blankless loading solution and returns the value that takes effect.The default cache capacity is 30 MB, and the maximum cache capacity is 100 MB. When this limit is exceeded,transition frames that are not frequently used are eliminated.

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint32_t capacity | Persistent cache capacity, in MB. The maximum value is 100 MB.The default value is 30 MB.The value ranges from 0 to 100. If this parameter is set to **0**, no cache capacity is available and thefunctionality is disabled globally.When a value less than 0 is set, the value **0** takes effect. When a value greater than 100 is set, the value **100* takes effect. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | The effective value that ranges from 0 MB to 100 MB.<br> When a value less than 0 is set, the value 0 takes effect. When a value greater than 100 is set, the value 100<br>  takes effect. |

### OH_ArkWebCookieManager_SaveCookieSync()

```c
ArkWeb_ErrorCode OH_ArkWebCookieManager_SaveCookieSync()
```

**描述**

Ensure that all cookies currently accessible via the CookieManager API have been persisted to disk.If you want to use this interface in a non-UI thread, you need to initialize the CookieManager interfaceusing OH_ArkWeb_GetNativeAPI first.

**起始版本：** 20

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkWeb_ErrorCode | Save cookie result code.<br>         {@link ARKWEB_SUCCESS} Save cookie success.<br>         {@link ARKWEB_COOKIE_SAVE_FAILED} Save cookie failed.<br>         {@link ARKWEB_COOKIE_MANAGER_INITIALIZE_FAILED} The CookieManager initialize failed.<br>         {@link ARKWEB_COOKIE_MANAGER_NOT_INITIALIZED} It is not allowed to call on a non-UI thread without<br>                                                       initializing the CookieManager interface. please<br>   													 initialize the CookieManager interface using<br>  													 OH_ArkWeb_GetNativeAPI first. |

### OH_ArkWebCookieManager_SaveCookieAsync()

```c
void OH_ArkWebCookieManager_SaveCookieAsync(OH_ArkWeb_OnCookieSaveCallback callback)
```

**描述**

Ensure that all cookies currently accessible via the CookieManager API have been persisted to disk.Without initializing the CookieManager interface, this call will automatically be executed on the UI thread.

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkWeb_OnCookieSaveCallback](capi-native-interface-arkweb-h.md#oh_arkweb_oncookiesavecallback) callback | Callback execute when save cookie done. |

### OH_NativeArkWeb_SetActiveWebEngineVersion()

```c
void OH_NativeArkWeb_SetActiveWebEngineVersion(ArkWebEngineVersion webEngineVersion)
```

**描述**

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| { | ArkWebEngineVersion } webEngineVersion - ArkWeb内核版本 （详细说明见[ArkWebEngineVersion](capi-native-interface-arkweb-h.md#arkwebengineversion))。 |

### OH_NativeArkWeb_GetActiveWebEngineVersion()

```c
ArkWebEngineVersion OH_NativeArkWeb_GetActiveWebEngineVersion()
```

**描述**

**起始版本：** 20

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkWebEngineVersion](capi-native-interface-arkweb-h.md#arkwebengineversion) | 返回由[ArkWebEngineVersion](capi-native-interface-arkweb-h.md#arkwebengineversion)枚举所定义的当前使用的ArkWeb内核版本。 |

### OH_NativeArkWeb_LazyInitializeWebEngineInCookieManager()

```c
void OH_NativeArkWeb_LazyInitializeWebEngineInCookieManager(bool lazy)
```

**描述**

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| { | bool } lazy - Controls whether to delay the initialization of the web engine. |

### OH_NativeArkWeb_IsActiveWebEngineEvergreen()

```c
bool OH_NativeArkWeb_IsActiveWebEngineEvergreen()
```

**描述**

**起始版本：** 23

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 表示当前应用所使用内核是否为常青内核。true表示当前应用所使用内核是常青内核，false表示当前应用所使用内核不是常青内核。 |


