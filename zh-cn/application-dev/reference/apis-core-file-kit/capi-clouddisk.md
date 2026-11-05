# CloudDisk
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->

## 概述

本模块提供云盘管理的接口和错误码，用于实现应用与云盘的文件同步管理能力。应用注册一个同步路径作为根节点，以该路径为父目录的所有子目录都属于同步范围，该目录简称为同步根路径。<br>注册成功后，应用可以监听同步根路径下文件的变更，查询文件的历史操作记录，以及设置或查询文件的同步状态。适用于需要在应用内集成云盘同步功能、追踪文件同步状态或管理云端文件变更的场景。

**起始版本：** 21
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [cloud_disk_error_code.h](capi-cloud-disk-error-code-h.md) | 提供云盘管理模块的错误码定义，用于标识云盘管理接口调用过程中的异常情况，帮助开发者定位和处理权限校验失败、参数无效、路径冲突、IPC连接失败等问题。 |
| [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md) | 云盘管理模块的接口定义，提供云盘同步根路径的注册、激活、监听和查询能力，支持监听文件变更、设置和查询文件同步状态，并提供占位符文件的创建、水合、脱水及回调注册能力，适用于需要在应用内实现云盘文件同步、变更监听和按需下载的场景。 |
