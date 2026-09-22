# ArkWeb_ProxyMethod

```c
typedef struct ArkWeb_ProxyMethod {...} ArkWeb_ProxyMethod
```

## Overview

ArkWeb_ProxyMethod is a struct that defines a JavaScript proxy method. It supports secure communication between JavaScript and native code, and is suitable for scenarios where native capabilities need to be called from a web page. This struct specifies the basic information of a native method that can be called from JavaScript, consisting of three fields: the method name, the corresponding native callback pointer, and the custom data to carry. Multiple ArkWeb_ProxyMethod instances can be combined into an ArkWeb_ProxyObject, which is injected into a web page as an object, allowing web apps to conveniently access native device capabilities.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_type.h](capi-arkweb-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char* methodName | Pointer to the method name to be injected. |
| [ArkWeb_OnJavaScriptProxyCallback](capi-arkweb-type-h.md#arkweb_onjavascriptproxycallback) callback | Callback triggered when JavaScript calls this method through a Proxy object, used to handle method calls from JavaScript. The callback can access the parameters (dataArray) passed in from JavaScript and execute the corresponding native logic. |
| void* userData | Custom data to be carried in the callback. |


