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

## 33600004 该接口被调用过于频繁

**错误信息**

The interface is called too frequently.

**错误描述**

该接口被调用过于频繁。

**可能原因**

该接口被调用过于频繁。在500ms内被调用超过了50次。

**处理步骤**

在收到划词通知后调用该接口。

## 33600005 接口调用时机错误

**错误信息**

The interface is called at the wrong time.

**错误描述**

在错误的时机调用了该接口。

**可能原因**

接口调用时机错误。用户此时可能未进行划词操作。

**处理步骤**

在收到划词通知后调用该接口。

## 33600006 当前应用禁止取词

**错误信息**

The current application is prohibited from accessing content.

**错误描述**

当前应用禁止划词服务取词。

**可能原因**

当前应用设置了文本内容不可出本应用。

**处理步骤**

切换到允许划词的应用后，重新调用该接口。

## 33600007 划词内容超出范围

**错误信息**

The length of selected content is out of range.

**错误描述**

选择的文本内容超出范围。

**可能原因**

当前选中了大于2000个文字的文本。

**处理步骤**

选中1到2000个文字的文本后，重新调用该接口。

## 33600008 获取内容超时

**错误信息**

Getting the selected content times out.

**错误描述**

获取选择的文本内容超时。

**可能原因**

应用返回选中文字超时。

**处理步骤**

尝试重新调用该接口。
