# Web

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui; @zourongchun-->
<!--Designer: @yaomingliu; @zhufenghao-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=3cf0e4d31df69a8bda793fe15a55a60676b46acc translatedAt=2026-08-03T09:56:52.220Z pushedAt=2026-08-06T13:09:13.779Z -->

## Overview

Declares ArkWeb NDK API exception error codes, applicable to exception diagnosis and error handling on the native side, helping developers quickly locate issues and improve debugging efficiency.

Provides APIs for injecting objects and executing JavaScript code, applicable to bidirectional interaction between the app and frontend pages, enhancing page capabilities and improving user experience and development efficiency.

Provides APIs for intercepting ArkWeb requests, applicable to custom protocol handling, network request monitoring, and data security scenarios, enhancing app controllability and security.

Declares ArkWeb network protocol stack error codes, applicable to network request failure diagnosis and exception handling, helping developers quickly troubleshoot network faults and optimize connection stability.

Provides ArkWeb native-side capabilities such as page refresh, executing JavaScript, and registering callbacks, applicable to scenarios where WebView behavior needs to be controlled from the native side and frontend events need to be responded to, enhancing app flexibility and interaction capabilities.

For more details, see [Mutual Invoking Between the Application and the Frontend Page (C/C++)](../../web/arkweb-ndk-jsbridge.md), [Establishing a Data Channel Between the Application and the Frontend Page (C/C++)](../../web/arkweb-ndk-page-data-channel.md), and [Intercepting Network Requests Initiated by the Web Component](../../web/web-scheme-handler.md). These resources help developers implement efficient bidirectional communication and request interception, improving app performance and controllability.

**Since**: 12

## Files

| Name| Description|
| -- | -- |
| [arkweb_error_code.h](capi-arkweb-error-code-h.md) | Declares the error codes of the ArkWeb NDK APIs.|
| [arkweb_interface.h](capi-arkweb-interface-h.md) | Provides the ArkWeb APIs for obtaining native APIs and the basic native API types.|
| [arkweb_net_error_list.h](capi-arkweb-net-error-list-h.md) | Declares the error codes of the ArkWeb network protocol stack.|
| [arkweb_scheme_handler.h](capi-arkweb-scheme-handler-h.md) | Declares the APIs for intercepting requests from ArkWeb. |
| [arkweb_type.h](capi-arkweb-type-h.md) | Defines the common types on the ArkWeb native side. |
| [native_interface_arkweb.h](capi-native-interface-arkweb-h.md) | Declares the APIs for injecting objects, executing JavaScript, and other functions. |