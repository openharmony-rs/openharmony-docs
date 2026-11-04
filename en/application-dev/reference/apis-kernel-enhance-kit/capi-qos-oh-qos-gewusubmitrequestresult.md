# OH_QoS_GewuSubmitRequestResult
<!--Kit: Kernel Enhance Kit-->
<!--Subsystem: Kernel-->
<!--Owner: @gatieme-->
<!--Designer: @tanyihua-->
<!--Tester: @panny060-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=44f696abae3c115f1176591a2964d5afb84358b9 translatedAt=2026-11-04T01:24:03.262Z pushedAt=2026-11-04T03:24:28.471Z nl=1 -->

```c
typedef struct { ... } OH_QoS_GewuSubmitRequestResult
```

## Overview
The return result of the OH_QoS_GewuSubmitRequest() API, used to obtain the submission status and result of an inference request of the Gewu service (an on-device AI inference acceleration service). When the request is submitted successfully, the `request` field contains the created request handle, which can be used to abort the request later. When the request fails, the `error` field stores the error code, allowing developers to handle the issue based on the specific error cause. This struct is applicable to the scenario of determining whether a request has successfully entered a session and obtaining the request handle after submitting an on-device AI inference request.

**Since**: 20

**Related module**: [QoS](capi-qos.md)

**Header file**: [qos.h](capi-qos-h.md)

## Summary

### Member Variables

| Name | Type | Description |
| -- | -- | -- |
| request | [OH_QoS_GewuRequest](capi-qos-h.md#oh_qos_gewurequest) | Request handle created after the request is submitted successfully. It can be used to abort the request later. This field is valid only when `error` is `OH_QOS_GEWU_OK`; it is invalid when the request fails. |
| error | [OH_QoS_GewuErrorCode](capi-qos-h.md#oh_qos_gewuerrorcode) | Error code.<br>- `OH_QOS_GEWU_OK`: The request is submitted successfully.<br>- `OH_QOS_GEWU_NOMEM`: Insufficient memory, indicating that there is not enough memory to process the request. Release resources and retry.<br>- `OH_QOS_GEWU_INVAL`: Invalid parameter, indicating that the passed session handle, request content, or callback is invalid. Check the parameter type, format, and value.<br>- `OH_QOS_GEWU_NOENT`: Session not found, indicating that the specified session does not exist or has been destroyed. Check whether the session has been created successfully and is still valid.<br>- `OH_QOS_GEWU_NOPERM`: Insufficient permission, indicating that the caller lacks the permission required by the API. Check the application permission configuration.<br>- `OH_QOS_GEWU_NOSYS`: Subsystem not found, indicating that the system does not support the related function or the dependent subsystem is unavailable. Check the system version and the status of dependent libraries.<br>The mapping between the above enum values and numbers: `OH_QOS_GEWU_OK`=0, `OH_QOS_GEWU_NOPERM`=201, `OH_QOS_GEWU_NOMEM`=203, `OH_QOS_GEWU_INVAL`=401, `OH_QOS_GEWU_NOENT`=502, `OH_QOS_GEWU_NOSYS`=801. |


