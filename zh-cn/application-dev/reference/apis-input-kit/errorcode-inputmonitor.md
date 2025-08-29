# 按键前置监听错误码

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 4100001 按键不支持前置监听

**错误信息**

Event listening not supported for the key.

**错误描述**

事件监听不支持该按键。

**可能原因**

需要监听的按键当前接口不支持。

**处理步骤**

检查传入的按键值是否支持监听，当前仅支持监听META_LEFT键、META_RIGHT键、电源键、音量键。