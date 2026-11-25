# ArkWeb_CookieManagerAPI
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=d85a1b8fa185d55a402f908f378a6e1872935c67 translatedAt=2026-11-06T11:47:09.367Z pushedAt=2026-11-13T11:16:37.441Z nl=1 -->

```c
typedef struct {...} ArkWeb_CookieManagerAPI
```

## Overview

ArkWeb_CookieManagerAPI is a Native API struct for cookie management. This struct provides capabilities such as reading, setting, clearing, and synchronizing cookies. It is applicable to scenarios where user sessions need to be managed and user preferences need to be tracked in the Web component, helping developers conveniently implement data persistence and state synchronization.

By default, CookieManager-related APIs must be obtained by calling the OH_ArkWeb_GetNativeAPI method on the UI thread. Before calling, it is recommended to verify the availability of the function pointer through [ARKWEB_MEMBER_MISSING](capi-arkweb-type-h.md#macros) to avoid crashes caused by a mismatch between the SDK and the device ROM. Starting from API version 26.0.1, after calling [OH_NativeArkWeb_LazyInitializeWebEngineInCookieManager](capi-native-interface-arkweb-h.md#oh_nativearkweb_lazyinitializewebengineincookiemanager) and setting it to true, CookieManager-related APIs support use on non-UI threads.

**Since**: 12

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_type.h](capi-arkweb-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| size_t size | Size of the struct.|


### Member Functions

| Name | Description |
| -- | -- |
| [ArkWeb_ErrorCode (\*fetchCookieSync)(const char* url, bool incognito, bool includeHttpOnly, char** cookieValue)](#fetchcookiesync) | Obtains the cookie value of a specified URL. |
| [ArkWeb_ErrorCode (\*configCookieSync)(const char* url,const char* cookieValue, bool incognito, bool includeHttpOnly)](#configcookiesync) | Sets the cookie value of a specified URL. |
| [bool (*existCookies)(bool incognito)](#existcookies) | Checks whether cookies exist. |
| [void (*clearAllCookiesSync)(bool incognito)](#clearallcookiessync) | Clears all cookies. |
| [void (*clearSessionCookiesSync)()](#clearsessioncookiessync) | Clears all session cookies. |

## Member Function Description

### fetchCookieSync()

```c
ArkWeb_ErrorCode (*fetchCookieSync)(const char* url, bool incognito, bool includeHttpOnly, char** cookieValue)
```

**Description**

Obtains the cookie value corresponding to the specified URL. It is used in scenarios such as user login state maintenance, session management, and personalized configuration reading. By default, this method must be called on the UI thread, and it is recommended to verify the availability of the function pointer before calling. Starting from API version 26.0.1, after calling [OH_NativeArkWeb_LazyInitializeWebEngineInCookieManager](capi-native-interface-arkweb-h.md#oh_nativearkweb_lazyinitializewebengineincookiemanager) and setting it to true, calling on non-UI threads is supported.

**Parameters**

| Name| Description|
| -- | -- |
| const char* url | URL of the cookie to obtain. A complete URL is recommended.|
|  bool incognito | Whether to obtain the in-memory cookies of the Web component in privacy mode. The value true means to obtain cookies in privacy mode (automatically cleared after app exit), and false means to obtain cookies in non-privacy mode (persistent storage). |
|  bool includeHttpOnly | Whether to include cookies marked with the HTTP-Only attribute in cookieValue. The value true means to include them, and false means not to include them.<br/>**Note:** Reading HTTP-Only cookies must comply with security and compliance requirements. |
|  char** cookieValue |  Output parameter, which is a pointer to the cookie value corresponding to the URL. The memory is allocated internally by the function, and the caller must release it after use. The return value is a string that contains all matching cookie items in the format of name=value, where name and value are the name and value of the cookie, respectively. |

**Returns**

| Type                                                              | Description                                                                                                                        |
|------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| [ArkWeb_ErrorCode](capi-arkweb-error-code-h.md#arkweb_errorcode) | Result code.<br>[ARKWEB_SUCCESS](capi-arkweb-error-code-h.md#arkweb_errorcode): success.<br>[ARKWEB_INVALID_URL](capi-arkweb-error-code-h.md#arkweb_errorcode): invalid URL. Possible causes: incorrect URL format, empty URL, or non-compliant URL.<br>[ARKWEB_INVALID_PARAM](capi-arkweb-error-code-h.md#arkweb_errorcode): invalid cookieValue parameter. |

### configCookieSync()

```c
ArkWeb_ErrorCode (*configCookieSync)(const char* url, const char* cookieValue, bool incognito, bool includeHttpOnly)
```

**Description**

Sets the cookie value for the specified URL. It is used in scenarios such as saving user preferences, maintaining login state, and saving session information. By default, this method must be called on the UI thread, and it is recommended to verify the availability of the function pointer before calling. Starting from API version 26.0.1, after calling [OH_NativeArkWeb_LazyInitializeWebEngineInCookieManager](capi-native-interface-arkweb-h.md#oh_nativearkweb_lazyinitializewebengineincookiemanager) and setting it to true, calling on non-UI threads is supported.

**Parameters**

| Name| Description|
| -- | -- |
| const char* url | URL of the specified cookie. It must be a complete URL.|
| const char* cookieValue | Value of the cookie to set, in the format of name=value, where name and value are the name and value of the cookie, respectively. |
| bool incognito | Whether to set the cookie for the corresponding URL in privacy mode. The value true means the cookie is set in privacy mode (automatically cleared after the app exits), and false means the cookie is set in non-privacy mode (persistent storage). |
| bool includeHttpOnly | Whether to include or overwrite cookies marked with the HTTP-Only attribute. The value true means cookies marked with the HTTP-Only attribute can also be included in the result or overwritten, and false means only non-HTTP-Only cookies are processed.<br/>**Note:** Overwriting HTTP-Only cookies may affect security. Ensure that this meets your service security requirements. |

**Returns**

| Type                                                              | Description                                                                                                                        |
|------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| [ArkWeb_ErrorCode](capi-arkweb-error-code-h.md#arkweb_errorcode) | Result code.<br>[ARKWEB_SUCCESS](capi-arkweb-error-code-h.md#arkweb_errorcode): the cookie is set successfully.<br>[ARKWEB_INVALID_URL](capi-arkweb-error-code-h.md#arkweb_errorcode): invalid URL. Possible causes: incorrect URL format, empty URL, or non-compliant URL.<br>[ARKWEB_INVALID_COOKIE_VALUE](capi-arkweb-error-code-h.md#arkweb_errorcode): invalid cookieValue parameter. |

### existCookies()

```c
bool (*existCookies)(bool incognito)
```

**Description**

Checks whether a cookie exists. It is used in scenarios such as determining whether the user is logged in, checking whether a session is valid, and verifying identity status. By default, this method must be called on the UI thread, and it is recommended to verify the availability of the function pointer before calling. Starting from API version 26.0.1, after calling [OH_NativeArkWeb_LazyInitializeWebEngineInCookieManager](capi-native-interface-arkweb-h.md#oh_nativearkweb_lazyinitializewebengineincookiemanager) and setting it to true, calling on non-UI threads is supported.

**Parameters**

| Name| Description|
| -- | -- |
|  bool incognito | Whether the cookie exists in incognito mode or in non-incognito mode. The value **true** indicates that the cookie exists in incognito mode, and **false** indicates the opposite.|

**Returns**

| Type| Description|
|----|----|
| bool   | **true** is returned if the cookie exists; otherwise, **false** is returned.  |

### clearAllCookiesSync()

```c
void (*clearAllCookiesSync)(bool incognito)
```

**Description**

Clears all cookies (including persistent cookies and session cookies). It is used in scenarios such as user logout, clearing private data, and resetting user state. If only session cookies need to be cleared, it is recommended to use [clearSessionCookiesSync()](#clearsessioncookiessync). By default, this method must be called on the UI thread, and it is recommended to verify the availability of the function pointer before calling. Starting from API version 26.0.1, after calling [OH_NativeArkWeb_LazyInitializeWebEngineInCookieManager](capi-native-interface-arkweb-h.md#oh_nativearkweb_lazyinitializewebengineincookiemanager) and setting it to true, calling on non-UI threads is supported.

**Parameters**

| Name| Description|
|----|----|
| bool incognito   | Whether to clear all cookies in incognito mode. The value **true** means to clear all cookies in incognito mode, and **false** means the opposite.  |


### clearSessionCookiesSync()

```c
void (*clearSessionCookiesSync)()
```

**Description**

Clears all session cookies. It is used in scenarios such as clearing temporary session data, closing all sessions, and session timeout cleanup. By default, this method must be called on the UI thread, and it is recommended to verify the availability of the function pointer before calling. Starting from API version 26.0.1, after calling [OH_NativeArkWeb_LazyInitializeWebEngineInCookieManager](capi-native-interface-arkweb-h.md#oh_nativearkweb_lazyinitializewebengineincookiemanager) and setting it to true, calling on non-UI threads is supported.
