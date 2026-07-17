# swapfs_errcode.h

## 概述

Declare the error codes of swapfs module.

**库：** libohswapfs.so

**系统能力：** SystemCapability.FileManagement.File.Swapfs

**起始版本：** 26.0.0

**相关模块：** [Swapfs](capi-swapfs.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_Swapfs_ErrCode](#oh_swapfs_errcode) | OH_Swapfs_ErrCode | swapfs模块错误码 |

## 枚举类型说明

### OH_Swapfs_ErrCode

```c
enum OH_Swapfs_ErrCode
```

**描述**

swapfs模块错误码

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| SWAPFS_E_OK = 0 | 操作成功。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_INVAL = 36200001 | 无效参数，包括空指针、零长度或非法配置值。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_DIO_ALIGN = 36200002 | DIO缓冲区地址或长度未按SWAPFS_DIO_ALIGNMENT对齐。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_BUFFER_TOO_SMALL = 36200003 | SwapIn缓冲区大小小于所需大小（DIO模式为occupiedSize，缓冲模式为dataSize）。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_KEY_NOT_FOUND = 36200004 | 指定的keyId在当前管理器中不存在。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_KEY_STATE_INVALID = 36200005 | key处于REMOVING状态，无法对其进行操作。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_BUSY = 36200006 | 检测到并发冲突。RemoveAllData或DestroyManager检测到有活动操作正在进行。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_NOSPC = 36200007 | 设备存储空间不足。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_QUOTA_EXCEEDED = 36200008 | 交换空间配额超出。总占用空间已达到配置的限制。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_IO_ERROR = 36200009 | IO读写失败，包括读取不完整、写入不完整、fsync失败或rename失败。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_FEATURE_DISABLED = 36200010 | 由于设备空间不足或控制策略，SwapOut功能已被禁用。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_ACCES = 36200011 | 权限被拒绝。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_PATH_UNAVAILABLE = 36200012 | 无法创建交换根路径或该路径不可用。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_SHUTTING_DOWN = 36200013 | 管理器正在关闭。新的swap-out、swap-in、remove或remove-all操作将被拒绝。<br>**起始版本：** 26.0.0 |
| SWAPFS_E_NOMEM = 36200014 | 内存分配失败。<br>**起始版本：** 26.0.0 |


