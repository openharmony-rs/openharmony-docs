# swapfs_errcode.h (系统接口)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->

## 概述

声明swapfs模块的错误码，包括文件系统操作过程中的各类错误状态定义。

**引用文件：** <filemanagement/swapfs/swapfs_errcode.h>

**库：** libohswapfs.so

**系统能力：** SystemCapability.FileManagement.File.Swapfs

**起始版本：** 26.0.0

**相关模块：** [Swapfs](capi-swapfs-sys.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_Swapfs_ErrCode](#oh_swapfs_errcode) | OH_Swapfs_ErrCode | swapfs模块的错误码。 |

## 枚举类型说明

### OH_Swapfs_ErrCode

```c
enum OH_Swapfs_ErrCode
```

**描述**

swapfs模块的错误码。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| SWAPFS_E_OK = 0 | 操作成功。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_INVAL = 36200001 | 无效参数。可能的原因包括空指针、零长度或无效的配置值。请检查传入参数是否合法。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_DIO_ALIGN = 36200002 | Direct I/O缓冲区地址或长度未对齐到SWAPFS_DIO_ALIGNMENT。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_BUFFER_TOO_SMALL = 36200003 | 换入缓冲区大小小于所需大小（Direct I/O模式下为occupiedSize，缓冲模式下为dataSize）。<br> dataSize为实际写入的数据字节数。<br> occupiedSize为磁盘上占用的物理空间字节数（Direct I/O模式下对齐到 4096，等于dataSize向上取整到SWAPFS_DIO_ALIGNMENT的倍数）。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_KEY_NOT_FOUND = 36200004 | 指定的keyId在当前管理器中不存在。请确认keyId是否正确或已创建。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_KEY_STATE_INVALID = 36200005 | key处于OH_SWAPFS_KEY_STATUS_REMOVING状态，无法进行操作。请等待key删除完成或使用其他可用的key。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_BUSY = 36200006 | 检测到并发冲突。<br> [OH_Swapfs_RemoveAllData](./capi-oh-swapfs-h-sys.md#oh_swapfs_removealldata)或[OH_Swapfs_DestroyManager](./capi-oh-swapfs-h-sys.md#oh_swapfs_destroymanager)检测到有活跃操作正在进行。请稍后重试或等待当前操作完成。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_NOSPC = 36200007 | 设备存储空间不足。请清理存储空间后重试。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_QUOTA_EXCEEDED = 36200008 | 换出空间配额超限。总占用空间已达到配置的上限。请清理已换出的数据或调整配额上限。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_IO_ERROR = 36200009 | IO读取或写入失败。原因可能包括：实际读取/写入字节数少于请求字节数（短读/短写）、数据持久化失败（fsync失败）或文件重命名失败。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_FEATURE_DISABLED = 36200010 | 换出功能因设备存储空间不足或控制策略被禁用。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_ACCES = 36200011 | 权限被拒绝。请检查应用权限或文件访问权限。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_PATH_UNAVAILABLE = 36200012 | 换出根路径无法创建或不可用。请检查路径配置或存储设备状态。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_SHUTTING_DOWN = 36200013 | 管理器正在关闭。<br> 新的[OH_Swapfs_SwapOut](./capi-oh-swapfs-h-sys.md#oh_swapfs_swapout)、[OH_Swapfs_SwapIn](./capi-oh-swapfs-h-sys.md#oh_swapfs_swapin)、[OH_Swapfs_RemoveData](./capi-oh-swapfs-h-sys.md#oh_swapfs_removedata)或[OH_Swapfs_RemoveAllData](./capi-oh-swapfs-h-sys.md#oh_swapfs_removealldata)操作将被拒绝。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_NOMEM = 36200014 | 内存分配失败。<br>**起始版本：** 26.0.0 |
