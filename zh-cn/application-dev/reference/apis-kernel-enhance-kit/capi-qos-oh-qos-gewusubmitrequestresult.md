# OH_QoS_GewuSubmitRequestResult
<!--Kit: Kernel Enhance Kit-->
<!--Subsystem: Kernel-->
<!--Owner: @gatieme-->
<!--Designer: @tanyihua-->
<!--Tester: @panny060-->
<!--Adviser: @fang-jinxu-->

## 概述
OH_QoS_GewuSubmitRequest()接口的返回结果，成功时返回请求的 request，失败时 error 会置为对应的错误码 。

**起始版本：** 20

**相关模块：** [QoS](capi-qos.md)

**所在头文件：** [qos.h](capi-qos-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| OH_QoS_GewuRequest request | 创建出来的请求句柄 |
| [OH_QoS_GewuErrorCode](capi-qos-h.md#oh_qos_gewuerrorcode) error | 错误码。- 请求提交成功返回OH_QOS_GEWU_OK。- 由于没有足够的内存而创建会话失败返回OH_QOS_GEWU_NOMEM。 |


