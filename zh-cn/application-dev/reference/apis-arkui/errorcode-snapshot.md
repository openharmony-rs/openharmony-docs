# 截图错误码
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiangtao92-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 160001 图像加载错误

**错误信息**

An image component in builder is not ready for taking a snapshot. The check for the ready state is required when the checkImageStatus option is enabled.

**错误描述**

图像加载错误。

**可能原因**

在进行截图操作前，若Image组件解码检查失败或节点图像加载失败。此时，调用截图接口，将可能触发相应的错误码。

**处理步骤**

NA

## 160002 截图超时

**错误信息**

Timeout.

**错误描述**

图像加载超时。

**可能原因**

系统任务未执行。

**处理步骤**

NA