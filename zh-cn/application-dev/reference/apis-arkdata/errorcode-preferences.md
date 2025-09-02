# 用户首选项错误码
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @yanhuii-->
<!--Designer: @houpengtao1-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 15500000 内部错误
**错误信息**

Inner error.

**错误描述**

用户首选项内部发生错误。

**可能原因**

优先查看错误日志，通过日志可以详细了解错误原因，主要有以下几种：
1. 内部状态异常。
2. 错误地使用接口。
3. 系统错误，如内存不足、I/O错误、JS引擎异常等。

**处理步骤**

1. 开发者排查是否存在对象关闭后再使用。
2. 开发者排查是否按接口文档正确使用接口。
3. 尝试重试，如果依然无法解决，可以提示用户重启应用、升级应用或升级设备版本。

## 15500010 删除用户首选项持久化文件失败
**错误信息**

Failed to delete the user preferences persistence file.

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

Failed to obtain the subscription service.

**错误描述**

进行进程间订阅时，获取订阅服务失败。

**可能原因**

当前平台不支持订阅服务。

**处理步骤**

需要在当前平台部署订阅服务。

## 15501001 上下文环境非Stage模型

**错误信息**

The operations is supported in stage mode only.

**错误描述**

该操作仅支持Stage模型。

**可能原因**

当前上下文环境非Stage模型。

**处理步骤**

请切换当前上下文环境，使用Stage模型。

## 15501002 Options中传入的dataGroupId参数非法

**错误信息**

Invalid dataGroupId.

**错误描述**

使用非法dataGroupId参数。

**可能原因**

使用的dataGroupId不是从应用市场正常申请的。

**处理步骤**

应用从应用市场申请dataGroupId，并正确传入该参数。