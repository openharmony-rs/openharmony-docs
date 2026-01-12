# 屏上感知错误码
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @zou_ye-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码](../errorcode-universal.md)。

## 34000001 服务异常

**错误信息**

Service exception.

**错误描述**

当调用onScreen模块getPageContent或sendControlEvent接口时，如果服务异常，会报此错误码。

**可能原因**

服务状态异常。

**处理步骤**

1. 定时重试操作，如每隔1s或按指数增长间隔重试。
2. 连续重试3次不可用则停止尝试，期间优先尝试获取设备日志进一步分析。

## 34000002 应用或页面不支持

**错误信息**

The application or page is not supported.

**错误描述**

当调用onScreen模块getPageContent接口时，若应用或页面不支持，会报此错误码。

**可能原因**

应用或页面不支持该功能。

**处理步骤**

请换到支持的应用或页面再进行尝试。

## 34000003 窗口ID无效

**错误信息**

The window id is invalid.

**错误描述**

当调用onScreen模块getPageContent接口时，若窗口ID不存在，会报此错误码。

**可能原因**

1. 在分屏场景下未传入具体的window ID。
2. 传入的window ID对应的窗口未在屏幕上显示或处于悬浮状态。

**处理步骤**

1. 在分屏场景下，传入需要获取的窗口的window ID。
2. 传入正确的window ID。

## 34000004 页面未准备就绪

**错误信息**

The page is not ready.

**错误描述**

当调用onScreen模块getPageContent接口时，若页面未准备就绪，会报此错误码。

**可能原因**

页面尚未准备就绪。

**处理步骤**

在页面准备就绪后，调用接口。

## 34000005 目标未找到

**错误信息**

The target is not found.

**错误描述**

当调用onScreen模块sendControlEvent接口时，若未找到目标，会报此错误码。

**可能原因**

传入的window ID、session ID或hook ID有误，因此无法找到需要控制的目标。

**处理步骤**

请传入正确的window ID、session ID或hook ID。

## 34000006 请求超时

**错误信息**

The request timed out.

**错误描述**

当调用onScreen模块getPageContent接口时，若接口超时，会报此错误码。

**可能原因**

服务接口超时。

**处理步骤**

1. 定时重试操作，如每隔1s或按指数增长间隔重试。
2. 连续重试3次不可用则停止尝试，期间优先尝试获取设备日志进一步分析。