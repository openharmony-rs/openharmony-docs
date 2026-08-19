# @ohos.file.statvfs

该模块向应用程序提供获取文件系统总字节数、空闲字节数的ArkTS接口。通过该模块，开发者可以实时掌握文件系统存储状况，避免因存储空间不足导致的应用崩溃，提升用户体验和系统稳定性。 使用场景包括：文件下载前检查存储空间、应用安装前进行磁盘空间预估、缓存管理中的空间监控等。

**起始版本：** 23

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
| [getFreeSize](arkts-corefile-statfs-getfreesize-f.md) | 获取指定文件或目录所在文件系统的空闲字节数。使用Promise异步回调。 |
| [getFreeSize](arkts-corefile-statfs-getfreesize-f.md) | 获取指定文件或目录所在文件系统的空闲字节数。使用callback异步回调。 |
| [getFreeSizeSync](arkts-corefile-statfs-getfreesizesync-f.md) | 以同步方法获取指定文件或目录所在文件系统的空闲字节数。 |
| [getTotalSize](arkts-corefile-statfs-gettotalsize-f.md) | 获取指定文件或目录所在文件系统的总字节数。使用Promise异步回调。 |
| [getTotalSize](arkts-corefile-statfs-gettotalsize-f.md) | 获取指定文件或目录所在文件系统的总字节数。使用callback异步回调。 |
| [getTotalSizeSync](arkts-corefile-statfs-gettotalsizesync-f.md) | 以同步方法获取指定文件或目录所在文件系统的总字节数。 |

