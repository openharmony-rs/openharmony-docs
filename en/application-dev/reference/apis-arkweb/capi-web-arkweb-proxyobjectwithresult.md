# ArkWeb_ProxyObjectWithResult
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=5191f5de3eca0919d8d5e44823dbef1bf6b74270 translatedAt=2026-11-04T11:54:40.239Z pushedAt=2026-11-04T11:55:33.793Z nl=1 -->

```c
typedef struct {...} ArkWeb_ProxyObjectWithResult
```

## Overview

ArkWeb_ProxyObjectWithResult is a JavaScript proxy object struct with a return value, extending the capabilities of ArkWeb_ProxyObject. This struct organizes multiple ArkWeb_ProxyMethodWithResult instances into an object and injects it into a web page, allowing JavaScript to obtain a return value after calling Native methods. It resolves the issue that ArkWeb_ProxyObject cannot return execution results, simplifying the development process and improving development efficiency. It is suitable for API scenarios that require returning structured execution results to the web frontend.

**Since**: 18

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_type.h](capi-arkweb-type-h.md)

## Total

### Member Variables

| Name                                                | Description|
|----------------------------------------------------| -- |
| const char* objName | Name of the injected object, used to reference the object when JavaScript calls it. The naming must follow JavaScript identifier rules, and special characters are not supported. |
| const [ArkWeb_ProxyMethodWithResult](capi-web-arkweb-proxymethodwithresult.md)* methodList | Array of method structs carried by the injected object. The array length is specified by the **size** parameter. Each method in the array is registered to the web page, and JavaScript can call it in the format of "objectName.methodName". |
| size_t size | Length of the method struct array, that is, the number of elements in the array. This value must be consistent with the actual length of the **methodList** array. The minimum value is 0, and the maximum value depends on system resource limits. |


