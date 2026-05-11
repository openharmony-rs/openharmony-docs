# 页面切换日志

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @liuyifeifei;@buzhenwang-->
<!--Designer: @shenchenkai-->
<!--Tester: @liyang2235-->
<!--Adviser: @jinqiuheng-->

## 简介

页面切换日志用于记录应用页面切换栈，比如窗口创建销毁、页面切换等信息，帮助开发者通过该日志分析故障发生前用户操作，提高问题定位效率。

## 日志获取

如果进程通过hiappevent接口在某故障事件配置策略中，使能页面切换日志，例如[崩溃事件配置策略](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md#appcrashpolicy24)，当应用发生该故障时，hiappevent会将对应的页面切换日志快照文件返回给应用用于故障分析，日志快照文件格式如下所示：

```text
page_switch.20260324-170403-035.1.log
```

| 第一列 | 第二列 | 第三列 | 第四列 |
| -------- | -------- | -------- | -------- |
| 日志前缀 | 时间戳 | 日志ID | 日志后缀 |
| page_switch | 20260324-170403-035 | 1 | log |

> **说明：**
>
> 日志快照最多保存两个文件，ID最大值2。

## 日志格式

日志快照文件中日志格式如下所示：

```text
2026-03-24 17:03:55.361   2569   2569 Hap onBackground
```
| 第一列 | 第二列 | 第三列 | 第四列 |  第五列 |
| -------- | -------- | -------- | -------- | -------- |
| 日期 | 时间戳 | 进程号 | 线程号 | 日志内容 |
| 2026-03-24 | 17:03:55.361 | 2569 | 2569 | Hap onBackground |

> **说明：**
>
> 日志内容最多支持1024字节，超出截断处理。