# 输入设备错误码

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->

> **说明：**
>
> - 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码](../errorcode-universal.md)。

<!--Del-->
## 3900001 指定的设备不存在

**错误信息**

The specified device does not exist.

**错误描述**

指定的设备在多模设备列表中不存在。

**可能原因**

1. 输入设备的设备ID变更。
2. 输入设备的物理连接断开。

**处理步骤**

1. 通过[inputDevice.getDeviceList](js-apis-inputdevice.md#inputdevicegetdevicelist9)查询设备ID，并传入正确的设备ID。
2. 检查设备的物理连接是否断开。<!--DelEnd-->

## 3900002 键盘设备没有连接

**错误信息**

There is currently no keyboard device connected.

**错误描述**

当前未检测到已连接的键盘设备。

**可能原因**

输入设备的物理连接断开。

**处理步骤**

检查设备的物理连接是否断开。

## 3900003 非输入法应用调用

**错误信息**

It is prohibited for non-input applications.

**错误描述**

禁止非输入法应用调用此接口。

**可能原因**

非输入法应用调用此接口。

**处理步骤**

请使用输入法应用调用该接口。

<!--Del-->
## 3900004 指定的显示器不存在

**错误信息**

The specified display does not exist.

**错误描述**

指定的displayId不存在。

**可能原因**

当前设备上并没有此显示器ID。

**处理步骤**

1. 查询有效的显示器ID，并传入正确的显示器ID。
2. 检查显示器的连接状态。<!--DelEnd-->

<!--Del-->
## 3900005 不支持的输入设备

**错误信息**

Unsupported input device.

**错误描述**

不支持此外设。

**可能原因**

设置的inputDeviceId对应的外设并不是外接的USB或蓝牙外设。

**处理步骤**

请重新设置外接的USB或蓝牙外设的ID。<!--DelEnd-->

## 3800001 多模输入服务内部错误

**错误信息**

Input service exception. Possible causes: 1. Memory allocation failure. 2. Thread busy. 3. Service terminated abnormally. 4. Other unexpected errors. Try again later.

**错误描述**

多模输入服务内部错误。

**可能原因**

内存分配失败，线程繁忙，服务运行异常等非预期错误。

**处理步骤**

建议稍后重试。