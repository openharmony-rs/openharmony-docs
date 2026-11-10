# ArkWeb_RequestHeaderList_
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=9335f9431a5527342362c84e826071649d8c2b39 translatedAt=2026-11-06T11:49:12.525Z pushedAt=2026-11-09T11:44:59.694Z nl=1 -->

```c
typedef struct ArkWeb_RequestHeaderList_ ArkWeb_RequestHeaderList
```

## Overview

ArkWeb_RequestHeaderList is an HTTP request header list struct used to represent and manage a collection of key-value pairs of HTTP request headers in the ArkWeb NDK. This struct contains a request header array (headers) and the array length (headerCount), where headers is a pointer array of ArkWeb_RequestHeader and headerCount indicates the number of elements in the array. This struct is used together with ArkWeb_ResourceRequest and other structs to provide the capability of reading and setting network request headers for Web components. Use cases: processing HTTP request headers in a custom protocol handler, modifying request headers in a network request interceptor, adding authentication headers in API authentication scenarios, and configuring request headers in scenarios such as cache control and content negotiation.

**Since**: 12

**Related module**: [Web](capi-web.md)

**System capability**: SystemCapability.Web.Webview.Core

**Header file**: [arkweb_scheme_handler.h](capi-arkweb-scheme-handler-h.md)

