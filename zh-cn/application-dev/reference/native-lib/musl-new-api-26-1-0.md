# musl 26.1.0 新增接口

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @da_wei_li11-->
<!--Designer: @liyiming13-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

## 概述

OpenHarmony采用musl作为C标准库，musl库是一个轻量、快速、简单、免费的开源libc库，详细介绍参考[musl官方参考手册](https://musl.libc.org/manual.html)。

本文档描述musl在API version 26.1.0新增的接口。

**相关模块：** [libc标准库](musl.md)

## group_sem_open

`group_sem_open` 是OpenHarmony扩展接口，用于创建或打开指定`gid`下的命名信号量。详细介绍参考[group_ipc.h](capi-group-ipc-h.md)。

## group_sem_unlink

`group_sem_unlink` 是OpenHarmony扩展接口，用于删除指定`gid`下的命名信号量名称。详细介绍参考[group_ipc.h](capi-group-ipc-h.md)。

## group_shm_open

`group_shm_open` 是OpenHarmony扩展接口，用于创建或打开指定`gid`下的共享内存对象。详细介绍参考[group_ipc.h](capi-group-ipc-h.md)。

## group_shm_unlink

`group_shm_unlink` 是OpenHarmony扩展接口，用于删除指定`gid`下的共享内存对象名称。详细介绍参考[group_ipc.h](capi-group-ipc-h.md)。
