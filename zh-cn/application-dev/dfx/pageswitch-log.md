# 页面切换日志

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @buzhenwang-->
<!--Designer: @shenchenkai-->
<!--Tester: @liyang2235-->
<!--Adviser: @jinqiuheng-->

## 简介

页面切换日志用于记录应用页面切换栈，比如窗口创建销毁、页面切换等信息，帮助开发者通过该日志分析故障发生前用户操作，提高问题定位效率。

## 日志获取

如果进程通过hiappevent接口在某故障事件配置策略中，使能页面切换日志，例如[崩溃事件配置策略](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md#appcrashpolicy24)，当应用发生该故障时，hiappevent会将对应的页面切换日志快照文件返回给应用用于故障分析，日志快照文件格式如下所示：

```text
page_switch-com.example.myapplication-1-1-20260509142812417.log
```

| 第一列 | 第二列 | 第三列 | 第四列 | 第五列 | 第六列 |
| :--------: | :--------: | :--------: | :--------: | :--------: | :--------: |
| 日志前缀 | 进程名 | 实例索引 | 文件索引 | 时间戳 | 日志后缀 |
| page_switch | com.example.myapplication | 1 | 1 | 20260509142812417 | log |

> **说明：**
>
> 进程名：进程名中包含`:`、`/`、`-` 字符时，对应字符统一替换为 `_`。
>
> 实例索引：多个进程共用沙箱场景（例如[多实例](../quick-start/multiInstance.md)或[ExtensionAbility组件](../application-models/extensionability-overview.md)）会出现日志写冲突，所以页面切换日志会为每个进程创建一组日志文件，使用实例索引用于标识不同进程。取值范围：[1, 10]。
>
> 文件索引：同一进程名及实例索引下最多保留 2 个文件。取值范围：[1, 2]。
>
> 时间戳：格式为 YYYYMMDDhhmmssSSS，其中年（YYYY）占4位，月（MM）、日（DD）、时（hh）、分（mm）、秒（ss）各占2位，毫秒（SSS）占3位。

## 日志格式

日志快照文件中日志格式如下所示：

```text
2026-03-24 17:03:55.361   2569   2569 Hap onBackground
```
| 第一列 | 第二列 | 第三列 | 第四列 |  第五列 |
| :--------: | :--------: | :--------: | :--------: | :--------: |
| 日期 | 时间戳 | 进程号 | 线程号 | 日志内容 |
| 2026-03-24 | 17:03:55.361 | 2569 | 2569 | Hap onBackground |

> **说明：**
>
> 日志内容最多支持1024字节，超出截断处理。