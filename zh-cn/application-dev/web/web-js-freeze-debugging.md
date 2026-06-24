# 定位JS代码阻塞导致的页面卡死问题
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @qq_44167590-->
<!--Designer: @hjoksky-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

## 问题描述

前端页面卡死的原因多种多样，其中一种常见原因是其中的JS代码执行时间过长，导致阻塞渲染进程，未及时送显。本文档提供此类问题的定位分析方法。

## 前置知识

关于appfreezewarning的基本原理，请参考[应用冻屏告警事件介绍](../dfx/hiappevent-watcher-appfreezewarning-events.md)。

## 定位步骤

当发生JS代码阻塞渲染进程超过5秒时，系统会在以下路径生成日志文件：
```c
/data/log/faultlog/faultlogger/appfreezewarning-xxx.log
```

打开日志文件，查找 **Reason** 字段，日志示例如下：
```c
Device info:xxx
Build info:xxx
Fingerprint:xxx
Module name:com.xxx.demo
Foreground:No
Pid:xxx
Uid:xxx
Reason:RENDER_JS_FREEZE
appfreezewarning: com.xxx.demo RENDER_JS_FREEZE at xxx
DisplayPowerInfo:xxx
>>>>>>>>>>>>>>>>>>>>>>>>>>
DOMAIN:WEBVIEW
STRINGID:RENDER_JS_FREEZE
TIMESTAMP:xxx
PID:xxx
UID:xxx
PACKAGE_NAME:com.xxx.demo
PROCESS_NAME:com.xxx.demo:render
**************************
start time:xxx
DOMAIN = AAFWK
EVENTNAME = BUSINESS_THREAD_BLOCK_3S
TIMESTAMP = xxx
PID = xxx
UID = xxx
TID = xxx
...
```
如果 **Reason** 字段的值为 **RENDER_JS_FREEZE** ，则说明此次卡死是由前端JS代码阻塞渲染进程导致的。

然后在日志中全局搜索以下关键字：
```c
Collect Freezelog Callback
```
根据返回的JS堆栈信息，开发者可以进一步排查代码阻塞的具体原因。JS堆栈示例如下：
```c
Collect Freezelog Callback Start Time:2026/06/05-12:10:16:442
startInfiniteLoop (resource://rawfile/page.html:17:9)
jsTest (resource://rawfile/page.html:20:9)
HTMLButtonElement.onclick (resource://rawfile/page.html:14:73)
Collect Freezelog Callback End Time:2026/06/05-12:10:16:442
```