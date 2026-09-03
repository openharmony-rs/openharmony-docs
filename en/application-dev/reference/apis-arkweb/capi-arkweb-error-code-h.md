# arkweb_error_code.h

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=d1b85ec7ea193eefc4ef0fcb99c42629d3e17584 translatedAt=2026-08-03T09:56:41.664Z pushedAt=2026-08-05T08:36:19.502Z -->

## Overview

Declares the exception error codes of ArkWeb NDK APIs, which are used to return specific error information when ArkWeb-related API calls fail, helping developers quickly locate and resolve issues. These error codes cover common exception scenarios such as initialization, parameter verification, URL processing, cookie management, and library loading.

**File to include**: <web/arkweb_error_code.h>

**Library**: libohweb.so

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Related module**: [Web](capi-web.md)

## Summary

### Enums

| Name                                   | typedef Keyword| Description|
|---------------------------------------|------------|----|
| [ArkWeb_ErrorCode](#arkweb_errorcode) | ArkWeb_ErrorCode | Enumerates the result statuses of ArkWeb NDK API operations, used to determine whether an API call is successful. |
| [ArkWeb_BlanklessErrorCode](#arkweb_blanklesserrorcode) | ArkWeb_BlanklessErrorCode | Enumerates the result statuses of blankless loading feature operations, used to determine whether a blankless loading API call is successful. |

## Enum Description

### ArkWeb_ErrorCode

```c
enum ArkWeb_ErrorCode
```

**Description**

Enumerates the error codes of ArkWeb NDK APIs.

**Since**: 12

| Enum Item                                    | Description                                               |
| ------------------------------------------ | --------------------------------------------------- |
| ARKWEB_SUCCESS = 0                         | Operation successful.                                             |
| ARKWEB_INIT_ERROR = 17100001               | Initialization failure. Check the system environment to ensure that the dependent libraries are installed, and retry initialization.                                        |
| ARKWEB_ERROR_UNKNOWN = 17100100            | Unknown error. Collect logs and provide feedback.                                          |
| ARKWEB_INVALID_PARAM = 17100101            | Invalid parameter. Check whether the format, range, and type of the input parameter meet the API requirements.                                          |
| ARKWEB_SCHEME_REGISTER_FAILED = 17100102   | Failed to register the scheme. Register the scheme before creating the **Web** component.   |
| ARKWEB_INVALID_URL = 17100103              | Invalid URL. Check the URL format or protocol support.                                         |
| ARKWEB_INVALID_COOKIE_VALUE = 17100104     | Invalid cookie value. Check the cookie format and validity.                                    |
| ARKWEB_LIBRARY_OPEN_FAILURE = 17100105     | Failed to open the dynamic link library. Check whether the dynamic link library file exists, whether the path is correct, and whether the read permission is granted.<br>**Since:** 15           |
| ARKWEB_LIBRARY_SYMBOL_NOT_FOUND = 17100106 | The required symbol cannot be found in the dynamic link library.<br>**Since**: 15|
| ARKWEB_COOKIE_MANAGER_NOT_INITIALIZED = 17100107 | CookieManager not initialized. Call the initialization API to complete the initialization of CookieManager.<br>**Since:** 20 |
| ARKWEB_COOKIE_MANAGER_INITIALIZE_FAILED = 17100108 | Failed to initialize CookieManager. Check the system capability and permission configuration.<br>**Since:** 20 |
| ARKWEB_COOKIE_SAVE_FAILED = 17100109 | Failed to save the cookie. Check whether the storage space is sufficient, whether the write permission is granted, and whether the cookie value meets the specifications.<br>**Since:** 20 |

### ArkWeb_BlanklessErrorCode

```c
enum ArkWeb_BlanklessErrorCode
```

**Description**

Enumerates the error codes for the blankless loading.

**Since**: 20

| Enum Item                                    | Description                                               |
| ------------------------------------------ | --------------------------------------------------- |
| ARKWEB_BLANKLESS_SUCCESS = 0               | Operation successful.                                              |
| ARKWEB_BLANKLESS_ERR_UNKNOWN = -1          | Unknown error or internal status error.                            |
| ARKWEB_BLANKLESS_ERR_INVALID_ARGS = -2     | Invalid parameter.                                         |
| ARKWEB_BLANKLESS_ERR_CONTROLLER_NOT_INITED = -3 | **WebViewController** is not bound to any component.                      |
| ARKWEB_BLANKLESS_ERR_KEY_NOT_MATCH = -4    | The key value is not matched. The **OH_NativeArkWeb_SetBlanklessLoadingWithKey** and **OH_NativeArkWeb_GetBlanklessInfoWithKey** APIs must be used in pair and use the same key value.|
| ARKWEB_BLANKLESS_ERR_SIGNIFICANT_CHANGE = -5 | When the similarity is low, the system will deem the scene change too abrupt and frame insertion through the **OH_NativeArkWeb_SetBlanklessLoadingWithKey** API will fail.|
| ARKWEB_BLANKLESS_ERR_DEVICE_NOT_SUPPORT = 801 | This device does not support this feature.|