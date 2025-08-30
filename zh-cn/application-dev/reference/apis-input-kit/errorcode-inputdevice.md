# 输入设备错误码

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

<!--Del-->
## 3900001 指定的设备不存在

**错误信息**

The specified device does not exist.

**错误描述**

指定的设备在多模设备列表中不存在。

**可能原因**

1. 输入设备的设备id变更。
2. 输入设备的物理连接断开。

**处理步骤**

1. 通过[inputDevice.getDeviceList](js-apis-inputdevice.md#inputdevicegetdevicelist9)查询设备id，并传入正确的设备id。
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