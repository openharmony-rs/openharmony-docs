# OH_QoS_GewuCreateSessionResult
<!--Kit: Kernel Enhance Kit-->
<!--Subsystem: Kernel-->
<!--Owner: @gatieme-->
<!--Designer: @tanyihua-->
<!--Tester: @panny060-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct { ... } OH_QoS_GewuCreateSessionResult
```

## Overview
Defines a struct for the return results of the **OH_QoS_GewuCreateSession()** API. If the operation is successful, the created session is returned. If the operation fails, the corresponding error code is returned.

**Since**: 20

**Related module**: [QoS](capi-qos.md)

**Header file**: [qos.h](capi-qos-h.md)

## Summary

### Member Variables

| Name                                                              | Description|
|------------------------------------------------------------------| -- |
| [OH_QoS_GewuSession](capi-qos-h.md#variables) session                               | Defines the created session handle.|
| [OH_QoS_GewuErrorCode](capi-qos-h.md#oh_qos_gewuerrorcode) error | Defines the error code. - If a session is successfully created, **OH_QOS_GEWU_OK** is returned. - If the session fails to be created due to insufficient memory, **OH_QOS_GEWU_NOMEM** is returned.|
