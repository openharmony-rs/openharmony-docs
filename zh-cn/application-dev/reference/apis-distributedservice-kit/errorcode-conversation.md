# 跨设备唤醒与消息传输错误码
<!--Kit: Distributed Service Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wangrui7-->
<!--Designer: @yangyang2-->
<!--Tester: @Ytt-test-->
<!--Adviser: @hu-zhiqiong-->
> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 2000001 内部错误

**错误信息**

Internal error.

**错误描述**

内部错误

**可能原因**

对端ability拉起失败、内存申请失败等其他软总线错误。

**处理步骤**

确认对端是否安装该ability，确认软总线是否正常运行等。

## 2004001 对端设备系统版本过低

**错误信息**

Remote system version is too low.

**错误描述**

对端设备系统版本过低。

**可能原因**

对端设备系统版本过低。

**处理步骤**

升级对端设备版本。

## 2004002 对端拉起ability失败

**错误信息**

Failed to start ability on the remote side.

**错误描述**

对端拉起ability失败。

**可能原因**

传入的abilityName错误，或者对端没有该ability等。

**处理步骤**

确认abilityName是否正确。

## 2004003 发送数据失败

**错误信息**

Failed to send data.

**错误描述**

发送数据失败。

**可能原因**

发送数据失败。

**处理步骤**

确保对端同账号，确保对端deviceId正确，确保本端网络状态。

## 2004004 等待对端确认超时

**错误信息**

Timeout while waiting for acknowledgement from the remote side.

**错误描述**

等待对端确认超时。

**可能原因**

等待对端确认超时、对端关机等。

**处理步骤**

确保对端网络正常。