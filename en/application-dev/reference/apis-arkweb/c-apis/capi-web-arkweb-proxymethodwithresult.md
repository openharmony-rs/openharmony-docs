# ArkWeb_ProxyMethodWithResult

```c
typedef struct ArkWeb_ProxyMethodWithResult {...} ArkWeb_ProxyMethodWithResult
```

## Overview

ArkWeb_ProxyMethodWithResult is a JavaScript proxy method struct with a return value. It extends the capabilities of ArkWeb_ProxyMethod and supports obtaining a return value after JavaScript calls a native method. Based on the method name and callback function, this struct adds the return value processing capability, making it suitable for scenarios where execution results need to be returned to the web frontend.

**Since**: 18

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_type.h](capi-arkweb-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char* methodName | Pointer to the method name to be injected. |
| [ArkWeb_OnJavaScriptProxyCallbackWithResult](capi-arkweb-type-h.md#arkweb_onjavascriptproxycallbackwithresult) callback | Callback invoked when JavaScript calls the native proxy method, used to process the method call and return the execution result. This parameter must be a valid function pointer and cannot be NULL. |
| void* userData | Custom data to be carried in the callback. |


