# @ohos.busManager.serial错误码

<!--Kit: Basic Services Kit-->
<!--Subsystem: BusManager-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @hwymlgitcode-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->

> **说明：**
> 
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)

## 35700001 服务异常

**错误信息**

Service error.

**错误描述**

调用串口通信相关接口时，串口通信服务内部发生异常。

**可能原因**

1. 串口通信服务未启动。

2. 串口通信服务内部异常。

**处理步骤**

1. 检查设备串口功能是否正常。

2. 重启设备后重试。

## 35700002 参数错误

**错误信息**

Invalid parameter.

**错误描述**

调用串口通信相关接口时，传入的参数不合法。

**可能原因**

1. 波特率不是正整数。

2. 写入数据长度超出范围。

3. 超时时间超出接口限定范围。

4. 参数类型错误。

**处理步骤**

1. 检查波特率是否为正整数。

2. 检查写入数据长度是否在(0, 4096]范围内。

3. 检查超时时间是否在[0, 300000]范围内。

4. 检查参数类型是否正确。

## 35700003 虚拟串口断开

**错误信息**

Virtual serial port disconnected.

**错误描述**

操作串口通信相关接口时，USB虚拟串口设备已断开连接。

**可能原因**

1. USB转串口线缆被拔出。
2. USB虚拟串口设备异常断开。

**处理步骤**

1. 检查USB转串口线缆连接是否正常。

2. 重新插拔USB设备后，重新调用[getSerialPortList](js-apis-busmanager-serial.md#serialgetserialportlist)获取设备列表，再调用[open](js-apis-busmanager-serial.md#open)接口打开设备。

## 35700004 端口已被占用

**错误信息**

Port already in use.

**错误描述**

调用[open](js-apis-busmanager-serial.md#open)接口打开串口时，串口端口已被其他应用或进程占用。

**可能原因**

1. 同一串口被其他应用打开。
2. 上次操作未正常关闭串口。

**处理步骤**

1. 关闭占用该串口的其他应用。

2. 调用[close](js-apis-busmanager-serial.md#close)关闭串口后重新打开。

## 35700005 端口未打开

**错误信息**

Port not open.

**错误描述**

操作串口通信相关接口时，串口端口未打开。

**可能原因**

1. 未调用[open](js-apis-busmanager-serial.md#open)方法打开串口。
2. 串口已被关闭。

**处理步骤**

1. 先调用[open](js-apis-busmanager-serial.md#open)方法打开串口。

2. 检查串口是否已被关闭，若已关闭则重新打开。

## 35700006 传输超时

**错误信息**

Transmission timeout.

**错误描述**

调用[write](js-apis-busmanager-serial.md#write)接口写入数据时，数据传输超时。

**可能原因**

1. 指定超时时间内数据未能写入串口。
2. 接收端设备未响应。
3. 串口通信参数配置不匹配。
4. 写入请求过于频繁，硬件发送缓冲区拥塞，导致数据来不及发送。

**处理步骤**

1. 检查接收端设备是否正常连接。

2. 适当增大超时时间参数。

3. 检查串口通信参数（波特率等）是否与对端一致。

4. 降低写入频率或在写入间调用[drain](js-apis-busmanager-serial.md#drain)接口等待前次数据发送完成后再发送。

## 35700007 用户授权被拒绝

**错误信息**

User authorization required.

**错误描述**

调用[open](js-apis-busmanager-serial.md#open)接口打开串口时，系统会校验用户是否已允许应用访问目标串口，若用户拒绝授权，则抛出该错误码。

**可能原因**

1. 用户在授权弹窗中拒绝了应用访问目标串口的请求。

**处理步骤**

1. 引导用户在授权弹窗中允许应用访问目标串口。

## 35700008 权限被拒绝

**错误信息**

Permission denied.

**错误描述**

调用[addPortAuthorization](js-apis-busmanager-serial-sys.md#serialaddportauthorization)接口时，当前应用不是串口授权弹窗应用，无权执行该操作。

**可能原因**

1. 调用方不是串口授权弹窗应用。[addPortAuthorization](js-apis-busmanager-serial-sys.md#serialaddportauthorization)接口仅允许串口授权弹窗应用调用。

**处理步骤**

1. 确认当前应用是否为串口授权弹窗应用。该接口仅允许特定的串口授权弹窗应用调用，其他应用无法使用。
