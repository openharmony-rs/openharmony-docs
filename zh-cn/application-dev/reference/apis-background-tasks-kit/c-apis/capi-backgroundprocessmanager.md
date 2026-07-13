# BackgroundProcessManager

## 概述

BackgroundProcessManager provides APIs.

**起始版本：** 17
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [background_process_manager.h](capi-background-process-manager-h.md) | 本模块提供了后台子进程管控接口。开发者可以通过本模块接口对子进程进行压制、解压制，避免子进程过多占用系统资源，导致系统使用卡顿。本模块接口仅对通过{@link OH_Ability_StartNativeChildProcess}接口创建的子进程生效。 |
