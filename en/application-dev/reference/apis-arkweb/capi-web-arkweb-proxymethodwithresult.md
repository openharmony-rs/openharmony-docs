# ArkWeb_ProxyMethodWithResult

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=3cf0e4d31df69a8bda793fe15a55a60676b46acc translatedAt=2026-08-03T09:53:28.916Z pushedAt=2026-08-06T11:37:13.434Z -->

```c
typedef struct {...} ArkWeb_ProxyMethodWithResult
```

## Overview

ArkWeb_ProxyMethodWithResult is a JavaScript proxy method struct with a return value. It extends the capabilities of ArkWeb_ProxyMethod and supports obtaining a return value after JavaScript calls a native method. Based on the method name and callback function, this struct adds the return value processing capability, making it suitable for scenarios where execution results need to be returned to the web frontend.

**Since**: 18

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_type.h](capi-arkweb-type-h.md)

## Total

### Member Variables

| Name                                                                                                                     | Description|
|-------------------------------------------------------------------------------------------------------------------------| -- |
| const char* methodName                                                                                                  | Name of the native method injected into the JavaScript environment, used for calling the specified native method from the web frontend. This parameter must be a non-null pointer. It is recommended to use a name with clear business semantics to avoid conflicts with existing JavaScript methods. |
| [ArkWeb_OnJavaScriptProxyCallbackWithResult](capi-arkweb-type-h.md#arkweb_onjavascriptproxycallbackwithresult) callback | Callback invoked when JavaScript calls the native proxy method, used to process the method call and return the execution result. This parameter must be a valid function pointer and cannot be NULL.      |
| void* userData                                                                                                          | Pointer to the custom data, allocated and released by the caller. It must remain valid during callback execution and is used to pass business context or state objects in the callback. NULL if not passed.                |