# 用户首选项错误码

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 15500000 内部错误
**错误信息**

Inner error.

**错误描述**

用户首选项内部发生错误。

**可能原因**

读写持久化文件失败。

**处理步骤**

需通过日志信息确认错误发生原因或者寻找开发人员支持。

## 15500010 删除用户首选项持久化文件失败
**错误信息**

Failed to delete preferences file.

**错误描述**

删除用户首选项持久化文件失败。

**可能原因**

系统错误导致文件删除失败，可能原因如下：
1. 文件名称不正确。
2. 文件路径不正确。

**处理步骤**

1. 检查文件名称是否正确。
2. 检查文件路径是否正确。

## 15500019 获取订阅服务失败

**错误信息**

Failed to obtain subscription service.

**错误描述**

进行进程间订阅时，获取订阅服务失败。

**可能原因**

当前平台不支持订阅服务。

**处理步骤**

需要在当前平台部署订阅服务。

## 15501001 上下文环境非Stage模型

**错误信息**

 Only supported in stage mode.

**错误描述**

该操作仅支持Stage模型。

**可能原因**

当前上下文环境非Stage模型。

**处理步骤**

请切换当前上下文环境，使用Stage模型。

## 15501002 Options中传入的dataGroupId参数非法

**错误信息**

The data group id is not valid.

**错误描述**

使用非法dataGroupId参数。

**可能原因**

使用的dataGroupId不是从应用市场正常申请的。

**处理步骤**

应用从应用市场申请dataGroupId，并正确传入该参数。