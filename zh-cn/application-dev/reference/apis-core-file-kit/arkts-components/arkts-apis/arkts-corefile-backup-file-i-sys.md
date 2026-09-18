# File（系统接口）

文件对象，包含文件元数据、文件数据和清单文件信息。用于客户端与备份服务进行IPC。

@extends FileMeta, FileData, FileManifestData @interface File

**继承/实现关系：** File extends [FileMeta](arkts-corefile-backup-filemeta-i-sys.md)<!--Del-->, [FileData](arkts-corefile-backup-filedata-i-sys.md)<!--DelEnd--><!--Del-->, [FileManifestData](arkts-corefile-backup-filemanifestdata-i-sys.md)<!--DelEnd-->

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { backup } from '@kit.CoreFileKit';
```
