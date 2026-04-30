# Contacts错误码

<!--Kit: Contacts Kit-->
<!--Subsystem: Applications-->
<!--Owner: @librahCode-->
<!--Designer: @jiayanhong-hw-->
<!--Tester: @shangzhijie-->
<!--Adviser: @zhang_yixin13-->
> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 16700001 系统内部错误

**错误信息**

general error.

**错误描述**

系统内部错误。

**可能原因**

系统内部处理异常。

**处理步骤**

系统异常，请稍后重试。



## 16700002 参数检查失败

**错误信息**

Invalid parameter value.

**错误描述**

参数校验失败。

**可能原因**

1. 空参数错误 (Null Argument Error)。

2. 参数格式错误 (Format Error)。

3. 参数值范围错误 (Value Range Error)。

**处理步骤**

请阅读参数规格约束，按照可能原因进行排查。



## 16700101 查询数据库失败

**错误信息**

Failed to get value from contacts data.

**错误描述**

查询数据库失败。

**可能原因**

数据库操作失败。

**处理步骤**

当前访问数据库失败，请稍后重试。



## 16700102 增删改数据库失败

**错误信息**

Failed to set value to contacts data.

**错误描述**

增删改数据库失败。

**可能原因**

数据库操作失败。

**处理步骤**

当前访问数据库失败，请稍后重试。



## 16700103 用户取消

**错误信息**

User canceled.

**错误描述**

用户取消。

**可能原因**

用户取消本次操作。

**处理步骤**

当前用户主动取消操作，请稍后重试。



## 401 打开联系人头像文件失败

**错误信息**

Failed to open contact portrait file.

**错误描述**

无法打开联系人头像文件。

**可能原因**

头像文件路径错误、文件不存在、磁盘损坏。

**处理步骤**

检查文件是否存在。



## 401 系统内部错误

**错误信息**

Internal error. Invalid contact id. Failed to generate contact profile.

**错误描述**

内部关联联系人id无效。

**可能原因**

系统内部处理异常。

**处理步骤**

系统异常，请稍后重试。

**错误信息**

Internal error. Failed to save contact portrait.

**错误描述**

保存联系人头像失败。

**可能原因**

头像文件异常、系统内部处理异常。

**处理步骤**

检查文件。

**错误信息**

Internal error. The query resultSet is nullptr.

**错误描述**

数据库查询插入结果集为空指针。

**可能原因**

系统内部处理异常。

**处理步骤**

系统异常，请稍后重试。

**错误信息**

Internal error. The query resultSet is empty.

**错误描述**

数据库查询插入结果集存在但无数据。

**可能原因**

系统内部处理异常。

**处理步骤**

系统异常，请稍后重试。

**错误信息**

Internal error. Invalid contact rawId.

**错误描述**

内部关联联系人rawId无效。

**可能原因**

系统内部处理异常。

**处理步骤**

系统异常，请稍后重试。
