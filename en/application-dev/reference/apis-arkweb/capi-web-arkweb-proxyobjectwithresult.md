# ArkWeb_ProxyObjectWithResult

## Overview

Defines a proxy object to be injected.

**Since**: 18

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_type.h](capi-arkweb-type-h.md)

## Total

### Member Variables

| Name                                                | Description|
|----------------------------------------------------| -- |
| const char* objName                                | Pointer to the object name to be injected.|
| const [ArkWeb_ProxyMethodWithResult](capi-web-arkweb-proxymethodwithresult.md)* methodList | Pointer to the method struct array of an object to be injected.|
| size_t size                                        | Length of the method struct array.|
