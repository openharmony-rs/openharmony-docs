# arkweb_error_code.h

## Overview

Declares the exception error codes of ArkWeb NDK APIs, which are used to return specific error information when ArkWeb-related API calls fail, helping developers quickly locate and resolve issues. These error codes cover common exception scenarios such as initialization, parameter verification, URL processing, cookie management, and library loading.

**Library**: libohweb.so

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 11

**Related module**: [Web](capi-web.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkWeb_ErrorCode](#arkweb_errorcode) | ArkWeb_ErrorCode | Enumerates the error codes of ArkWeb NDK APIs. |

### Macro

| Name | Description |
| -- | -- |
| ARKWEB_ERROR_CODE_H | Declares the exception error codes of ArkWeb NDK APIs, which are used to return specific error information when ArkWeb-related API calls fail, helping developers quickly locate and resolve issues. These error codes cover common exception scenarios such as initialization, parameter verification, URL processing, cookie management, and library loading.<br>**Since**: 12<br>**System capability**: SystemCapability.Web.Webview.Core |

## Enum type description

### ArkWeb_ErrorCode

```c
enum ArkWeb_ErrorCode
```

**Description**

Enumerates the error codes of ArkWeb NDK APIs.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKWEB_SUCCESS = 0 | Operation successful. |
| ARKWEB_INIT_ERROR = 17100001 | Initialization failure. Check the system environment to ensure that the dependent libraries are installed, and retry initialization. |
| ARKWEB_ERROR_UNKNOWN = 17100100 | Unknown error. Collect logs and provide feedback. |
| ARKWEB_INVALID_PARAM = 17100101 | Invalid parameter. Check whether the format, range, and type of the input parameter meet the API requirements. |
| ARKWEB_SCHEME_REGISTER_FAILED = 17100102 | Failed to register the scheme. Register the scheme before creating the **Web** component. |
| ARKWEB_INVALID_URL = 17100103 | Invalid URL. Check the URL format or protocol support. |
| ARKWEB_INVALID_COOKIE_VALUE = 17100104 | Invalid cookie value. Check the cookie format and validity. |
| ARKWEB_LIBRARY_OPEN_FAILURE = 17100105 | Failed to open the library.<br>**Since**: 15<br>**System capability**: SystemCapability.Web.Webview.Core |
| ARKWEB_LIBRARY_SYMBOL_NOT_FOUND = 17100106 | The required symbol was not found in the library.<br>**Since**: 15<br>**System capability**: SystemCapability.Web.Webview.Core |
| ARKWEB_COOKIE_MANAGER_NOT_INITIALIZED = 17100107 |  CookieManager not initialized. Call the initialization API to complete the initialization of CookieManager.<br>**Since**: 20 |
| ARKWEB_COOKIE_MANAGER_INITIALIZE_FAILED = 17100108 |  Failed to initialize CookieManager. Check the system capability and permission configuration.<br>**Since**: 20 |
| ARKWEB_COOKIE_SAVE_FAILED = 17100109 |  Failed to save the cookie. Check whether the storage space is sufficient, whether the write permission is granted, and whether the cookie value meets the specifications.<br>**Since**: 20 |


