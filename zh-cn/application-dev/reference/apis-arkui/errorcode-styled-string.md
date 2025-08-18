# 属性字符串错误码
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hddgzw-->
<!--Designer: @pssea-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @HelloCrease-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 170001 转换错误

**错误信息**

Convert Error.

**错误描述**

fromHtml无法将传入的字符串转换出对应的属性字符串。

**可能原因**

字符串为空或字符串不符合HTML格式。

**处理步骤**

NA

<!--Del-->
## 170002 属性字符串解码错误

**错误信息**

Styled string decode error.

**错误描述**

unmarshalling无法将传入的字节反序列化出对应的属性字符串。

**可能原因**

传入的字节不符合属性字符串序列化的格式导致无法反序列化。

**处理步骤**

NA
<!--DelEnd-->

## 180101 无效的属性字符串

**错误信息**

Invalid styled string.

**错误描述**

属性字符串序列化CAPI中，ArkUI_StyledString_Descriptor的属性字符串对象为空。

**可能原因**

参数中传递属性字符串有误。

**处理步骤**

检查参数中是否正确传递属性字符串。