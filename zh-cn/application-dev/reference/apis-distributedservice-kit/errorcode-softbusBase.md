# 设备感知错误码
<!--Kit: Distributed Service Kit-->
<!--Subsystem: Communication-->
<!--Owner: @Lucky-M-->
<!--Designer: @Lucky-M-->
<!--Tester: @openharmony_ci-->
<!--Adviser: @hu-zhiqiong-->

设备感知模块提供基于软总线的设备发现与感知能力，支持扫描周边设备并获取感知设备列表，适用于设备互联、分布式业务等需要发现周边设备的场景。

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 2000001 内部错误

**错误信息**

Internal error.

**错误描述**

内部错误，系统出现非预期错误，请求失败。

**可能原因**

软总线服务异常、内存申请失败等系统内部错误。

**处理步骤**

确认软总线服务是否正常运行后重试；若持续失败，请重启设备或抓取 hilog 日志反馈。

## 2000002 调用顺序错误

**错误信息**

Caller error.

**错误描述**

调用方未按指定顺序调用接口，请求失败。

**可能原因**

未先调用 [startPerceptionScan](js-apis-softbusBase-sys.md#softbusbasestartperceptionscan) 启动扫描，或在调用 [stopPerceptionScan](js-apis-softbusBase-sys.md#softbusbasestopperceptionscan) 停止扫描后，再调用 [getPerceptionDeviceList](js-apis-softbusBase-sys.md#softbusbasegetperceptiondevicelist) 获取设备列表。

**处理步骤**

先调用 startPerceptionScan 启动扫描，再调用 getPerceptionDeviceList 获取设备列表；停止扫描后不再查询设备列表。

## 2000003 临时错误

**错误信息**

Temporary error.

**错误描述**

临时错误，请求因临时性原因失败，可重试。

**可能原因**

系统资源繁忙、底层瞬时不可用等临时错误。

**处理步骤**

建议等待3～5秒后重试该接口调用；若持续失败，请抓取 hilog 日志反馈。

## 2006001 底层模块错误

**错误信息**

Underlying module error.

**错误描述**

底层模块错误，请求因其他底层模块异常失败，可间隔30秒后重试。

**可能原因**

依赖的底层模块（如蓝牙、传输等）发生错误。

**处理步骤**

间隔30秒后重试；若持续失败，请确认底层模块（如蓝牙）是否已正常开启，并抓取 hilog 日志反馈。
