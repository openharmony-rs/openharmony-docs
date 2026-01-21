# 情景模式错误码
<!--Kit: Basic Services Kit-->
<!--Subsystem: Applications-->
<!--Owner: @chenzhe123-->
<!--Designer: @wangchun-->
<!--Tester: @RayShih-->
<!--Adviser: @fang-jinxu -->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 35200001 内部错误

**错误信息**

Internal error.

**错误描述**

多线程处理异常、内部指针校验错误等内部处理错误时，方法将返回该错误码。

**可能原因**

多线程处理、内部处理异常等内核通用错误。

**处理步骤**

确认系统资源是否足够。