# ArkWeb_RequestHeaderList_

```c
typedef struct ArkWeb_RequestHeaderList_ ArkWeb_RequestHeaderList
```

## Overview

ArkWeb_RequestHeaderList is an HTTP request header list struct used to represent and manage a collection of key-value pairs of HTTP request headers in the ArkWeb NDK. This struct contains a request header array (headers) and the array length (headerCount), where headers is a pointer array of ArkWeb_RequestHeader and headerCount indicates the number of elements in the array. This struct is used together with ArkWeb_ResourceRequest and other structs to provide the capability of reading and setting network request headers for Web components. Use cases: processing HTTP request headers in a custom protocol handler, modifying request headers in a network request interceptor, adding authentication headers in API authentication scenarios, and configuring request headers in scenarios such as cache control and content negotiation.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_scheme_handler.h](capi-arkweb-scheme-handler-h.md)

