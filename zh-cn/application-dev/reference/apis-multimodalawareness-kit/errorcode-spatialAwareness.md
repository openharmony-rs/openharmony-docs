# 空间感知错误码
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @zou_ye-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码](../errorcode-universal.md)说明文档。

## 35100001 服务异常

**错误信息**

Service exception.

**错误描述**

调用distanceMeasurement模块onDistanceMeasure、 onIndoorOrOutdoorIdentify、offDistanceMeasure、offIndoorOrOutdoorIdentify接口时，若服务异常，会报此错误码。

**可能原因**

服务状态异常。

**处理步骤**

1. 定时重试操作，如间隔1s或者按照指数增长间隔重试。
2. 连续重试3次不可用则停止尝试，期间可优先尝试获取器件列表方式进一步获取设备可用性。



## 35100002 订阅失败

**错误信息**

Subscription failed.

**错误描述**

调用distanceMeasurement模块onDistanceMeasure或onIndoorOrOutdoorIdentify接口时，若订阅失败，会报此错误码。

**可能原因**

订阅异常。

**处理步骤**

1. 定时重试操作，如间隔1s或者按照指数增长间隔重试。
2. 连续重试3次不可用则停止尝试。



## 35100003 取消订阅失败

**错误信息**

Unsubscription failed.

**错误描述**

调用distanceMeasurement模块offDistanceMeasure或 offIndoorOrOutdoorIdentify接口时，若取消订阅失败，会报此错误码。

**可能原因**

取消订阅异常。

**处理步骤**

1. 定时重试操作，如间隔1s或者按照指数增长间隔重试。
2. 连续重试3次不可用则停止尝试。



## 35100004 无效参数

**错误信息**

Parameter invalid.

**错误描述**

当调用distanceMeasurement模块测距接口时，参数不满足范围，会报此错误码。

**可能原因**

参数不满足范围。

**处理步骤**

1. 参考API接口文档输入正确的参数。