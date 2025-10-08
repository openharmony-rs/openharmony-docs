# NativeChildProcess_Args

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

## 概述

传递给子进程的参数。

**起始版本：** 13

**相关模块：** [ChildProcess](capi-childprocess.md)

**所在头文件：** [native_child_process.h](capi-native-child-process-h.md)

## 汇总

### 成员变量

| 名称                                          | 描述 |
|---------------------------------------------| -- |
| char* entryParams                           | 入口参数，大小不能超过150KB。 |
| struct [NativeChildProcess_FdList](capi-nativechildprocess-fdlist.md) fdList | 传递给子进程的文件描述符信息列表。 |
