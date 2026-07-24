# 属性字符串错误码
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hddgzw-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

属性字符串错误码定义了属性字符串在转换、解码、序列化等操作过程中可能出现的错误信息及对应的处理建议，帮助开发者快速定位和解决属性字符串相关问题。

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 170001 转换错误

**错误信息**

Convert Error.

**错误描述**

fromHtml无法将传入的字符串转换为属性字符串。

**可能原因**

字符串为空或字符串不符合HTML格式。

**处理步骤**

1. 检查传入的字符串是否为空，如果为空，请传入有效的非空字符串。
2. 确认字符串是否符合HTML格式要求，如果不符合，请修改为符合HTML格式的字符串后重新调用。

<!--Del-->
## 170002 属性字符串解码错误

**错误信息**

Styled string decode error.

**错误描述**

unmarshalling无法将传入的字节反序列化为属性字符串。

**可能原因**

传入的字节不符合属性字符串序列化的格式要求。

**处理步骤**

NA
<!--DelEnd-->

## 180101 无效的属性字符串

**错误信息**

invalid styled string.

**错误描述**

在属性字符串序列化CAPI中，ArkUI_StyledString_Descriptor的属性字符串对象为空。

**可能原因**

参数中传递的属性字符串为空。

**处理步骤**

1. 检查ArkUI_StyledString_Descriptor中的属性字符串对象是否已正确初始化。
2. 确认在调用相关接口时，属性字符串对象未被设置为空。