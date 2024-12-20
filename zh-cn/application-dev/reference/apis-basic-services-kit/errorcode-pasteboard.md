# 剪贴板错误码

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 12900001 索引超过范围

**错误信息** 

The index is out of range.

**错误描述**

当调用getRecord等涉及索引的接口时，索引超过范围时，系统会报此错误码。

**可能原因**

接口的参数索引值超出当前PasteData中的记录数，比如，getRecord传入index值过大。

**处理步骤**

检查参数索引值是否在正确范围，使用恰当的索引值重新进行开发。

## 12900002 Record数量超过最大限制

**错误信息**

The number of records exceeds the upper limit.

**错误描述**

当添加Record时，若当前PasteData记录数已达到最大值，系统会报此错误码。

**可能原因**

当前PasteData记录数已达到最大值，未进行相关Record的删除或数目检查，直接继续添加Record导致。

**处理步骤**

1. 检查判断当前PasteData记录数是否已达最大值。
2. 若当前PasteData记录数已达最大值，删除相关Record后，再重新添加Record进行开发。

## 12900003 另外一个复制或粘贴正在进行

**错误信息**

Another copy or paste operation is in progress.

**错误描述**

上次的复制/粘贴动作还未结束时，再次调用相关接口，系统会报此错误码。

**可能原因**

复制粘贴均为异步接口，当复制/粘贴的数据内容较大，需要时间较长时，在此期间再次执行复制/粘贴则会出错。

**处理步骤**

1. 再次进行复制/粘贴时，首先判断上次复制/粘贴的状态。
2. 当上次复制/粘贴动作完成后，再进行后续操作。

## 12900004 禁止复制

**错误信息**

Replication is prohibited.

**错误描述**

当对不支持复制的数据内容进行复制操作时，系统会报此错误码。

**可能原因**

数据内容不支持复制，比如只读类型的数据内容。

**处理步骤**

1. 在对相关数据内容进行复制时，首先判断其数据类型是否支持复制。
2. 若数据内容不支持复制，不对此类数据内容进行复制操作。

## 12900005 请求超时

**错误信息**

Request timed out.

**错误描述**

当内部处理数据耗时过长时，系统会报此错误码。

**可能原因**

内部处理数据耗时过长，比如处理数据过大。

**处理步骤**

如果处理数据过大，建议换成异步接口。

## 12900006 设置已存在

**错误信息**

Settings already exist.

**错误描述**

当应用全局的可粘贴的范围已存在时，再次进行设置时，系统会报此错误码。

**可能原因**

应用全局的可粘贴的范围已存在。

**处理步骤**

先删除已有设置，再进行新的设置。