# Page Switch Logs

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @liuyifeifei;@buzhenwang-->
<!--Designer: @shenchenkai-->
<!--Tester: @liyang2235-->
<!--Adviser: @jinqiuheng-->

## Overview

Page switch logs record the page switching stack of an application, such as window creation and destruction, and page switching. These logs help developers analyze user operations before a fault occurs, improving fault locating efficiency.

## Obtaining Logs

If a process enables page switch logs through HiAppEvent APIs in the configuration policy of a fault event, for example, [crash event configuration policy](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md#appcrashpolicy24), HiAppEvent returns the corresponding page switch log snapshot file to the application for fault analysis when the fault occurs. The log snapshot file format is as follows:

```text
page_switch.20260324-170403-035.1.log
```

| Column 1 | Column 2 | Column 3 | Column 4 |
| -------- | -------- | -------- | -------- |
| Log prefix | Timestamp | Log ID | Log suffix |
| page_switch | 20260324-170403-035 | 1 | log |

> **NOTE**
>
> A maximum of two log snapshot files can be retained. The maximum ID is 2.

## Log Format

The log format in a log snapshot file is as follows:

```text
2026-03-24 17:03:55.361   2569   2569 Hap onBackground
```

| Column 1 | Column 2 | Column 3 | Column 4 |  Column 5 |
| -------- | -------- | -------- | -------- | -------- |
| Date | Timestamp | Process ID | Thread ID | Log content |
| 2026-03-24 | 17:03:55.361 | 2569 | 2569 | Hap onBackground |

> **NOTE**
>
> Log content supports a maximum of 1024 bytes. Content exceeding this limit is truncated.
