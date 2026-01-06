# 日历服务错误码

<!--Kit: Calendar Kit-->
<!--Subsystem: Applications-->
<!--Owner: @qq_42718467-->
<!--Designer: @huangxinwei-->
<!--Tester: @z30055209-->
<!--Adviser: @ge-yafang-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 23900001 参数值错误

**错误信息**

Parameter value error.

**错误描述**

参数值错误。

**可能原因**

1. 参数为字串时，长度超范围。

2. 参数值超范围。

**处理步骤**

1. 检查参数字串长度是否超范围。

2. 检查参数值是否超范围。

## 23900003 未找到指定的账户

**错误信息**

The specified account was not found.

**错误描述**

未找到指定的账户。

**可能原因**

输入账号与创建的账户不一致，导致查询的账户不存在。

**处理步骤**

确保使用已创建的账户，不要使用未创建的账户。

## 23900004 内部程序错误

**错误信息**

Internal program error. Possible causes:1. dataShare database execution error;2. null pointer error; 3. Data parsing error.

**错误描述**

内部程序错误。

**可能原因**

1. 数据共享数据库执行错误。

2. 空指针错误。

3. 数据解析错误。

**处理步骤**

1. 根据数据共享数据库执行错误，上报对应的开发人员。

2. 根据空指针错误，上报对应的开发人员。

3. 根据数据解析错误，上报对应的开发人员。