# CloudDisk
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->

## 概述

此模块提供云盘管理模块的接口和错误码。应用注册一个同步路径的作为根节点，以该路径为父目录的所有子目录都属于同步的范围，该目录简称为：同步根路径。<br> 注册成功后，可以监听该同步根路径下文件的变更，可以查询同步根路径下文件的历史操作记录，以及设置或查询同步根路径下文件的同步状态。

**起始版本：** 21
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [cloud_disk_error_code.h](capi-cloud-disk-error-code-h.md) | 提供云盘管理模块的错误码定义。 |
| [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md) | 云盘管理模块的接口定义。 |
