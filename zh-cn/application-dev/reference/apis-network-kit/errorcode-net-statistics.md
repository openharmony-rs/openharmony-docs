# 流量管理错误码

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 2100001 无效的参数

**错误信息**

Invalid parameter value.

**错误描述**

参数输入有误。

**可能原因**

输入的结束时间小于开始时间。

**处理步骤**

检查输入的时间参数是否合理。


## 2100002 连接服务失败

**错误信息**

Failed to connect to the service.

**错误描述**

操作失败，连接系统服务发生异常。

**可能原因**

服务发生异常。

**处理步骤**

检查系统服务运行状态是否正常。

## 2100003 系统内部错误

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

## 2103005 读取系统map失败

**错误信息**

Failed to read the system map.

**错误描述**

读取系统map失败。

**可能原因**

在内核map对象上读取流量数据失败。

**处理步骤**

检查输入的网卡或应用UID是否有流量产生。

## 2103011 系统map创建失败

**错误信息**

Failed to create a system map.

**错误描述**

内核对象创建失败。

**可能原因**

网卡没有流量产生，内核流量对象还未创建。

**处理步骤**

确保网卡上有流量产生。

## 2103012 获取网卡名失败

**错误信息**

Failed to obtain the NIC name.

**错误描述**

获取网卡名失败。

**可能原因**

本机没有此网卡名。

**处理步骤**

检查传入的网卡名是否正确。

## 2103017 读取数据库失败

**错误信息**

Failed to read the database.

**错误描述**

读取数据库失败。

**可能原因**

数据库被损坏。

**处理步骤**

检查本机数据库文件是否被损坏。
