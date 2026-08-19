# @ohos.file.trash

该模块提供可以查询、还原或彻底删除最近删除（回收站）里的文件/文件夹的能力。当前仅支持本地文件目录。 应用可通过FileAccess的删除操作将文件/文件夹移动到回收站， 具体可参考[@ohos.file.fileAccess](arkts-file-fileaccess.md)。 > **说明：** > > - 当前只支持FilePicker、文件管理器调用。 > - 本模块为系统接口。 > - 当前只支持文件管理器调用。 > - 本模块接口从API version 23开始废弃。不建议使用以下接口。

**起始版本：** 10

**废弃版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace trash--><!--Device-unnamed-declare namespace trash-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { trash } from '@kit.CoreFileKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [completelyDelete](arkts-corefile-trash-completelydelete-f-sys.md) | 将uri对应文件/目录从最近删除（回收站）列表中彻底删除。 |
| [listFile](arkts-corefile-trash-listfile-f-sys.md) | 查询最近删除（回收站）列表中文件/目录信息。 |
| [recover](arkts-corefile-trash-recover-f-sys.md) | 将uri对应文件/目录恢复到原路径。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [FileInfo](arkts-corefile-trash-fileinfo-i-sys.md) | 最近删除（回收站）内文件的FileInfo对象。 |
<!--DelEnd-->

