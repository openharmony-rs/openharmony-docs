# ArkWeb_ProxyObjectWithResult

```c
typedef struct ArkWeb_ProxyObjectWithResult {...} ArkWeb_ProxyObjectWithResult
```

## Overview

ArkWeb_ProxyObjectWithResult is a JavaScript proxy object struct with a return value, extending the capabilities of ArkWeb_ProxyObject. This struct organizes multiple ArkWeb_ProxyMethodWithResult instances into an object and injects it into a web page, allowing JavaScript to obtain a return value after calling Native methods. It resolves the issue that ArkWeb_ProxyObject cannot return execution results, simplifying the development process and improving development efficiency. It is suitable for API scenarios that require returning structured execution results to the web frontend.

**Since**: 18

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_type.h](capi-arkweb-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char* objName | Name of the injected object. The name must follow JavaScript identifier rules and cannot contain special characters. |
| const [ArkWeb_ProxyMethodWithResult*](capi-web-arkweb-proxymethodwithresult.md) methodList | Array of method structs carried by the injected object. The array length is specified by the **size** parameter. Each method in the array is registered to the web page, and JavaScript can call it in the format of "objectName. methodName". |
| size_t size | Length of the method struct array. Must be consistent with the actual number of elements in the methodList array. |


