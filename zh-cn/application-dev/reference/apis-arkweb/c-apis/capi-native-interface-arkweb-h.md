# native_interface_arkweb.h

## 概述

native_interface_arkweb.h是ArkWeb Native API的核心入口头文件，定义了应用与ArkWeb引擎交互所需的枚举、结构体和NDK函数接口，涵盖JavaScript执行与代理注入、Cookie管理、无白屏加载控制、内核版本选择等功能。该模块适用于需要通过Native方式与Web组件进行深度交互的场景，解决了ArkWeb组件的复杂能力（如JavaScript双向通信、Cookie持久化、内核版本切换）在ArkTS层无法直接调用的技术难题，为开发者提供了完整的底层控制能力，能够实现高性能、可定制的Web组件功能。

**库：** libohweb.so

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 11

**相关模块：** [Web](capi-web.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkWeb_BlanklessInfo](capi-web-arkweb-blanklessinfo.md) | ArkWeb_BlanklessInfo | 页面首屏加载预测信息，主要包括首屏相似度预测值、首屏加载耗时预测值、错误码，应用需根据此信息来决策是否启用无白屏加载插帧方案（该方案通过在页面加载过程中插入预渲染帧来减少白屏时间）。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkWebEngineVersion](#arkwebengineversion) | ArkWebEngineVersion | ArkWeb内核版本，请参考{@link M114内核在OpenHarmony 6.0系统上的适配指导}，{@link M132内核在OpenHarmony 7.0系统上的适配指导}。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*NativeArkWeb_OnJavaScriptCallback)(const char*)](#nativearkweb_onjavascriptcallback) | NativeArkWeb_OnJavaScriptCallback | 定义执行JavaScript代码后返回结果的回调函数的类型。 |
| [typedef char* (\*NativeArkWeb_OnJavaScriptProxyCallback)(const char** argv, int32_t argc)](#nativearkweb_onjavascriptproxycallback) | NativeArkWeb_OnJavaScriptProxyCallback | 定义注入对象的回调函数的类型。 |
| [typedef void (\*NativeArkWeb_OnValidCallback)(const char*)](#nativearkweb_onvalidcallback) | NativeArkWeb_OnValidCallback | 定义Web组件可用时的回调函数的类型。 |
| [typedef void (\*NativeArkWeb_OnDestroyCallback)(const char*)](#nativearkweb_ondestroycallback) | NativeArkWeb_OnDestroyCallback | 定义Web组件销毁时的回调函数的类型。 |
| [typedef void (\*OH_ArkWeb_OnCookieSaveCallback)(ArkWeb_ErrorCode errorCode)](#oh_arkweb_oncookiesavecallback) | OH_ArkWeb_OnCookieSaveCallback | 定义保存cookie的回调函数的类型。 |
| [typedef void (\*OH_ArkWeb_OnCookieFetchCallback)(ArkWeb_ErrorCode errorCode, char* cookieValue)](#oh_arkweb_oncookiefetchcallback) | OH_ArkWeb_OnCookieFetchCallback | 定义在获取cookie操作完成时调用的回调函数类型。 |
| [void OH_NativeArkWeb_RunJavaScript(const char* webTag, const char* jsCode, NativeArkWeb_OnJavaScriptCallback callback)](#oh_nativearkweb_runjavascript) | - | 在当前显示页面的环境下，加载并异步执行一段JavaScript代码。此函数应在主线程中调用。**使用场景**：需要在Native层动态修改页面内容、获取页面运行时信息、与页面JavaScript交互时使用，例如获取表单数据、执行自定义脚本等。 |
| [void OH_NativeArkWeb_RegisterJavaScriptProxy(const char* webTag, const char* objName, const char** methodList, NativeArkWeb_OnJavaScriptProxyCallback* callback, int32_t size, bool needRefresh)](#oh_nativearkweb_registerjavascriptproxy) | - | 注册对象及函数名称列表，用于向Web页面注入Native对象，实现应用侧与前端页面的双向通信。用于Web页面调用Native功能、Native代码控制Web页面行为、混合应用中的跨层交互等场景。 |
| [void OH_NativeArkWeb_UnregisterJavaScriptProxy(const char* webTag, const char* objName)](#oh_nativearkweb_unregisterjavascriptproxy) | - | 删除已注册的对象及其下的回调函数，用于清理不再需要的JavaScript注入对象。典型使用场景：页面销毁时清理注入对象、功能模块卸载时移除对应的Native接口、防止内存泄漏等场景。 |
| [void OH_NativeArkWeb_SetJavaScriptProxyValidCallback(const char* webTag, NativeArkWeb_OnValidCallback callback)](#oh_nativearkweb_setjavascriptproxyvalidcallback) | - | 设置对象可注册时的回调函数。需要在JavaScript代理对象成功注册后执行特定逻辑时使用，例如注册成功后通知页面或记录日志。 |
| [NativeArkWeb_OnValidCallback OH_NativeArkWeb_GetJavaScriptProxyValidCallback(const char* webTag)](#oh_nativearkweb_getjavascriptproxyvalidcallback) | - | 获取已注册的对象可注册时的回调函数。 |
| [void OH_NativeArkWeb_SetDestroyCallback(const char* webTag, NativeArkWeb_OnDestroyCallback callback)](#oh_nativearkweb_setdestroycallback) | - | 设置Web组件销毁时的回调函数。典型使用场景：需要在Web组件销毁时释放资源、清理状态或执行收尾操作时使用，例如释放JavaScript代理对象、取消网络请求、关闭文件句柄等。 |
| [NativeArkWeb_OnDestroyCallback OH_NativeArkWeb_GetDestroyCallback(const char* webTag)](#oh_nativearkweb_getdestroycallback) | - | 获取已注册的Web组件销毁时的回调函数。 |
| [ArkWeb_ErrorCode OH_NativeArkWeb_LoadData(const char* webTag, const char* data, const char* mimeType, const char* encoding, const char* baseUrl, const char* historyUrl)](#oh_nativearkweb_loaddata) | - | 加载数据或URL，此函数应在主线程中调用。典型使用场景：从网络或本地文件加载页面内容、动态生成HTML内容并显示、实现离线页面展示、自定义页面渲染等。 |
| [void OH_NativeArkWeb_RegisterAsyncThreadJavaScriptProxy(const char* webTag, const ArkWeb_ProxyObjectWithResult* proxyObject, const char* permission)](#oh_nativearkweb_registerasyncthreadjavascriptproxy) | - | 注册一个包含回调方法的 JavaScript 对象，这些方法可带有返回值。该对象将被注入到当前页面的所有frame中，包括所有的 iframe，并且可以通过在 ArkWeb_ProxyObjectWithResult中指定的名称进行访问。该对象只会在下一次加载或重新加载页面后在 JavaScript 中生效。这些方法将在 ArkWeb 的工作线程中执行。典型使用场景：可在工作线程中处理JavaScript调用并返回结果时使用。例如执行耗时计算、异步任务处理、复杂业务逻辑处理等场景，避免阻塞主线程。 |
| [ArkWeb_BlanklessErrorCode OH_NativeArkWeb_SetBlanklessLoadingWithKey(const char* webTag, const char* key, bool isStarted)](#oh_nativearkweb_setblanklessloadingwithkey) | - | 设置无白屏加载是否启用。本接口必须与OH_NativeArkWeb_GetBlanklessInfoWithKey接口配套使用。 |
| [void OH_NativeArkWeb_ClearBlanklessLoadingCache(const char* key[], uint32_t size)](#oh_nativearkweb_clearblanklessloadingcache) | - | 清除指定key值页面无白屏优化缓存，本接口只清除缓存。<br>在小程序或Web应用场景中，当页面加载时内容变化显著，可能会出现一次明显的跳变。若对此跳变有所顾虑，可使用该接口清除页面缓存。 |
| [ArkWeb_BlanklessInfo OH_NativeArkWeb_GetBlanklessInfoWithKey(const char* webTag, const char* key)](#oh_nativearkweb_getblanklessinfowithkey) | - | 获取页面首屏加载预测信息（详细说明见[ArkWeb_BlanklessInfo](capi-web-arkweb-blanklessinfo.md)），并开始本次加载过渡帧生成，应用根据此信息确定是否需要启用无白屏加载。必须与[OH_NativeArkWeb_SetBlanklessLoadingWithKey](capi-native-interface-arkweb-h.md#oh_nativearkweb_setblanklessloadingwithkey)接口配套使用，并且必须在触发加载页面的接口之前调用。需在WebViewController与Web组件绑定后才能使用。 |
| [uint32_t OH_NativeArkWeb_SetBlanklessLoadingCacheCapacity(uint32_t capacity)](#oh_nativearkweb_setblanklessloadingcachecapacity) | - | 设置无白屏加载方案的持久化缓存容量，返回实际生效值。默认缓存容量为30MB，最大值为100MB。当实际缓存超过容量时，将采用淘汰不常用的过渡帧的方式清理。典型使用场景：根据应用内存占用情况调整缓存大小、优化存储空间使用、平衡无白屏效果与系统资源消耗等。 |
| [ArkWeb_ErrorCode OH_ArkWebCookieManager_SaveCookieSync()](#oh_arkwebcookiemanager_savecookiesync) | - | 将当前可通过CookieManager API访问的所有cookie持久化到磁盘。如果要在非UI线程中使用此接口，则需要先使用{@link OH_ArkWeb_GetNativeAPI}初始化CookieManager接口。典型使用场景：可在应用退出或特定时机保存cookie状态时使用。例如保存用户登录状态、应用配置信息、会话数据等，确保应用重启后能够恢复之前的状态。 |
| [void OH_ArkWebCookieManager_SaveCookieAsync(OH_ArkWeb_OnCookieSaveCallback callback)](#oh_arkwebcookiemanager_savecookieasync) | - | 将当前可通过CookieManager API访问的所有cookie持久化到磁盘。如果要在非UI线程中使用此接口，则需要先使用{@link OH_ArkWeb_GetNativeAPI}初始化CookieManager接口；在不初始化CookieManager接口的情况下，此接口将在UI线程上自动执行。典型使用场景：需要异步保存cookie状态时使用，例如在页面加载完成、用户操作完成后异步保存cookie，避免阻塞主线程。 |
| [void OH_NativeArkWeb_SetActiveWebEngineVersion(ArkWebEngineVersion webEngineVersion)](#oh_nativearkweb_setactivewebengineversion) | - |  |
| [ArkWebEngineVersion OH_NativeArkWeb_GetActiveWebEngineVersion()](#oh_nativearkweb_getactivewebengineversion) | - |  |
| [void OH_NativeArkWeb_LazyInitializeWebEngineInCookieManager(bool lazy)](#oh_nativearkweb_lazyinitializewebengineincookiemanager) | - |  |
| [bool OH_NativeArkWeb_IsActiveWebEngineEvergreen()](#oh_nativearkweb_isactivewebengineevergreen) | - |  |
| [ArkWeb_ErrorCode OH_ArkWebCookieManager_FetchCookieSync(const char* url, bool incognito, bool includeHttpOnly, bool includePartitionedCookies, char** cookieValue)](#oh_arkwebcookiemanager_fetchcookiesync) | - | 获取指定URL对应的cookies。如果要在非UI线程中使用此接口，则需要先使用{@link OH_ArkWeb_GetNativeAPI}初始化CookieManager接口。 |
| [void OH_ArkWebCookieManager_FetchCookieAsync(const char* url, bool incognito, bool includeHttpOnly, bool includePartitionedCookies, OH_ArkWeb_OnCookieFetchCallback callback)](#oh_arkwebcookiemanager_fetchcookieasync) | - | 异步获取指定URL对应的cookies。在不初始化CookieManager接口的情况下，此接口将在UI线程上自动执行。 |

## 枚举类型说明

### ArkWebEngineVersion

```c
enum ArkWebEngineVersion
```

**描述**

ArkWeb内核版本，请参考{@link M114内核在OpenHarmony 6.0系统上的适配指导}，{@link M132内核在OpenHarmony 7.0系统上的适配指导}。

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| SYSTEM_DEFAULT = 0 | 系统默认内核（可参考{@link 约束与限制}），OpenHarmony 6.0版本默认为M132，OpenHarmony 7.0版本默认为M144。<br>**起始版本：** 20 |
| ARKWEB_M114 = 1 | OpenHarmony 6.0版本的遗留内核。开发者可选择此遗留内核，若系统版本上不存在此内核则设置无效，使用系统默认内核。<br>**起始版本：** 20 |
| ARKWEB_M132 = 2 | OpenHarmony 6.0版本的常青内核（OpenHarmony 7.0版本的遗留内核），M132为OpenHarmony 6.0版本的默认内核。若系统版本上不存在此内核则设置无效，使用系统默认内核。<br>**起始版本：** 20 |
| ARKWEB_M144 = 3 | OpenHarmony 7.0版本的常青内核，M144为OpenHarmony 7.0版本的默认内核。若系统版本上不存在此内核则设置无效，使用系统默认内核。<br>**起始版本：** 26.0.0 |
| ARKWEB_EVERGREEN = 99999 | 系统的最新内核（常青内核）。开发者可选择在每个系统版本上都使用最新的内核。<br>**起始版本：** 23 |


## 函数说明

### NativeArkWeb_OnJavaScriptCallback()

```c
typedef void (*NativeArkWeb_OnJavaScriptCallback)(const char*)
```

**描述**

定义执行JavaScript代码后返回结果的回调函数的类型。

**起始版本：** 11

### NativeArkWeb_OnJavaScriptProxyCallback()

```c
typedef char* (*NativeArkWeb_OnJavaScriptProxyCallback)(const char** argv, int32_t argc)
```

**描述**

定义注入对象的回调函数的类型。

**起始版本：** 11

### NativeArkWeb_OnValidCallback()

```c
typedef void (*NativeArkWeb_OnValidCallback)(const char*)
```

**描述**

定义Web组件可用时的回调函数的类型。

**起始版本：** 11

### NativeArkWeb_OnDestroyCallback()

```c
typedef void (*NativeArkWeb_OnDestroyCallback)(const char*)
```

**描述**

定义Web组件销毁时的回调函数的类型。

**起始版本：** 11

### OH_ArkWeb_OnCookieSaveCallback()

```c
typedef void (*OH_ArkWeb_OnCookieSaveCallback)(ArkWeb_ErrorCode errorCode)
```

**描述**

定义保存cookie的回调函数的类型。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkWeb_ErrorCode](capi-arkweb-error-code-h.md#arkweb_errorcode) errorCode | [ARKWEB_SUCCESS](capi-arkweb-error-code-h.md#arkweb_errorcode) 保存cookie成功。<br>[ARKWEB_COOKIE_SAVE_FAILED](capi-arkweb-error-code-h.md#arkweb_errorcode) 保存cookie失败。<br>[ARKWEB_COOKIE_MANAGER_INITIALIZE_FAILED](capi-arkweb-error-code-h.md#arkweb_errorcode) CookieManager初始化失败。 |

### OH_ArkWeb_OnCookieFetchCallback()

```c
typedef void (*OH_ArkWeb_OnCookieFetchCallback)(ArkWeb_ErrorCode errorCode, char* cookieValue)
```

**描述**

定义在获取cookie操作完成时调用的回调函数类型。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkWeb_ErrorCode](capi-arkweb-error-code-h.md#arkweb_errorcode) errorCode | 获取cookie回调错误码。<br>[ARKWEB_SUCCESS](capi-arkweb-error-code-h.md#arkweb_errorcode) 获取cookie成功。<br>[ARKWEB_INVALID_URL](capi-arkweb-error-code-h.md#arkweb_errorcode) 无效的URL。<br>[ARKWEB_LIBRARY_OPEN_FAILURE](capi-arkweb-error-code-h.md#arkweb_errorcode) 打开动态链接库失败。<br>[ARKWEB_LIBRARY_SYMBOL_NOT_FOUND](capi-arkweb-error-code-h.md#arkweb_errorcode) 动态链接库中找不到所需的符号。 |
| char\* cookieValue | 获取与URL对应的cookies。函数将为cookieValue分配内存，开发者必须通过{@link OH_ArkWeb_ReleaseString}释放该字符串。 |

### OH_NativeArkWeb_RunJavaScript()

```c
void OH_NativeArkWeb_RunJavaScript(const char* webTag, const char* jsCode, NativeArkWeb_OnJavaScriptCallback callback)
```

**描述**

在当前显示页面的环境下，加载并异步执行一段JavaScript代码。此函数应在主线程中调用。**使用场景**：需要在Native层动态修改页面内容、获取页面运行时信息、与页面JavaScript交互时使用，例如获取表单数据、执行自定义脚本等。

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | Web组件的名称。 |
| const char* jsCode | 一段JavaScript的代码脚本。 |
| [NativeArkWeb_OnJavaScriptCallback](capi-native-interface-arkweb-h.md#nativearkweb_onjavascriptcallback) callback | 代码执行完后通知开发者结果的回调函数。 |

### OH_NativeArkWeb_RegisterJavaScriptProxy()

```c
void OH_NativeArkWeb_RegisterJavaScriptProxy(const char* webTag, const char* objName, const char** methodList, NativeArkWeb_OnJavaScriptProxyCallback* callback, int32_t size, bool needRefresh)
```

**描述**

注册对象及函数名称列表，用于向Web页面注入Native对象，实现应用侧与前端页面的双向通信。用于Web页面调用Native功能、Native代码控制Web页面行为、混合应用中的跨层交互等场景。

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | Web组件的名称。 |
| const char* objName | 注入对象的名称。 |
| const char** methodList | 注入函数列表的名称。 |
| [NativeArkWeb_OnJavaScriptProxyCallback](capi-native-interface-arkweb-h.md#nativearkweb_onjavascriptproxycallback)* callback | 注入的回调函数。 |
| int32_t size | 注入的回调函数的个数。 |
| bool needRefresh | 是否需要刷新页面。true：刷新页面，false：不刷新页面。 |

### OH_NativeArkWeb_UnregisterJavaScriptProxy()

```c
void OH_NativeArkWeb_UnregisterJavaScriptProxy(const char* webTag, const char* objName)
```

**描述**

删除已注册的对象及其下的回调函数，用于清理不再需要的JavaScript注入对象。典型使用场景：页面销毁时清理注入对象、功能模块卸载时移除对应的Native接口、防止内存泄漏等场景。

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | Web组件的名称。 |
| const char* objName | 注入对象的名称。 |

### OH_NativeArkWeb_SetJavaScriptProxyValidCallback()

```c
void OH_NativeArkWeb_SetJavaScriptProxyValidCallback(const char* webTag, NativeArkWeb_OnValidCallback callback)
```

**描述**

设置对象可注册时的回调函数。需要在JavaScript代理对象成功注册后执行特定逻辑时使用，例如注册成功后通知页面或记录日志。

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | Web组件的名称。 |
| [NativeArkWeb_OnValidCallback](capi-native-interface-arkweb-h.md#nativearkweb_onvalidcallback) callback | 对象可注册时的回调函数。 |

### OH_NativeArkWeb_GetJavaScriptProxyValidCallback()

```c
NativeArkWeb_OnValidCallback OH_NativeArkWeb_GetJavaScriptProxyValidCallback(const char* webTag)
```

**描述**

获取已注册的对象可注册时的回调函数。

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | Web组件的名称。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeArkWeb_OnValidCallback](capi-native-interface-arkweb-h.md#nativearkweb_onvalidcallback) | 已注册的对象可注册时的回调函数。如果未设置由参数webTag指定的有效回调函数，则将返回空指针。 |

### OH_NativeArkWeb_SetDestroyCallback()

```c
void OH_NativeArkWeb_SetDestroyCallback(const char* webTag, NativeArkWeb_OnDestroyCallback callback)
```

**描述**

设置Web组件销毁时的回调函数。典型使用场景：需要在Web组件销毁时释放资源、清理状态或执行收尾操作时使用，例如释放JavaScript代理对象、取消网络请求、关闭文件句柄等。

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | Web组件的名称。 |
| [NativeArkWeb_OnDestroyCallback](capi-native-interface-arkweb-h.md#nativearkweb_ondestroycallback) callback | Web组件销毁时的回调函数。 |

### OH_NativeArkWeb_GetDestroyCallback()

```c
NativeArkWeb_OnDestroyCallback OH_NativeArkWeb_GetDestroyCallback(const char* webTag)
```

**描述**

获取已注册的Web组件销毁时的回调函数。

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | Web组件的名称。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeArkWeb_OnDestroyCallback](capi-native-interface-arkweb-h.md#nativearkweb_ondestroycallback) | 返回已注册的Web组件销毁时的回调函数。如果未设置由参数webTag指定的销毁回调函数，则将返回空指针。 |

### OH_NativeArkWeb_LoadData()

```c
ArkWeb_ErrorCode OH_NativeArkWeb_LoadData(const char* webTag, const char* data, const char* mimeType, const char* encoding, const char* baseUrl, const char* historyUrl)
```

**描述**

加载数据或URL，此函数应在主线程中调用。典型使用场景：从网络或本地文件加载页面内容、动态生成HTML内容并显示、实现离线页面展示、自定义页面渲染等。

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | Web组件的名称。 |
| const char* data | "Base64"或"URL"编码的字符串，不能为空。 |
| const char* mimeType | 媒体类型，例如"text/html"，不能为空。 |
| const char* encoding | 编码类型，例如"UTF-8"，不能为空。 |
| const char* baseUrl | 指定的URL路径("http"/"https"/"data"协议)，由Web组件分配给window.origin。 |
| const char* historyUrl | 历史URL，当它不为空时，可以通过历史记录来管理，实现前进和后退功能。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkWeb_ErrorCode](capi-arkweb-error-code-h.md#arkweb_errorcode) | OH_NativeArkWeb_LoadData 错误码。      <br>[ARKWEB_SUCCESS](capi-arkweb-error-code-h.md#arkweb_errorcode) 加载数据成功。      <br>[ARKWEB_INVALID_PARAM](capi-arkweb-error-code-h.md#arkweb_errorcode) 必填参数未指定或参数类型不正确或参数校验失败。      <br>[ARKWEB_INIT_ERROR](capi-arkweb-error-code-h.md#arkweb_errorcode) 初始化失败，根据传入的"webTag"找不到有效的Web组件。      <br>[ARKWEB_LIBRARY_OPEN_FAILURE](capi-arkweb-error-code-h.md#arkweb_errorcode) 打开动态链接库失败。请检查库文件路径是否正确、库文件是否损坏、是否有足够的访问权限。      <br>[ARKWEB_LIBRARY_SYMBOL_NOT_FOUND](capi-arkweb-error-code-h.md#arkweb_errorcode) 动态链接库中未找到所需的符号。 |

### OH_NativeArkWeb_RegisterAsyncThreadJavaScriptProxy()

```c
void OH_NativeArkWeb_RegisterAsyncThreadJavaScriptProxy(const char* webTag, const ArkWeb_ProxyObjectWithResult* proxyObject, const char* permission)
```

**描述**

注册一个包含回调方法的 JavaScript 对象，这些方法可带有返回值。该对象将被注入到当前页面的所有frame中，包括所有的 iframe，并且可以通过在 ArkWeb_ProxyObjectWithResult中指定的名称进行访问。该对象只会在下一次加载或重新加载页面后在 JavaScript 中生效。这些方法将在 ArkWeb 的工作线程中执行。典型使用场景：可在工作线程中处理JavaScript调用并返回结果时使用。例如执行耗时计算、异步任务处理、复杂业务逻辑处理等场景，避免阻塞主线程。

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | Web组件名称。 |
| [const ArkWeb_ProxyObjectWithResult](capi-web-arkweb-proxyobjectwithresult.md)* proxyObject | 注册的对象。 |
| const char* permission | json格式字符串，默认值为空。该字符串用来配置JSBridge的权限限制，可以配置对象和方法级别。 |

### OH_NativeArkWeb_SetBlanklessLoadingWithKey()

```c
ArkWeb_BlanklessErrorCode OH_NativeArkWeb_SetBlanklessLoadingWithKey(const char* webTag, const char* key, bool isStarted)
```

**描述**

设置无白屏加载是否启用。本接口必须与OH_NativeArkWeb_GetBlanklessInfoWithKey接口配套使用。

**需要权限：** ohos.permission.INTERNET and ohos.permission.GET_NETWORK_INFO

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | Web组件名称。 |
| const char* key | 唯一标识本页面的key值。必须与[OH_NativeArkWeb_GetBlanklessInfoWithKey](capi-native-interface-arkweb-h.md#oh_nativearkweb_getblanklessinfowithkey)接口的key值相同。<br>合法取值范围：非空，长度不超过2048个字符。<br>非法值设置行为：返回错误码[ArkWeb_BlanklessErrorCode](capi-arkweb-error-code-h.md#arkweb_blanklesserrorcode)，插帧不生效。 |
| bool isStarted | 是否启用插帧。true：启用插帧，当页面首屏相似度较高且需要减少白屏时间以提升加载体验时选择；false：不启用插帧，当页面跳变过大导致相似度较低或不需要优化加载体验时选择。<br>默认值：false。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkWeb_BlanklessErrorCode](capi-arkweb-error-code-h.md#arkweb_blanklesserrorcode) | 返回错误码，具体见[ArkWeb_BlanklessErrorCode](capi-arkweb-error-code-h.md#arkweb_blanklesserrorcode)定义。 |

### OH_NativeArkWeb_ClearBlanklessLoadingCache()

```c
void OH_NativeArkWeb_ClearBlanklessLoadingCache(const char* key[], uint32_t size)
```

**描述**

清除指定key值页面无白屏优化缓存，本接口只清除缓存。<br>在小程序或Web应用场景中，当页面加载时内容变化显著，可能会出现一次明显的跳变。若对此跳变有所顾虑，可使用该接口清除页面缓存。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* key[] | 清除Blankless优化方案页面的key值列表，key值为[OH_NativeArkWeb_GetBlanklessInfoWithKey](capi-native-interface-arkweb-h.md#oh_nativearkweb_getblanklessinfowithkey)中指定过的。<br>合法取值范围：长度不超过2048，keys数组长度<=100。key和加载页面时输入给ArkWeb的相同。<br>非法值设置行为：key长度超过2048时该key不生效；长度超过100时，取前100个；当为NULL时，清除所有缓存。 |
| uint32_t size | keys数组的大小。<br>合法取值范围：0~100。取值超过100时，keys数组取前100个。<br>非法值设置行为：取值大于100时，取前100个。 |

### OH_NativeArkWeb_GetBlanklessInfoWithKey()

```c
ArkWeb_BlanklessInfo OH_NativeArkWeb_GetBlanklessInfoWithKey(const char* webTag, const char* key)
```

**描述**

获取页面首屏加载预测信息（详细说明见[ArkWeb_BlanklessInfo](capi-web-arkweb-blanklessinfo.md)），并开始本次加载过渡帧生成，应用根据此信息确定是否需要启用无白屏加载。必须与[OH_NativeArkWeb_SetBlanklessLoadingWithKey](capi-native-interface-arkweb-h.md#oh_nativearkweb_setblanklessloadingwithkey)接口配套使用，并且必须在触发加载页面的接口之前调用。需在WebViewController与Web组件绑定后才能使用。

**需要权限：** ohos.permission.INTERNET and ohos.permission.GET_NETWORK_INFO

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | Web组件名称。 |
| const char* key | 唯一标识本页面的key值。<br>合法取值范围：非空，长度不超过2048个字符。<br>设置非法值时不生效。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkWeb_BlanklessInfo](capi-web-arkweb-blanklessinfo.md) | 页面首屏加载预测信息，主要包括首屏相似度预测值，首屏加载耗时预测值，应用需根据此信息来决策是否启用无白屏加载插帧。 |

### OH_NativeArkWeb_SetBlanklessLoadingCacheCapacity()

```c
uint32_t OH_NativeArkWeb_SetBlanklessLoadingCacheCapacity(uint32_t capacity)
```

**描述**

设置无白屏加载方案的持久化缓存容量，返回实际生效值。默认缓存容量为30MB，最大值为100MB。当实际缓存超过容量时，将采用淘汰不常用的过渡帧的方式清理。典型使用场景：根据应用内存占用情况调整缓存大小、优化存储空间使用、平衡无白屏效果与系统资源消耗等。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint32_t capacity | 设置持久化缓存容量，单位MB，最大设置不超过100MB。<br>默认值：30MB。<br>合法取值范围：0~100，当设置为0时，无缓存空间，则功能全局不开启。<br>非法值处理行为：大于100时生效值为100。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | 返回实际生效的容量值，单位为MB，范围0~100。      <br>大于100时生效值为100。 |

### OH_ArkWebCookieManager_SaveCookieSync()

```c
ArkWeb_ErrorCode OH_ArkWebCookieManager_SaveCookieSync()
```

**描述**

将当前可通过CookieManager API访问的所有cookie持久化到磁盘。如果要在非UI线程中使用此接口，则需要先使用{@link OH_ArkWeb_GetNativeAPI}初始化CookieManager接口。典型使用场景：可在应用退出或特定时机保存cookie状态时使用。例如保存用户登录状态、应用配置信息、会话数据等，确保应用重启后能够恢复之前的状态。

**起始版本：** 20

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkWeb_ErrorCode](capi-arkweb-error-code-h.md#arkweb_errorcode) | OH_ArkWebCookieManager_SaveCookieSync 错误码。请检查磁盘空间是否充足、是否有写入权限、cookie数据格式是否正确。      <br>[ARKWEB_SUCCESS](capi-arkweb-error-code-h.md#arkweb_errorcode) 保存cookie成功。      <br>[ARKWEB_COOKIE_SAVE_FAILED](capi-arkweb-error-code-h.md#arkweb_errorcode) 保存cookie失败。      <br>[ARKWEB_COOKIE_MANAGER_INITIALIZE_FAILED](capi-arkweb-error-code-h.md#arkweb_errorcode) CookieManager初始化失败。      <br>[ARKWEB_COOKIE_MANAGER_NOT_INITIALIZED](capi-arkweb-error-code-h.md#arkweb_errorcode) 在非UI线程中，不允许在不初始化CookieManager接口的情况下调用该接口。请先使用      {@link OH_ArkWeb_GetNativeAPI}初始化CookieManager接口。 |

### OH_ArkWebCookieManager_SaveCookieAsync()

```c
void OH_ArkWebCookieManager_SaveCookieAsync(OH_ArkWeb_OnCookieSaveCallback callback)
```

**描述**

将当前可通过CookieManager API访问的所有cookie持久化到磁盘。如果要在非UI线程中使用此接口，则需要先使用{@link OH_ArkWeb_GetNativeAPI}初始化CookieManager接口；在不初始化CookieManager接口的情况下，此接口将在UI线程上自动执行。典型使用场景：需要异步保存cookie状态时使用，例如在页面加载完成、用户操作完成后异步保存cookie，避免阻塞主线程。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkWeb_OnCookieSaveCallback](capi-native-interface-arkweb-h.md#oh_arkweb_oncookiesavecallback) callback | 保存cookie成功或失败后执行该回调。传入callback时使用回调方式异步接收操作结果，适用于需要异步通知保存结果的场景；不传入时根据具体实现可能有不同的行为。 |

### OH_NativeArkWeb_SetActiveWebEngineVersion()

```c
void OH_NativeArkWeb_SetActiveWebEngineVersion(ArkWebEngineVersion webEngineVersion)
```

**描述**

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| { | ArkWebEngineVersion } webEngineVersion - ArkWeb内核版本。详细说明见 [ArkWebEngineVersion](capi-native-interface-arkweb-h.md#arkwebengineversion). |

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
| { | bool } lazy - 是否延后初始化ArkWeb内核，true：延后，false：不延后。 |

### OH_NativeArkWeb_IsActiveWebEngineEvergreen()

```c
bool OH_NativeArkWeb_IsActiveWebEngineEvergreen()
```

**描述**

**起始版本：** 23

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 返回当前应用所使用内核是否为常青内核。true表示是常青内核，false表示不是常青内核。 |

### OH_ArkWebCookieManager_FetchCookieSync()

```c
ArkWeb_ErrorCode OH_ArkWebCookieManager_FetchCookieSync(const char* url, bool incognito, bool includeHttpOnly, bool includePartitionedCookies, char** cookieValue)
```

**描述**

获取指定URL对应的cookies。如果要在非UI线程中使用此接口，则需要先使用{@link OH_ArkWeb_GetNativeAPI}初始化CookieManager接口。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* url | 指定cookie所属的URL。建议填写完整的URL。 |
| bool incognito | true表示获取隐私模式下webview的内存cookie, false表示获取非隐私模式下的cookie。 |
| bool includeHttpOnly | true表示标记为HTTP-Only属性的cookie也将包含在cookieValue中，false表示不包含。 |
| bool includePartitionedCookies | true表示第一方partitioned cookies也将包含在cookieValue中，false表示不包含。 |
| char** cookieValue | 获取与URL对应的cookie值。函数将为cookieValue分配内存，开发者必须通过{@link OH_ArkWeb_ReleaseString}释放该字符串。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkWeb_ErrorCode](capi-arkweb-error-code-h.md#arkweb_errorcode) | 返回值错误码。      <br>[ARKWEB_SUCCESS](capi-arkweb-error-code-h.md#arkweb_errorcode) 获取cookie成功。      <br>[ARKWEB_INVALID_URL](capi-arkweb-error-code-h.md#arkweb_errorcode) 无效的URL。      <br>[ARKWEB_INVALID_PARAM](capi-arkweb-error-code-h.md#arkweb_errorcode) 参数无效。      <br>[ARKWEB_COOKIE_MANAGER_NOT_INITIALIZED](capi-arkweb-error-code-h.md#arkweb_errorcode) 在非UI线程中，不允许在不初始化CookieManager接口的情况下调用该接口。      请先使用OH_ArkWeb_GetNativeAPI初始化CookieManager接口。      <br>[ARKWEB_LIBRARY_OPEN_FAILURE](capi-arkweb-error-code-h.md#arkweb_errorcode) 打开动态链接库失败。      <br>[ARKWEB_LIBRARY_SYMBOL_NOT_FOUND](capi-arkweb-error-code-h.md#arkweb_errorcode) 动态链接库中找不到所需的符号。 |

### OH_ArkWebCookieManager_FetchCookieAsync()

```c
void OH_ArkWebCookieManager_FetchCookieAsync(const char* url, bool incognito, bool includeHttpOnly, bool includePartitionedCookies, OH_ArkWeb_OnCookieFetchCallback callback)
```

**描述**

异步获取指定URL对应的cookies。在不初始化CookieManager接口的情况下，此接口将在UI线程上自动执行。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* url | 指定cookie所属的URL。建议填写完整的URL。 |
| bool incognito | true表示获取隐私模式下webview的内存cookie, false表示获取非隐私模式下的cookie。 |
| bool includeHttpOnly | true表示标记为HTTP-Only属性的cookie也将包含在cookieValue中，false表示不包含。 |
| bool includePartitionedCookies | true表示第一方partitioned cookies也将包含在cookieValue中，false表示不包含。 |
| [OH_ArkWeb_OnCookieFetchCallback](capi-native-interface-arkweb-h.md#oh_arkweb_oncookiefetchcallback) callback | 获取cookies完成后执行该回调。 |


