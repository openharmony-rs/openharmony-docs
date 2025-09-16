# VPN错误码

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码](../errorcode-universal.md)说明文档。

## 2203001 VPN创建失败

**错误信息**

VPN creation denied. Check the user type.

**错误描述**

拒绝创建VPN，请检测当前用户的类型。

**可能原因**

登录系统的用户类型不匹配，GUEST用户不能调用setUp接口。

**处理步骤**

检查当前登录系统用户的类型。


## 2203002 VPN已存在

**错误信息**

VPN already exists.

**错误描述**

VPN连接已存在，请先调用destroy接口销毁VPN连接。

**可能原因**

VPN已经被创建。

**处理步骤**

先执行destroy接口，再调用该接口。


## 2203004 无效描述符

**错误信息**

Invalid socket file descriptor.

**错误描述**

无效的文件描述符。

**可能原因**

tcp链路建立失败。

**处理步骤**

检查socket链路是否建立成功。

## 19900001 无效参数

**错误信息**

Invalid parameter value.

**错误描述**

无效参数。

**可能原因**

参数类型或数量错误。

**处理步骤**

请检查参数数量和类型。

## 19900002 系统内部错误

**错误信息**

System internal error.

**错误描述**

VPN系统内部错误。

**可能原因**

空指针、内存分配异常、IPC通信异常等。

**处理步骤**

检查VPN系统服务是否正常。