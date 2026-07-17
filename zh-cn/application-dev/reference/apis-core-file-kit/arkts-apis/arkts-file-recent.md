# @ohos.file.recent

该模块提供最近访问列表插入、移除、查询等常用能力。

> **说明：**  
>  
> - 当前只支持文件管理器调用。

**起始版本：** 10

**废弃版本：** 23

<!--Device-unnamed-declare namespace recent--><!--Device-unnamed-declare namespace recent-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { recent } from '@kit.CoreFileKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [add](arkts-corefile-recent-add-f-sys.md#add-1) | 将uri对应的文件加入最近访问列表。 |
| [listFile](arkts-corefile-recent-listfile-f-sys.md#listfile-1) | 查询最近访问列表中文件信息。 |
| [remove](arkts-corefile-recent-remove-f-sys.md#remove-1) | 将uri对应的文件从最近访问列表中移除。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [FileInfo](arkts-corefile-recent-fileinfo-i-sys.md) | 最近访问列表文件信息。 |
<!--DelEnd-->

