# 车辆感知错误码
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @ultimate_lin-->
<!--Designer: @charlie3wx-->
<!--Tester: @fhzs-->
<!--Adviser: @hu-zhiqiong-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码](../errorcode-universal.md)。

## 34000001 服务异常

**错误信息**

Service exception.

**错误描述**

调用carAwareness模块onSpatialMotion、offSpatialMotion、onRealTimeWeather、offRealTimeWeather、onRefueling、offRefueling和getAllCapabilityList接口时，若服务异常，会报此错误码。

**可能原因**

服务状态异常。

**处理步骤**

1. 定时重试操作，如间隔1s或者按照指数增长间隔重试。
2. 连续重试3次不可用则停止尝试，期间优先尝试获取设备日志进一步分析。

## 34000002 指定能力不支持

**错误信息**

Specific capability not supported.

**错误描述**

调用carAwareness模块onSpatialMotion、onRealTimeWeather、onRefueling接口时，若指定能力不支持，会报此错误码。

**可能原因**

1. 设备硬件不具备对应感知能力所需的传感器（如车外摄像头、后排摄像头等）。
2. 当前设备型号未适配该感知能力，不在能力支持列表内。
3. 传入的感知能力参数非法，不在Capability枚举的合法取值范围内。

**处理步骤**

1. 提前调用 `getAllCapabilityList` 接口查询当前设备支持的感知能力列表，确认待使用的能力在支持范围内再调用对应接口。
2. 检查传入的Capability参数是否为合法枚举值，避免拼写错误或传入未定义的取值。
3. 针对不支持该能力的设备，在业务中做降级适配，避免直接调用对应接口触发异常。

