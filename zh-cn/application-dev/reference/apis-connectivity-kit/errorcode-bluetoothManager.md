# 蓝牙服务子系统错误码

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @chengguohong; @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 2900001

**错误信息**

Service stopped.

**错误描述**

蓝牙服务已停止，蓝牙服务相关的接口无法调用。

**可能原因**

蓝牙服务启动异常。

**处理步骤**

重新执行打开或关闭蓝牙。

## 2900003

**错误信息**

Bluetooth disabled.

**错误描述**

蓝牙开关已关闭。

**可能原因**

蓝牙开关已关闭。

**处理步骤**

重新执行打开蓝牙开关。

## 2900004

**错误信息**

Profile not supported.

**错误描述**

配置文件是不支持的。

**可能原因**

该配置文件在当前设备环境不支持。

**处理步骤**

检查设备是否支持该配置文件功能，若不支持则停止调用。

## 2900005

**错误信息**

Device not connected.

**错误描述**

该设备蓝牙未连接。

**可能原因**

设备配对异常。

**处理步骤**

重新打开蓝牙开关，执行配对流程。

## 2900006

**错误信息**

The maximum number of connections has been reached.

**错误描述**

超过最大连接数量。

**可能原因**

超出设备最大连接数量。

**处理步骤**

检查已配对设备数量，是否超出阈值。

## 2900007

**错误信息**

Asynchronous interface invoking timeout.

**错误描述**

异步接口调用超时。

**可能原因**

远端设备无响应。

**处理步骤**

超时后重试；若和远端设备存在链路，可以断开后，再重试。

## 2900008

**错误信息**

The value of proxy is a null pointer.

**错误描述**

pimpl或proxy为空。

**可能原因**

设备配对异常。

**处理步骤**

重新打开蓝牙开关，执行配对流程。

## 2900009

**错误信息**

Fails to start scan as it is out of hardware resources.

**错误描述**

由于硬件资源不足，无法启动本次扫描。

**可能原因**

当前系统中本应用或其他应用已启动的扫描通道过多，导致硬件资源不足。

**处理步骤**

本应用未启动过扫描，可重新关开蓝牙，释放其他应用占用的扫描资源；
本应用已启动过其他通道的扫描，可调用停止扫描接口，停止其他已启动的扫描，释放硬件资源后再重新启动本次扫描。

## 2900010

**错误信息**

Resources have reached the upper limit.

**错误描述**

资源达到上限。

**可能原因**

应用申请资源过多，需要释放资源。

**处理步骤**

调用对应接口释放资源。

## 2900011

**错误信息**

The operation is busy. The last operation is not complete.

**错误描述**

操作忙碌，上一个执行的操作还未完成。

**可能原因**

