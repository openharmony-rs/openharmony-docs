# ArkWeb_ProxyObject

```c
typedef struct ArkWeb_ProxyObject {...} ArkWeb_ProxyObject
```

## Overview

ArkWeb_ProxyObject is a JavaScript proxy object struct injected into a web page. It organizes a group of related ArkWeb_ProxyMethod methods into an object and exposes them to the web frontend as a whole. This struct specifies the object name in JavaScript (objName), the method array (methodList), and the method count (size), enabling a Native app to expose a structured API set to the web page. The proxy object associates ArkWeb_ProxyMethod on the native side with method calls on the JavaScript side through a method mapping mechanism, supporting automatic conversion of method parameters and return values.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_type.h](capi-arkweb-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char* objName | Name of the injected object. The name must follow JavaScript identifier rules and cannot contain special characters. |
| const [ArkWeb_ProxyMethod*](capi-web-arkweb-proxymethod.md) methodList | Pointer to the method struct array of an object to be injected. |
| size_t size | Length of the method struct array. Must be consistent with the actual number of elements in the methodList array. |


