# arkweb_error_code.h

## Overview

Declares the exception error codes of ArkWeb NDK APIs, which are used to return specific error information when ArkWeb-related API calls fail, helping developers quickly locate and resolve issues. These error codes cover common exception scenarios such as initialization, parameter verification, URL processing, cookie management, and library loading.

**Library**: libohweb.so

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Related module**: [Web](capi-arkweb-web.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkWeb_ErrorCode](#arkweb_errorcode) | ArkWeb_ErrorCode | Enumerates the error codes of ArkWeb NDK APIs. |
| [ArkWeb_BlanklessErrorCode](#arkweb_blanklesserrorcode) | ArkWeb_BlanklessErrorCode | Enumerates the error codes for the blankless loading. |

## Enum type description

### ArkWeb_ErrorCode

```c
enum ArkWeb_ErrorCode
```

**Description**

Enumerates the error codes of ArkWeb NDK APIs.

<!--Device-enum ArkWeb_ErrorCode--><!--Device-enum ArkWeb_ErrorCode-End-->

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKWEB_SUCCESS = 0 | &nbsp;Operation successful.<br><!--Device-ARKWEB_SUCCESS = 0--><!--Device-ARKWEB_SUCCESS = 0-End--> |
| ARKWEB_INIT_ERROR = 17100001 | &nbsp;Initialization failure. Check the system environment to ensure that the dependent libraries are installed, and retry initialization.<br><!--Device-ARKWEB_INIT_ERROR = 17100001--><!--Device-ARKWEB_INIT_ERROR = 17100001-End--> |
| ARKWEB_ERROR_UNKNOWN = 17100100 | &nbsp;Unknown error. Collect logs and provide feedback.<br><!--Device-ARKWEB_ERROR_UNKNOWN = 17100100--><!--Device-ARKWEB_ERROR_UNKNOWN = 17100100-End--> |
| ARKWEB_INVALID_PARAM = 17100101 | &nbsp;Invalid parameter. Check whether the format, range, and type of the input parameter meet the API requirements.<br><!--Device-ARKWEB_INVALID_PARAM = 17100101--><!--Device-ARKWEB_INVALID_PARAM = 17100101-End--> |
| ARKWEB_SCHEME_REGISTER_FAILED = 17100102 | &nbsp;Failed to register the scheme. Register the scheme before creating the **Web** component.<br><!--Device-ARKWEB_SCHEME_REGISTER_FAILED = 17100102--><!--Device-ARKWEB_SCHEME_REGISTER_FAILED = 17100102-End--> |
| ARKWEB_INVALID_URL = 17100103 | &nbsp;Invalid URL. Check the URL format or protocol support.<br><!--Device-ARKWEB_INVALID_URL = 17100103--><!--Device-ARKWEB_INVALID_URL = 17100103-End--> |
| ARKWEB_INVALID_COOKIE_VALUE = 17100104 | &nbsp;Invalid cookie value. Check the cookie format and validity.<br><!--Device-ARKWEB_INVALID_COOKIE_VALUE = 17100104--><!--Device-ARKWEB_INVALID_COOKIE_VALUE = 17100104-End--> |
| ARKWEB_LIBRARY_OPEN_FAILURE = 17100105 | Failed to open the library.<br>**Since**: 15<br>**System capability**: SystemCapability.Web.Webview.Core<br><!--Device-ARKWEB_LIBRARY_OPEN_FAILURE = 17100105--><!--Device-ARKWEB_LIBRARY_OPEN_FAILURE = 17100105-End--> |
| ARKWEB_LIBRARY_SYMBOL_NOT_FOUND = 17100106 | The required symbol was not found in the library.<br>**Since**: 15<br>**System capability**: SystemCapability.Web.Webview.Core<br><!--Device-ARKWEB_LIBRARY_SYMBOL_NOT_FOUND = 17100106--><!--Device-ARKWEB_LIBRARY_SYMBOL_NOT_FOUND = 17100106-End--> |
| ARKWEB_COOKIE_MANAGER_NOT_INITIALIZED = 17100107 | &nbsp;CookieManager not initialized. Call the initialization API to complete the initialization of CookieManager.<br>**Since**: 20<br><!--Device-ARKWEB_COOKIE_MANAGER_NOT_INITIALIZED = 17100107--><!--Device-ARKWEB_COOKIE_MANAGER_NOT_INITIALIZED = 17100107-End--> |
| ARKWEB_COOKIE_MANAGER_INITIALIZE_FAILED = 17100108 | &nbsp;Failed to initialize CookieManager. Check the system capability and permission configuration.<br>**Since**: 20<br><!--Device-ARKWEB_COOKIE_MANAGER_INITIALIZE_FAILED = 17100108--><!--Device-ARKWEB_COOKIE_MANAGER_INITIALIZE_FAILED = 17100108-End--> |
| ARKWEB_COOKIE_SAVE_FAILED = 17100109 | &nbsp;Failed to save the cookie. Check whether the storage space is sufficient, whether the write permission is granted, and whether the cookie value meets the specifications.<br>**Since**: 20<br><!--Device-ARKWEB_COOKIE_SAVE_FAILED = 17100109--><!--Device-ARKWEB_COOKIE_SAVE_FAILED = 17100109-End--> |

### ArkWeb_BlanklessErrorCode

```c
enum ArkWeb_BlanklessErrorCode
```

**Description**

Enumerates the error codes for the blankless loading.

<!--Device-enum ArkWeb_BlanklessErrorCode--><!--Device-enum ArkWeb_BlanklessErrorCode-End-->

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 20

| Enum item | Description |
| -- | -- |
| ARKWEB_BLANKLESS_SUCCESS = 0 | &nbsp;Operation successful.<br><!--Device-ARKWEB_BLANKLESS_SUCCESS = 0--><!--Device-ARKWEB_BLANKLESS_SUCCESS = 0-End--> |
| ARKWEB_BLANKLESS_ERR_UNKNOWN = -1 | &nbsp;Unknown error or internal status error.<br><!--Device-ARKWEB_BLANKLESS_ERR_UNKNOWN = -1--><!--Device-ARKWEB_BLANKLESS_ERR_UNKNOWN = -1-End--> |
| ARKWEB_BLANKLESS_ERR_INVALID_ARGS = -2 | &nbsp;Invalid parameter.<br><!--Device-ARKWEB_BLANKLESS_ERR_INVALID_ARGS = -2--><!--Device-ARKWEB_BLANKLESS_ERR_INVALID_ARGS = -2-End--> |
| ARKWEB_BLANKLESS_ERR_CONTROLLER_NOT_INITED = -3 | &nbsp;**WebViewController** is not bound to any component.<br><!--Device-ARKWEB_BLANKLESS_ERR_CONTROLLER_NOT_INITED = -3--><!--Device-ARKWEB_BLANKLESS_ERR_CONTROLLER_NOT_INITED = -3-End--> |
| ARKWEB_BLANKLESS_ERR_KEY_NOT_MATCH = -4 | &nbsp;The key value is not matched. The **OH_NativeArkWeb_SetBlanklessLoadingWithKey** and **OH_NativeArkWeb_GetBlanklessInfoWithKey** APIs must be used in pair and use the same key value.<br><!--Device-ARKWEB_BLANKLESS_ERR_KEY_NOT_MATCH = -4--><!--Device-ARKWEB_BLANKLESS_ERR_KEY_NOT_MATCH = -4-End--> |
| ARKWEB_BLANKLESS_ERR_SIGNIFICANT_CHANGE = -5 | &nbsp;When the similarity is low, the system will deem the scene change too abrupt and frame insertion through the **OH_NativeArkWeb_SetBlanklessLoadingWithKey** API will fail.<br><!--Device-ARKWEB_BLANKLESS_ERR_SIGNIFICANT_CHANGE = -5--><!--Device-ARKWEB_BLANKLESS_ERR_SIGNIFICANT_CHANGE = -5-End--> |
| ARKWEB_BLANKLESS_ERR_DEVICE_NOT_SUPPORT = 801 | &nbsp;This device does not support this feature.<br><!--Device-ARKWEB_BLANKLESS_ERR_DEVICE_NOT_SUPPORT = 801--><!--Device-ARKWEB_BLANKLESS_ERR_DEVICE_NOT_SUPPORT = 801-End--> |


