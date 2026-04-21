# Print_PrintDocCallback
 <!--Kit: Basic Services Kit-->   
 <!--Subsystem: Print-->  
 <!--Owner: @guoshengbang-->  
 <!--Designer: @Q-haosu-->    
 <!--Tester: @Q-haosu-->  
 <!--Adviser: @fang-jinxu-->

```c
typedef struct {...} Print_PrintDocCallback
```

## 概述

表示打印文档状态回调结构体。

**起始版本：** 13

**相关模块：** [OH_Print](capi-oh-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称 | 描述 | 
| -------- | -------- |
| [Print_OnStartLayoutWrite](capi-ohprint-h.md#print_onstartlayoutwrite) [startLayoutWriteCb](#startlayoutwritecb) | 打印开始布局回调。 | 
| [Print_OnJobStateChanged](capi-ohprint-h.md#print_onjobstatechanged) [jobStateChangedCb](#jobstatechangedcb) | 打印任务状态回调。 | 


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