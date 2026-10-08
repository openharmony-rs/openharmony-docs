# ArkWeb_RequestHeaderList_

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=3cf0e4d31df69a8bda793fe15a55a60676b46acc translatedAt=2026-08-03T09:53:46.903Z pushedAt=2026-08-06T11:49:46.940Z -->

```c
typedef struct ArkWeb_RequestHeaderList_ ArkWeb_RequestHeaderList
```

## Overview

ArkWeb_RequestHeaderList is an HTTP request header list struct used to represent and manage a collection of key-value pairs of HTTP request headers in the ArkWeb NDK. This struct contains a request header array (headers) and the array length (headerCount), where headers is a pointer array of ArkWeb_RequestHeader and headerCount indicates the number of elements in the array. This struct is used together with ArkWeb_ResourceRequest and other structs to provide the capability of reading and setting network request headers for Web components. Use cases: processing HTTP request headers in a custom protocol handler, modifying request headers in a network request interceptor, adding authentication headers in API authentication scenarios, and configuring request headers in scenarios such as cache control and content negotiation.

**Since**: 12

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_scheme_handler.h](capi-arkweb-scheme-handler-h.md)