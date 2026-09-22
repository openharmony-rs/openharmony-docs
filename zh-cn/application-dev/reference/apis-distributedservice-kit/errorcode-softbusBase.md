# 设备感知错误码
<!--Kit: Distributed Service Kit-->
<!--Subsystem: Communication-->
<!--Owner: @Lucky-M-->
<!--Designer: @Lucky-M-->
<!--Tester: @openharmony_ci-->
<!--Adviser: @hu-zhiqiong-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 2000001 内部错误

**错误信息**

Internal error.

**错误描述**

内部错误，系统出现非预期错误。

**可能原因**

软总线服务异常、内存申请失败等系统内部错误。

**处理步骤**

确认软总线服务是否正常运行后重试；若持续失败，请重启设备或抓取 hilog 日志反馈。

## 2000002 调用顺序错误

**错误信息**

Caller error.

**错误描述**

调用方未按指定顺序调用接口。

**可能原因**

未先调用 [startPerceptionScan](js-apis-softbusBase-sys.md#softbusbasestartperceptionscan) 启动扫描，或在调用 [stopPerceptionScan](js-apis-softbusBase-sys.md#softbusbasestopperceptionscan) 停止扫描后，再调用 [getPerceptionDeviceList](js-apis-softbusBase-sys.md#softbusbasegetperceptiondevicelist) 获取设备列表。

**处理步骤**

先调用 startPerceptionScan 启动扫描，再调用 getPerceptionDeviceList；停止扫描后不再查询设备列表。

## 2000003 临时错误

**错误信息**

Temporary error.

**错误描述**

临时错误，请求因临时性错误失败，可重试。

**可能原因**

系统资源繁忙、底层瞬时不可用等临时性错误。

**处理步骤**

稍后重试该接口调用。

## 2006001 底层模块错误

**错误信息**

Underlying module error.

**错误描述**

底层模块错误，请求因其他底层模块错误失败，可间隔一段时间后重试。

**可能原因**

依赖的底层模块（如蓝牙、传输等）发生错误。

**处理步骤**

间隔一段时间后重试；若持续失败，请确认底层模块（如蓝牙）是否已正常开启，并抓取 hilog 日志反馈。
