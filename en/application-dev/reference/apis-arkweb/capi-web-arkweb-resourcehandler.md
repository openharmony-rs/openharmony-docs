# ArkWeb_ResourceHandler_

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=d1b85ec7ea193eefc4ef0fcb99c42629d3e17584 translatedAt=2026-08-03T09:53:57.691Z pushedAt=2026-08-06T11:51:00.484Z -->

```c
typedef struct ArkWeb_ResourceHandler_ ArkWeb_ResourceHandler
```

## Overview

The ArkWeb_ResourceHandler struct is a resource handler for processing intercepted scheme requests. After ArkWeb_SchemeHandler intercepts a request of a specified scheme, this struct can be used to return custom response data to the Web component, including the response status code, response headers, and response body. This struct is passed as a parameter in the onRequestStart callback, through which developers can implement fully custom responses to intercepted requests.

**Since**: 12

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_scheme_handler.h](capi-arkweb-scheme-handler-h.md)