# OH_QoS_GewuSubmitRequestResult
<!--Kit: Kernel Enhance Kit-->
<!--Subsystem: Kernel-->
<!--Owner: @gatieme-->
<!--Designer: @tanyihua-->
<!--Tester: @panny060-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct { ... } OH_QoS_GewuSubmitRequestResult
```

## Overview
Defines a struct for the return results of the **OH_QoS_GewuSubmitRequest()** API. If the operation is successful, the request is returned. If the operation fails, the corresponding error code is returned.

**Since**: 20

**Related module**: [QoS](capi-qos.md)

**Header file**: [qos.h](capi-qos-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| OH_QoS_GewuRequest request | Defines the created request handle.|
| [OH_QoS_GewuErrorCode](capi-qos-h.md#oh_qos_gewuerrorcode) error | Defines the error code. - If the request is successfully submitted, **OH_QOS_GEWU_OK** is returned. - If the session fails to be created due to insufficient memory, **OH_QOS_GEWU_NOMEM** is returned.|
