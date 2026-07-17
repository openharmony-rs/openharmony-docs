# @ohos.file.statvfs

该模块提供文件系统相关存储信息的功能：向应用程序提供获取文件系统总字节数、空闲字节数的JS接口。

**起始版本：** 9

<!--Device-unnamed-declare namespace statfs--><!--Device-unnamed-declare namespace statfs-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { statfs } from '@kit.CoreFileKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getFreeSize](arkts-corefile-statfs-getfreesize-f.md#getfreesize-1) | 异步方法获取指定文件系统空闲字节数，以Promise形式返回结果。 |
| [getFreeSize](arkts-corefile-statfs-getfreesize-f.md#getfreesize-2) | 异步方法获取指定文件系统空闲字节数，使用callback形式返回结果。 |
| [getFreeSizeSync](arkts-corefile-statfs-getfreesizesync-f.md#getfreesizesync-1) | 以同步方法获取指定文件系统空闲字节数。 |
| [getTotalSize](arkts-corefile-statfs-gettotalsize-f.md#gettotalsize-1) | 异步方法获取指定文件系统总字节数，以Promise形式返回结果。 |
| [getTotalSize](arkts-corefile-statfs-gettotalsize-f.md#gettotalsize-2) | 异步方法获取指定文件系统总字节数，使用callback形式返回结果。 |
| [getTotalSizeSync](arkts-corefile-statfs-gettotalsizesync-f.md#gettotalsizesync-1) | 以同步方法获取指定文件系统总字节数。 |

