# 以太网连接错误码


<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码](../errorcode-universal.md)说明文档。

## 2200001 非法参数值

**错误信息**

Invalid parameter value.

**错误描述**

非法参数值。

**可能原因**

输入参数取值范围错误。

**处理步骤**

检查输入参数的取值范围是否正确。

## 2200002 连接服务失败

**错误信息**

Failed to connect to the service.

**错误描述**

操作失败，连接系统服务发生异常。

**可能原因**

服务发生异常。

**处理步骤**

检查系统服务运行状态是否正常。

## 2200003 系统内部错误

**错误信息**

System internal error.

**错误描述**

系统内部错误。

**可能原因**

1.内存异常。

2.空指针。

**处理步骤**

1.检查内存空间是否充足，清理内存后重试。

2.系统异常，请稍后重试或重启设备。

## 2201005 设备信息不存在

**错误信息**

The device information does not exist.

**错误描述**

设备信息不存在。

**可能原因**

设置的设备或者获取的设备不存在。

**处理步骤**

```
> hdc shell ifconfig
```
查看是否有对应的设备，比如eth0，eth1。

## 2201006 设备未连接

**错误信息**

Device disconnected.

**错误描述**

设备未连接。

**可能原因**

硬件网卡问题。

**处理步骤**

需要查看以太网服务和底层netsys的log，查看kernel是否有上报连接状态。

## 2201007 用户配置写入失败

**错误信息**

Failed to write the user configuration.

**错误描述**

写入配置文件信息失败。

**可能原因**

系统报错。

**处理步骤**

系统内部错误，出现的情况不明确，建议通过日志定位问题。
