# ArkWeb_CookieManagerAPI

```c
typedef struct ArkWeb_CookieManagerAPI {...} ArkWeb_CookieManagerAPI
```

## Overview

ArkWeb_CookieManagerAPI is a Native API struct for cookie management. This struct provides capabilities such as reading, setting, clearing, and synchronizing cookies. It is applicable to scenarios where user sessions need to be managed and user preferences need to be tracked in the Web component, helping developers conveniently implement data persistence and state synchronization.<br>CookieManager APIs must be obtained by calling the OH_ArkWeb_GetNativeAPI method in the UI thread. Before calling, you are advised to use {@link ARKWEB_MEMBER_MISSING} to check the availability of function pointers, so as to avoid crashes caused by mismatch between the SDK and the device ROM.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_type.h](capi-arkweb-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| size_t size | Size of the struct. |


### Member functions

| Name | Description |
| -- | -- |
| [ArkWeb_ErrorCode (\*fetchCookieSync)(const char* url, bool incognito, bool includeHttpOnly, char** cookieValue)](#fetchcookiesync) | Obtains the cookie value of a specified URL. This method is used in scenarios such as user login state maintenance, session management, and personalized configuration reading. This method must be called in the UI thread. Before calling, you are advised to check the availability of the function pointer. |
| [ArkWeb_ErrorCode (\*configCookieSync)(const char* url,const char* cookieValue, bool incognito, bool includeHttpOnly)](#configcookiesync) | Sets the cookie value of a specified URL. This method is used in scenarios such as saving user preference settings, maintaining login state, and saving session information. This method must be called in the UI thread. Before calling, you are advised to check the availability of the function pointer. |
| [bool (\*existCookies)(bool incognito)](#existcookies) | Check whether cookies exist. |
| [void (\*clearAllCookiesSync)(bool incognito)](#clearallcookiessync) | Clears all cookies (including persistent cookies and session cookies). This method is used in scenarios such as user logout, clearing privacy data, and resetting user state. If you only need to clear session cookies, you are advised to use {@link clearSessionCookiesSync}. This method must be called in the UI thread. Before calling, you are advised to check the availability of the function pointer. |
| [void (\*clearSessionCookiesSync)()](#clearsessioncookiessync) | Clears all session cookies. This method is used in scenarios such as clearing temporary session data, closing all sessions, and cleaning up session timeouts. This method must be called in the UI thread. Before calling, you are advised to check the availability of the function pointer. |

## Member function description

### fetchCookieSync()

```c
ArkWeb_ErrorCode (*fetchCookieSync)(const char* url, bool incognito, bool includeHttpOnly, char** cookieValue)
```

**Description**

Obtains the cookie value of a specified URL. This method is used in scenarios such as user login state maintenance, session management, and personalized configuration reading. This method must be called in the UI thread. Before calling, you are advised to check the availability of the function pointer.

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* url | URL of the cookie to obtain. A complete URL is recommended. |
|  bool incognito | Whether to obtain the in-memory cookies of the Web component in privacy mode. The value true means to obtain cookies in privacy mode (automatically cleared after app exit), and false means to obtain cookies in non-privacy mode (persistent storage). |
|  bool includeHttpOnly | Whether to include cookies marked with the HTTP-Only attribute in cookieValue. The value true means to include them, and false means not to include them. **Note:** Reading HTTP-Only cookies must comply with security and compliance requirements. |
|  char** cookieValue | Output parameter, which is a pointer to the cookie value corresponding to the URL. The memory is allocated internally by the function, and the caller must release it after use. The return value is a string that contains all matching cookie items in the format of name=value, where name and value are the name and value of the cookie, respectively. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkWeb_ErrorCode | Result code.          <br>{@link ARKWEB_SUCCESS}: success.<br>    <br>{@link ARKWEB_INVALID_URL}: invalid URL. Possible causes: incorrect URL format, empty URL, or non-<br>    compliant URL.<br>    <br>{@link ARKWEB_INVALID_PARAM}: invalid cookieValue parameter. |

### configCookieSync()

```c
ArkWeb_ErrorCode (*configCookieSync)(const char* url,const char* cookieValue, bool incognito, bool includeHttpOnly)
```

**Description**

Sets the cookie value of a specified URL. This method is used in scenarios such as saving user preference settings, maintaining login state, and saving session information. This method must be called in the UI thread. Before calling, you are advised to check the availability of the function pointer.

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* url | URL of the specified cookie. It must be a complete URL. |
| const char* cookieValue | Value of the cookie to set, in the format of name=value, where name and value are the name and value of the cookie, respectively. |
|  bool incognito | Whether to set the cookie for the corresponding URL in privacy mode. The value true means the cookie is set in privacy mode (automatically cleared after the app exits), and false means the cookie is set in non-privacy mode (persistent storage). |
|  bool includeHttpOnly | Whether to include or overwrite cookies marked with the HTTP-Only attribute. The value true means cookies marked with the HTTP-Only attribute can also be included in the result or overwritten, and false means only non-HTTP-Only cookies are processed. **Note:** Overwriting HTTP-Only cookies may affect security. Ensure that this meets your service security requirements. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkWeb_ErrorCode | Result code.          <br>{@link ARKWEB_SUCCESS}: the cookie is set successfully.<br>    <br>{@link ARKWEB_INVALID_URL}: invalid URL. Possible causes: incorrect URL format, empty URL, or non-<br>    compliant URL.<br>    <br>{@link ARKWEB_INVALID_COOKIE_VALUE}: invalid cookieValue parameter. |

### existCookies()

```c
bool (*existCookies)(bool incognito)
```

**Description**

Check whether cookies exist.

**Parameters**:

| Parameter | Description |
| -- | -- |
| bool incognito | True indicates whether cookies exist in privacy mode, and false indicates whether cookies exist in non-privacy mode. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | True indicates that the cookie exists, and false indicates that the cookie does not exist. |

### clearAllCookiesSync()

```c
void (*clearAllCookiesSync)(bool incognito)
```

**Description**

Clears all cookies (including persistent cookies and session cookies). This method is used in scenarios such as user logout, clearing privacy data, and resetting user state. If you only need to clear session cookies, you are advised to use {@link clearSessionCookiesSync}. This method must be called in the UI thread. Before calling, you are advised to check the availability of the function pointer.

**Parameters**:

| Parameter | Description |
| -- | -- |
| bool incognito | Whether to clear all cookies in incognito mode. The value **true** means to clear all cookies in incognito mode, and **false** means the opposite. |

### clearSessionCookiesSync()

```c
void (*clearSessionCookiesSync)()
```

**Description**

Clears all session cookies. This method is used in scenarios such as clearing temporary session data, closing all sessions, and cleaning up session timeouts. This method must be called in the UI thread. Before calling, you are advised to check the availability of the function pointer.


