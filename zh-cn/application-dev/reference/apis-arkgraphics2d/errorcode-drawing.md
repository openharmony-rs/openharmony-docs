# 图形绘制与显示错误码
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 25900001 参数值异常

**错误信息**

The parameter value is out of range.

**错误描述**

当参数值超过出参数范围要求时，系统会报此错误码。

**可能原因**

参数值超出接口调用范围会报错，如枚举值超出定义范围。

**处理步骤**

在定义接口参数前，确保参数值符合接口参数要求。