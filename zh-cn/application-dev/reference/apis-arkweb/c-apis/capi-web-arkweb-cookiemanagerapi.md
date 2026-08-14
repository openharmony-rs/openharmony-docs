# ArkWeb_CookieManagerAPI

```c
typedef struct ArkWeb_CookieManagerAPI {...} ArkWeb_CookieManagerAPI
```

## 概述

ArkWeb_CookieManagerAPI是Cookie管理相关Native API结构体。该结构体提供了Cookie的读取、设置、清除和同步等操作能力，适用于需要在WebView组件中管理用户会话、跟踪用户首选项等场景，能够帮助开发者便捷地实现数据持久化和状态同步。<br>CookieManager相关接口需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取，调用前建议通过[ARKWEB_MEMBER_MISSING](capi-arkweb-type-h.md#arkweb_member_missing)校验函数指针的可用性，避免SDK与设备ROM不匹配导致崩溃。

**起始版本：** 12

**相关模块：** [Web](capi-web.md)

**所在头文件：** [arkweb_type.h](capi-arkweb-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| size_t size | 结构体的大小。 |


### 成员函数

| 名称 | 描述 |
| -- | -- |
| [ArkWeb_ErrorCode (\*fetchCookieSync)(const char* url, bool incognito, bool includeHttpOnly, char** cookieValue)](#fetchcookiesync) | Obtains the cookie value corresponding to a specified URL. |
| [ArkWeb_ErrorCode (\*configCookieSync)(const char* url,const char* cookieValue, bool incognito, bool includeHttpOnly)](#configcookiesync) | Sets the cookie value for a specified URL. |
| [bool (\*existCookies)(bool incognito)](#existcookies) | Check whether cookies exist. |
| [void (\*clearAllCookiesSync)(bool incognito)](#clearallcookiessync) | 清除所有cookies（包括持久化cookies和会话cookies）。用于用户退出登录、清除隐私数据、重置用户状态等场景。若仅需清除会话cookies，建议使用[clearSessionCookiesSync](capi-web-arkweb-cookiemanagerapi.md#clearsessioncookiessync)。该方法需在UI线程调用，调用前建议校验函数指针的可用性。 |
| [void (\*clearSessionCookiesSync)()](#clearsessioncookiessync) | 清除所有会话cookies。用于清除临时会话数据、关闭所有会话、会话超时清理等场景。该方法需在UI线程调用，调用前建议校验函数指针的可用性。 |

## 成员函数说明

### fetchCookieSync()

```c
ArkWeb_ErrorCode (*fetchCookieSync)(const char* url, bool incognito, bool includeHttpOnly, char** cookieValue)
```

**描述**

Obtains the cookie value corresponding to a specified URL.

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* url | URL to which the cookie to be obtained belongs. A complete URL is recommended. |
|  bool incognito | True indicates that the memory cookies of the webview in privacy mode are obtained,and false indicates that cookies in non-privacy mode are obtained. |
|  bool includeHttpOnly | If true HTTP-only cookies will also be included in the cookieValue. |
|  char** cookieValue | Get the cookie value corresponding to the URL. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkWeb_ErrorCode | Fetch cookie result code.<br>             {@link ARKWEB_SUCCESS} fetch cookie success.<br>             {@link ARKWEB_INVALID_URL} invalid url.<br>             {@link ARKWEB_INVALID_PARAM} cookieValue is nullptr. |

### configCookieSync()

```c
ArkWeb_ErrorCode (*configCookieSync)(const char* url,const char* cookieValue, bool incognito, bool includeHttpOnly)
```

**描述**

Sets the cookie value for a specified URL.

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* url | Specifies the URL to which the cookie belongs. A complete URL is recommended. |
| const char* cookieValue | The value of the cookie to be set. |
|  bool incognito | True indicates that cookies of the corresponding URL are set in privacy mode,and false indicates that cookies of the corresponding URL are set in non-privacy mode. |
|  bool includeHttpOnly | If true, HTTP-only cookies can also be overwritten. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkWeb_ErrorCode | Config cookie result code.<br>             {@link ARKWEB_SUCCESS} config cookie success.<br>             {@link ARKWEB_INVALID_URL} invalid url.<br>             {@link ARKWEB_INVALID_COOKIE_VALUE} invalid cookie value. |

### existCookies()

```c
bool (*existCookies)(bool incognito)
```

**描述**

Check whether cookies exist.

**参数：**

| 参数项 | 描述 |
| -- | -- |
| bool incognito | True indicates whether cookies exist in privacy mode,and false indicates whether cookies exist in non-privacy mode. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | True indicates that the cookie exists, and false indicates that the cookie does not exist. |

### clearAllCookiesSync()

```c
void (*clearAllCookiesSync)(bool incognito)
```

**描述**

清除所有cookies（包括持久化cookies和会话cookies）。用于用户退出登录、清除隐私数据、重置用户状态等场景。若仅需清除会话cookies，建议使用[clearSessionCookiesSync](capi-web-arkweb-cookiemanagerapi.md#clearsessioncookiessync)。该方法需在UI线程调用，调用前建议校验函数指针的可用性。

### clearSessionCookiesSync()

```c
void (*clearSessionCookiesSync)()
```

**描述**

清除所有会话cookies。用于清除临时会话数据、关闭所有会话、会话超时清理等场景。该方法需在UI线程调用，调用前建议校验函数指针的可用性。


