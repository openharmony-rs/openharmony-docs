# ArkWeb_ResourceHandler_

```c
typedef struct ArkWeb_ResourceHandler_ ArkWeb_ResourceHandler
```

## Overview

The ArkWeb_ResourceHandler struct is a resource handler for processing intercepted scheme requests. After ArkWeb_SchemeHandler intercepts a request of a specified scheme, this struct can be used to return custom response data to the Web component, including the response status code, response headers, and response body. This struct is passed as a parameter in the onRequestStart callback, through which developers can implement fully custom responses to intercepted requests.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_scheme_handler.h](capi-arkweb-scheme-handler-h.md)

