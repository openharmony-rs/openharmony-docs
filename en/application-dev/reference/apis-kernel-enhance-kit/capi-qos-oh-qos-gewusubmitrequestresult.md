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
Return result of the **OH_QoS_GewuSubmitRequest()** API, used to obtain the submission status and result of a Gewu inference request. (The Gewu service is an on-device AI inference acceleration service.) Upon successful submission, the `request` field contains the created request handle, which can be used to cancel the request later. Upon failure, the `error` field stores the error code, helping you take appropriate action based on the specific error cause. This struct is applicable in scenarios where you need to determine whether a submitted on-device AI inference request has been successfully admitted into the session and obtain the request handle.

**Since**: 20

**Related module**: [QoS](capi-qos.md)

**Header file**: [qos.h](capi-qos-h.md)

## Summary

### Member Variables

| Name| Type| Description|
| -- | -- | -- |
| request | [OH_QoS_GewuRequest](capi-qos-h.md#oh_qos_gewurequest) | Request handle created after the request is successfully submitted. It can be used to cancel the request later. This parameter is valid only when `error` is `OH_QOS_GEWU_OK`. If the operation fails, this parameter is invalid.|
| error | [OH_QoS_GewuErrorCode](capi-qos-h.md#oh_qos_gewuerrorcode) | Error code.<br>- `OH_QOS_GEWU_OK`: The request is submitted successfully.<br>- `OH_QOS_GEWU_NOMEM`: Insufficient memory. There is not enough memory to process the request. You are advised to release resources and retry.<br>- `OH_QOS_GEWU_INVAL`: Invalid parameter. The input parameter such as the session handle, request content, or callback is invalid. Verify the parameter types, formats, and values.<br>- `OH_QOS_GEWU_NOENT`: Session not found. The specified session does not exist or has been destroyed. Verify that the session has been successfully created and is still valid.<br>- `OH_QOS_GEWU_NOPERM`: Insufficient permission. The caller lacks the required permission for the API. Verify the application permission configuration.<br>- `OH_QOS_GEWU_NOSYS`: Symbol not found. The system does not support the related function or the dependent symbols are unavailable. Check system version and the status of dependent libraries.<br>The mapping between the above enumerated values and their numeric codes is as follows: OH_QOS_GEWU_OK = **0**, OH_QOS_GEWU_NOPERM = **201**, OH_QOS_GEWU_NOMEM = **203**, OH_QOS_GEWU_INVAL = **401**, `OH_QOS_GEWU_NOENT` = **502**, and OH_QOS_GEWU_NOSYS = **801**.|
