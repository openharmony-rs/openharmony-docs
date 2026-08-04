# Print_PrintDocCallback
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->

```cpp
typedef struct {...} Print_PrintDocCallback
```

## 概述

表示打印文档回调结构体。用于 C/C++ 原生应用向打印框架提供文件生成和任务状态接收能力。

**起始版本：** 13

**相关模块：** [OH_Print](capi-oh-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称 | 描述 | 
| -------- | -------- |
| [Print_OnStartLayoutWrite](capi-ohprint-h.md#print_onstartlayoutwrite) [startLayoutWriteCb](#startlayoutwritecb) | 打印开始布局写回调。打印任务开始布局时，系统将调用此回调，应用需要在此回调中写入打印文件内容。 | 
| [Print_OnJobStateChanged](capi-ohprint-h.md#print_onjobstatechanged) [jobStateChangedCb](#jobstatechangedcb) | 打印任务状态变化回调。打印任务状态发生变化时，系统将调用此回调，以知通应用打印任务状态更新。 | 


## 结构体成员变量说明


### jobStateChangedCb

```c
Print_OnJobStateChanged Print_PrintDocCallback::jobStateChangedCb
```
**描述**

打印任务状态回调。


### startLayoutWriteCb

```c
Print_OnStartLayoutWrite Print_PrintDocCallback::startLayoutWriteCb
```
**描述**

文件开始回写回调函数。