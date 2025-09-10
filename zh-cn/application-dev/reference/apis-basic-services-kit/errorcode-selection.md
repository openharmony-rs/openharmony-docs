# 划词服务错误码

<!--Kit: Basic Services Kit-->
<!--Subsystem: SelectionInput-->
<!--Owner: @no86-->
<!--Designer: @mmwwbb-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 33600001 划词服务异常

**错误信息**

Selection service exception.

**错误描述**

划词服务异常时，会报此错误码。

**可能原因**

当划词应用调用此接口，若划词服务或其依赖的服务出现异常，系统将返回此错误码。

**处理步骤**

建议重启设备后重新调用接口。

## 33600002 此划词窗口已被销毁

**错误信息**

This selection window has been destroyed.

**错误描述**

此划词窗口已被销毁。

**可能原因**

1. 划词窗口已被销毁。
2. 划词窗口未被创建。

**处理步骤**

1. 在操作划词窗口前，检查窗口对象是否有效。
2. 避免操作已销毁的窗口对象。

## 33600003 无效的划词应用

**错误信息**

Invalid operation. The selection app is not valid.

**错误描述**

非法操作，划词应用无效。

**可能原因**

非用户选择的划词应用调用了划词接口。

**处理步骤**

在系统设置中检查当前的划词应用是否为本应用。
