# @ohos.file.cloudDiskManager(云盘管理)

本模块是为系统文件管理应用提供获取三方网盘注册的同步根信息的能力。

**起始版本：** 21

<!--Device-unnamed-declare namespace cloudDiskManager--><!--Device-unnamed-declare namespace cloudDiskManager-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudDiskManager } from '@kit.CoreFileKit';
```

## 汇总

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CloudDiskSystemAccessor](arkts-corefile-clouddiskmanager-clouddisksystemaccessor-c-sys.md) | 文件管理器访问云盘系统能力的类，如补水和脱水文件。 |
| [SyncFolderAccessor](arkts-corefile-clouddiskmanager-syncfolderaccessor-c-sys.md) | 同步根管理类，负责为系统文件管理应用提供获取三方网盘注册的同步根信息的能力。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [HydrateProgress](arkts-corefile-clouddiskmanager-hydrateprogress-i-sys.md) | 封装水合进度信息。 |
| [SyncFolder](arkts-corefile-clouddiskmanager-syncfolder-i-sys.md) | 表示同步根信息。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CallbackType](arkts-corefile-clouddiskmanager-callbacktype-e-sys.md) | 枚举云文件数据获取的回调类型。 |
| [HydratePriority](arkts-corefile-clouddiskmanager-hydratepriority-e-sys.md) | 枚举任务的优先级。 |
| [HydrateProgressState](arkts-corefile-clouddiskmanager-hydrateprogressstate-e-sys.md) | 枚举进度的状态。 |
| [SyncFolderState](arkts-corefile-clouddiskmanager-syncfolderstate-e-sys.md) | 枚举，云盘的同步根的状态。 |
<!--DelEnd-->
