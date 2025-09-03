# MDNS错误码


<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码](../errorcode-universal.md)说明文档。

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

## 2204003 重复注册

**错误信息**

Callback duplicated.

**错误描述**

callback 已经存在。

**可能原因**

重复注册相同名称和类型的mDNS服务。

**处理步骤**

检查mDNS服务是否存在。

## 2204007 服务已存在

**错误信息**

Service instance duplicated.

**错误描述**

服务已存在。

**可能原因**

之前注册的服务还在运行。

**处理步骤**

检查mDNS服务是否存在。

## 2204008 删除服务失败

**错误信息**

Failed to delete the service instance.

**错误描述**

想要移除的服务不存在。

**可能原因**

之前已经把服务删除，二次删除相同服务。

**处理步骤**

检查mDNS服务是否存在。

## 2204010 发送消息失败

**错误信息**

Failed to send the message.

**错误描述**

发送信息失败。

**可能原因**

局域网内不存在该mDNS服务。

**处理步骤**

检查局域网内目标mDNS服务是否存在。

## 2204006 解析服务超时

**错误信息**

Request timeout.

**错误描述**

解析服务超时。

**可能原因**

局域网内不存在该类型的mDNS服务。

**处理步骤**

检查局域网内目标类型的mDNS服务是否存在。