上一个执行的操作还未完成即执行本次操作，例如[readCharacteristicValue](js-apis-bluetooth-ble.md#readcharacteristicvalue)未结束即进行下一次操作。
其他涉及的接口有[writeCharacteristicValue](js-apis-bluetooth-ble.md#writecharacteristicvalue)、[readDescriptorValue](js-apis-bluetooth-ble.md#readdescriptorvalue)、[writeDescriptorValue](js-apis-bluetooth-ble.md#writedescriptorvalue)、[getRssiValue](js-apis-bluetooth-ble.md#getrssivalue)、[setCharacteristicChangeNotification](js-apis-bluetooth-ble.md#setcharacteristicchangenotification)、[setCharacteristicChangeIndication](js-apis-bluetooth-ble.md#setcharacteristicchangeindication)，如调用未完成均可能阻塞下一次操作。

**处理步骤**

异步接口需等待callback或promise返回后再执行下一次操作。

## 2900013

**错误信息**

The user does not respond.

**错误描述**

用户未回复前置操作。

**可能原因**

用户在一定时间内未执行规定操作，导致前置操作超时。

**处理步骤**

重新执行前置操作。

## 2900014

**错误信息**

User refuse the action.

**错误描述**

用户执行拒绝操作。

**可能原因**

用户拒绝前置操作的请求。

**处理步骤**

重新执行前置操作。

## 2900099

**错误信息**

Operation failed.

**错误描述**

操作失败。

**可能原因**

该配置文件在当前设备环境不支持。

**处理步骤**

请重试该操作。

## 2900100

**错误信息**

IPC failed.

**错误描述**

IPC 数据传输失败。

**可能原因**

数据传入异常。

**处理步骤**

请检查传入数据。

## 2901000

**错误信息**

Read forbidden.

**错误描述**

禁止读操作。

**可能原因**

无读操作权限。

**处理步骤**

检查是否有读操作权限。

## 2901001

**错误信息**

Write forbidden.

**错误描述**

禁止写操作。

**可能原因**

无写操作权限。

**处理步骤**

检查是否有写操作权限。

## 2901003

**错误信息**

The connection is not established.

**错误描述**

GATT未连接。

**可能原因**

GATT处于未连接的状态下执行操作，例如调用[getServices](js-apis-bluetooth-ble.md#getservices)和[readCharacteristicValue](js-apis-bluetooth-ble.md#readcharacteristicvalue)。

**处理步骤**

确保GATT处于已连接的状态。

## 2901004

**错误信息**

The connection is congested.

**错误描述**

GATT处于拥塞状态。

**可能原因**

读写特征值或描述符过于频繁，导致底层数据传输拥塞，例如入参[GattWriteType](js-apis-bluetooth-ble.md#gattwritetype)为WRITE_NO_RESPONSE的[writeCharacteristicValue](js-apis-bluetooth-ble.md#writecharacteristicvalue)接口调用过于频繁可能导致拥塞。

**处理步骤**

降低读写操作频率，如果是WRITE_NO_RESPONSE类型的写数据操作，建议调用间隔控制在50ms以上。

## 2901005

**错误信息**

The connection is not encrypted.

**错误描述**

GATT处于未加密的状态下，执行需要加密权限的特征值或描述符读写操作。此操作是否需要加密由server端特征值或描述符的权限指定。

**可能原因**

GATT加密权限不足。

**处理步骤**

检查GATT是否有加密权限。

## 2901006

**错误信息**

The connection is not authenticated.

**错误描述**

GATT处于未认证的状态下，执行需要认证权限的特征值或描述符读写操作。此操作是否需要加密由server端特征值或描述符的权限指定。

**可能原因**

GATT认证权限不足。

**处理步骤**

检查与对端设备是否配对，是否有认证权限。

## 2901007

**错误信息**

The connection is not authorized.

**错误描述**

GATT处于未授权的状态下，执行需要授权的特征值或描述符读写操作。此操作是否需要授权由server端特征值或描述符的权限指定。

**可能原因**

GATT未授权。

**处理步骤**

检查GATT是否已授权。

## 2901054

**错误信息**

IO error.

**错误描述**

IO传输失败。

**可能原因**

IO传输异常，造成失败。

**处理步骤**

请重试该操作。

## 2902050

**错误信息**

Failed to start scan as Ble scan is already started by the app.

**错误描述**

开启扫描失败。

**可能原因**

Ble扫描已被app开启。

**处理步骤**

检查是否已经开启扫描。

## 2902054

**错误信息**

The length of the advertising data exceeds the upper limit.

**错误描述**

广播报文超过最大长度。

**可能原因**

传统广播报文的最大长度为31字节，超过此长度将返回异常。当前，该长度限制仅适用于传统广播，不包括扩展广播。

**处理步骤**

检查广播报文是否超过最大长度限制。

## 2902055

**错误信息**

Invalid advertising id.

**错误描述**

广播标识符无效。

**可能原因**

传入的广播标识符应为[startAdvertising](js-apis-bluetooth-ble.md#blestartadvertising11)接口返回的值，无效的广播标识符默认为0xFF。

**处理步骤**

检查传入的广播标识符是否为[startAdvertising](js-apis-bluetooth-ble.md#blestartadvertising11)接口返回的有效标识符。
